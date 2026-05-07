# IWI Workforce Resilience — Landing Page

A B2B landing page for the **Integrated Wellness Institute** selling two flagship training program pairings to organizational decision-makers (HR Directors, Chief Wellness Officers, Training Division Commanders, Academy Directors, Risk Management, EAP/Behavioral Health Leads).

**Programs presented:**

1. **Mastering Resilience: First Responder Edition** — paired with the companion book *Mastering Resilience: Strategies for High-Demand Professionals*
2. **Peer Support in Action** — paired with the companion book *Peer Support Blueprint* (forthcoming)

Both built around IWI's PEACE Resilience Model.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | The landing page. Single self-contained HTML file with embedded CSS and JS. Loads fonts from Google Fonts CDN. |
| `mastering_resilience_cover.jpg` | The book cover image referenced from the hero. |
| `README.md` | This file. |

There are no build steps. No dependencies to install. Open `index.html` in a browser and it works.

---

## Deploy on GitHub Pages

1. Push these files to a GitHub repo (root of the repo, or a `/docs` folder — both work).
2. Repo → **Settings** → **Pages**.
3. Under **Source**, select the branch you pushed to (typically `main`) and either `/ (root)` or `/docs` depending on where the files live.
4. Save. GitHub gives you a URL like `https://<username>.github.io/<repo-name>/` within a minute or two.

That's the whole deploy. No build pipeline, no framework setup.

### Custom domain (optional)

If you want to serve this at a real domain like `programs.theiwinstitute.com`:

1. Add a `CNAME` file to the repo containing just your domain (e.g., `programs.theiwinstitute.com`).
2. In your DNS, add a `CNAME` record pointing the subdomain to `<username>.github.io`.
3. In **Settings** → **Pages**, enter the custom domain and tick "Enforce HTTPS" once the cert provisions.

---

## What to swap before going live

A few placeholders to update:

### 1. Lead capture form
The contact form in the **Schedule a Consultation** section currently uses `mailto:` as a fallback — when someone clicks Submit, it opens their email client with the form fields pre-filled, addressed to `contact@theiwinstitute.com`.

This works but is fragile (depends on the visitor having a configured email client). For production, wire the form up to a proper handler. Easy options:

- **Formspree** — paste your endpoint URL into the form's `action` attribute
- **Basin**, **Getform**, **Tally**, **Netlify Forms** if you migrate to Netlify
- A serverless function (Cloudflare Workers, Vercel, AWS Lambda) that posts to your CRM

The relevant code is at the bottom of `index.html` — search for `leadForm` in the `<script>` block.

### 2. Peer Support Blueprint cover
The Peer Support Blueprint book is referenced in the **Programs** section but is marked "Forthcoming." When the real cover is ready, you can add a similar hero treatment.

### 3. Reviews / testimonials
Three reviews from "Cmdr. M. R.", "Chief D. H.", and "Director K. T." in the **From Organizational Leadership** section are illustrative placeholders. Replace with real testimonials when you have them. Search for `class="review"` in `index.html` to find them.

### 4. Author bios
Brief bios for Drs. Kanter-Agliata and Stewart-Spencer are written from the materials in the project files. Refine the wording if needed. Search for `class="author"` in `index.html`.

### 5. Phone & email
Currently set to `contact@theiwinstitute.com` and `904.669.3345`. Search and replace if these need to change.

---

## Brand & design

The page is built on the IWI brand system:

- **Primary** `#4c6c94` (deep blue), **Sage** `#7da2a2`, **Gold** `#f1d025` (CTAs only)
- **Display type:** Cormorant Garamond (Google Fonts)
- **Body type:** Inter (Google Fonts)
- **Page background:** `#FAF8F4` (warm off-white) with subtle paper grain texture

All design tokens are CSS variables at the top of `<style>` in `index.html` — easy to adjust without hunting through the file.

---

## Browser support

Tested on current Chromium-based browsers. Uses modern CSS (`clamp()`, `aspect-ratio`, CSS variables, flexbox/grid) and IntersectionObserver for scroll animations — fully supported in any browser from the last few years. Falls back gracefully on older browsers (animations skip, layout still works).

---

## License

Add a `LICENSE` file with whatever terms you prefer (MIT, proprietary, etc.). This README does not specify one.
