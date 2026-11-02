# Invasion

A single-page, dependency-free arcade shooter in the spirit of classic 1978
fixed-shooters — original sprites, an 11×5 alien formation that marches and
speeds up as it thins out, eroding bunkers, a mystery UFO, and synthesized
sound — all built from one `index.html` with no build step, no libraries,
and no network calls.

## Play it

**Locally:** double-click `index.html`, or serve the folder with any static
server (`python3 -m http.server`) and open it in a browser.

**On GitHub Pages:** if Pages is enabled for this repository (see below), it is served at
`https://qualitycoding.github.io/invasion/`.

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Move | `←` `→` or `A` `D` | on-screen ◀ ▶ buttons |
| Fire | `Space` | on-screen FIRE button |
| Pause | `P` | — |
| Mute | `M` | speaker icon, top-right |
| Start / Restart | `Space` or `Enter` | tap FIRE or the screen |

Your high score and your mute setting are saved in the browser's `localStorage`,
so they persist between visits on the same device.

## Deploying to GitHub Pages

1. Create a new repository on GitHub (or use one you already have).
2. Push this folder's contents to the repo's default branch:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Invasion"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. On GitHub, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`,
   then pick branch `main` and folder `/ (root)`. Save.
5. GitHub will publish the site in about a minute at
   `https://<your-username>.github.io/<repo-name>/`.

The `.nojekyll` file in this repo tells GitHub Pages to serve the files
as-is, skipping Jekyll processing (not needed here, but it avoids Pages
ignoring any future files that start with an underscore).

## Notes on the code

Everything lives in `index.html`:
- Canvas-based rendering at a fixed 224×256 logical resolution, scaled up
  crisply to fit any screen (integer scaling, `image-rendering: pixelated`).
- All sprites are small pixel-art bitmaps defined directly in JavaScript
  (mirrored from half-patterns) — no image files.
- All sound is synthesized at runtime with the Web Audio API — no audio
  files. Sound starts on the first key press or tap, per browser autoplay
  rules.
- A fixed 60 Hz timestep keeps gameplay speed consistent across devices
  and frame rates.

Feel free to open it up and tune constants near the top of the `<script>`
block — alien speed, bullet limits, wave scaling, colors, and sprite
patterns are all grouped together and commented.

## License

Apache License 2.0 — see `LICENSE`. This is an original, independently authored game
inspired by the fixed-shooter genre; it is not affiliated with or
endorsed by any trademark holder in that genre, and uses no copyrighted
artwork, sprites, or audio from any prior game.
