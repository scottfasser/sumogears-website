# Sumo Gears — Website Design Concepts

Design prototypes for the new Sumo Gears site (All Automotive Import Export). Static HTML — no build step.

## Run locally
Pages load data files, so serve the folder rather than double-clicking:

```
npx serve .
# or
python3 -m http.server 8000
```

Open `http://localhost:8000` (redirects to the homepage).

Deploys as-is to GitHub Pages, Netlify or Vercel (static site, root = this folder).

## Pages
| File | Page |
|---|---|
| `SumoGears Homepage.dc.html` | Homepage |
| `SumoGears Product Page v2 - LC 60-70.dc.html` | Low range gear sets (Toyota / Suzuki toggle, platform tabs via URL hash) |
| `SumoGears Rebuild Kits.dc.html` | Rebuild kits (`#toyota`, `#suzuki`, `#lc80`, `#samurai`…) |
| `SumoGears FAQ.dc.html` | FAQ (`#<anchor>` opens a group or answer) |
| `SumoGears Dealer-Event Map v2.html` | Dealer & event map |
| `SumoGears Contact.dc.html` | Contact form (`?topic=dealer\|event\|product\|other`) |
| `SumoGears Review Hub.dc.html` | Internal team review hub |

## Structure
- `*.dc.html` — page markup with inline styles; logic in the `<script data-dc-script>` block of each file.
- `support.js` — small runtime that renders the `.dc.html` pages (uses React from a CDN). Required.
- `faq-data.js` — shared FAQ content (`window.SUMO_FAQ`), used by every page.
- `image-slot.js` — image placeholder component.
- `assets/` — logos, hero and community photos.
- `data/` — map geometry (world countries, US/CA/AU states).
- `logos-clean/` — source logo files.

## Notes
- Some product photos load from sumogearco.com and need an internet connection.
- External libraries (React, D3, TopoJSON, Google Fonts) load from CDNs.
- Contact form is front-end only — wire the submit to your backend or form service.
- Dealer/event data is sample data inside the map file (`const P = [...]`), except Cruiser Teq (real).
- Brand: navy `#0f2f57`, blue `#0686db` / `#0a63a8`, red `#eb0028`. Fonts: Zen Kaku Gothic New, Shippori Mincho, IBM Plex Mono.
- Client rules: FAQ stays general (no install instructions), no "in stock / ships same day" claims, no supplier locations in Japan, builder videos embedded from YouTube.
