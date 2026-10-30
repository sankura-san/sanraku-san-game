# The Mountain That Moves

A dark-fantasy interactive story: climb a mountain that recedes with every step, and decide at each checkpoint what you will sacrifice, bargain, or leave behind for a single wish. Nine endings, auto-saving, fully static — runs on GitHub Pages with no server, build step, or API keys.

## Project structure

```
index.html            page markup + the layered SVG mountain scene
css/
  utilities.css       small pre-generated utility classes (replaces the Tailwind CDN)
  style.css           theme, layout, buttons, choice cards, scene layers
  animations.css      all motion (fog, clouds, lantern, traveler, transitions) + reduced-motion rules
js/
  game.js             story text, choices, state, save/load, screens, modals
  animations.js       particle engine (one requestAnimationFrame loop), parallax, choice effects
assets/
  backgrounds/        sky.svg, far-ridges.svg, foreground-pines.svg
  sprites/            traveler.svg
  icons/              lantern, memories, name, shadow
  ui/                 favicon.svg, logo.svg
tools/make_utilities.py   optional: regenerates css/utilities.css if you add new utility classes
```

## Publish on GitHub Pages
1. Create a public repository (e.g. `the-mountain-that-moves`) and upload **everything in this folder** (keep the folder structure; `index.html` must be at the top level).
2. Repository **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save**.
3. After a minute your game is live at `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`.

All asset paths are relative, so it works under that sub-path.

## Test locally
Opening `index.html` directly mostly works, but a tiny local server matches GitHub Pages best:
`python3 -m http.server 8000` then visit http://localhost:8000

## Test checklist
- Title → "Begin the Ascent" → setup (try a custom wish) → "Step onto the Trail".
- Each checkpoint (I–IV): all three choices; the consequence slide; "Advance".
- "Look Back Down" (header) at each checkpoint, both "Keep Climbing" and "Turn Back & Descend".
- Summit: every ending — `memories`, `humanity`, `guardian`, `refuse`, and (only if you pinned your shadow with iron) the True Descent. Turn-back endings I–IV.
- Reload mid-run: you resume where you left off. ↻ resets. "Begin Another Climb" replays.
- Sound toggle, What Remains journal, Inspect Slide State, About, Esc closes dialogs.
- Phone-width layout; OS "reduce motion" setting (animations stop, game stays fully playable).

## Notes
- Fonts (Cormorant Garamond, Inter, JetBrains Mono) load from Google Fonts; if blocked, the game falls back to Georgia / system fonts.
- Art is original vector SVG (the reference sheets were concept boards, not cut-out sprites).
- Progress is stored in your browser's localStorage under `mountain_that_moves_save_v3`.
