# Chrome Extension Icon Generator

Design a complete **16 / 32 / 48 / 128 px** Chrome extension icon set directly in your browser — then download a ready-to-install `icons/` folder.

Built as a single, dependency-free HTML file. Everything runs locally: **nothing is uploaded, no account, no analytics**.

## Features

- **Live preview** of all four Chrome icon sizes plus a large 512 px view.
- **16 built-in symbols** (external link, JSON braces, letters, shield, gear, AI chip…) drawn stroke-based so they stay crisp at 16 px.
- **Custom symbol** — paste any SVG `path` (e.g. from [Lucide](https://lucide.dev)); it is auto-centered and auto-fit to any coordinate system.
- **Solid or soft gradient** tiles, 12 color presets or fully custom background / foreground colors.
- **One-click export**:
  - `icons.zip` → `icons/icon16.png … icon128.png` + `manifest-icons.json`
  - `icon.svg` for vector use
  - `manifest.json` icons block to copy/paste
- **State memory** — your design is kept in `localStorage`.
- **Shareable URL** — the whole design is encoded in the hash; anyone opening the link sees the same icon.

## Usage

Open `index.html` in any modern browser, or use the hosted version:

<https://xiaowulang-turbo.github.io/chrome-icon-generator/>

1. Pick an extension name, a symbol, colors and corner radius.
2. Adjust symbol scale until it reads well at 16 px.
3. **Download icons.zip** → unzip → drop the `icons/` folder into your extension root.
4. Reference the icons in `manifest.json`:

```json
{
  "icons": {
    "16": "icons/icon16.png",
    "32": "icons/icon32.png",
    "48": "icons/icon48.png",
    "128": "icons/icon128.png"
  }
}
```

## Why stroke-based symbols?

Chrome only ships 4 sizes — 16 px is tiny. Outlined icons with a consistent stroke weight survive downscaling far better than thin detail or text, which is why this generator keeps symbols flat and thick by default.

## Design notes

- Icons are authored on a 24 px mindset grid but rendered on a 40-unit canvas with auto-fit, so pasted paths from any icon set center correctly.
- Background tiles use a 22.5% corner radius by default (adjustable 0–50%).
- PNG export rasterizes the SVG at each exact pixel size in-browser (canvas API) — no server round-trip.

## Development

The whole tool is one file — edit `index.html` and refresh. No build step.

```bash
# local preview
python3 -m http.server 8080
# open http://localhost:8080
```

## License

MIT
