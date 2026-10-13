# Copilot instructions

Single-file, dependency-free space exploration quiz: `index.html` (inline CSS and JS). No build, lint, or test tooling. Open the file in a browser (`file://`, no server needed).

## Rules

- Keep everything in one `index.html`: no external libraries, fonts, or network requests.
- Stay accessible: native `<button>`s, visible `:focus-visible` outlines, `role="progressbar"` on `.bar`, and the `prefers-reduced-motion` rule.
- Preserve both themes. Colors come from CSS variables in `:root` and the `prefers-color-scheme: dark` block; add new colors to both.
- Keep body text sans-serif at 14–16px in a centered column (max 480px). Monospace is only for the mission-control HUD elements.
- Set question text with `textContent`, never by interpolating it into `innerHTML`.
- Comment only code that needs clarification.

## Structure

- `Q` holds `[question, [4 options], correctIndex]` tuples; progress, ticks, and results all derive from `Q.length`.
- State is `i`, `score`, `answered`, `locked`. "Play again" must reset all of them, so reset any new state there too.
- `show()` renders a question, `pick(k)` handles an answer, `telemetry()` updates score/accuracy, `end()` renders the results.

## Testing

After any change, smoke-test in the integrated browser: keyboard focus, score and accuracy updates, correct/wrong feedback, results screen, and Play again. In dark mode, check contrast too.
