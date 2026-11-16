# Güneş Yıldız Akgüneş Law & Consultancy Office – Website

The corporate website I built for Güneş Yıldız Akgüneş Law & Consultancy Office, a law firm based in İskenderun, Hatay, Türkiye. The site content is in Turkish.

I wrote the site in plain **HTML5, CSS3 and vanilla JavaScript**, without frameworks or a build step. It runs on any static host (GitHub Pages, Netlify, etc.) without extra setup.

## Pages

| File | Content |
|---|---|
| `index.html` | Hero, About Us, services overview, call-to-action |
| `kurucumuz.html` | Founder biography, education and experience |
| `hizmetler.html` | Detailed cards for 7 practice areas |
| `sss.html` | Frequently asked questions (accordion) |
| `iletisim.html` | Contact cards, contact form, Google Map |
| `gizlilik.html` | Privacy policy and KVKK (Turkish data protection law) notice |

## Technical Highlights

### Design & CSS
- All pages share a single stylesheet (`style.css`). Colors, fonts, radii and shadows are defined as **CSS custom properties** on `:root`, so the theme can be changed in one place.
- Layout is built with **CSS Grid** and **Flexbox**. Service and contact cards use `repeat(auto-fit, minmax(...))` to reflow automatically for any screen width.
- Headings scale fluidly with `clamp()`.
- The navbar uses `position: sticky` with a `backdrop-filter: blur()` frosted-glass effect.
- **Responsive:** below 860px the navbar collapses into a hamburger menu, with further adjustments at 520px and 420px. No horizontal scrolling at any width.
- **Accessibility:** animations are disabled for users with `prefers-reduced-motion`. Icon-only links have `aria-label`s, and the menu button exposes its state through `aria-expanded`.

### JavaScript (`script.js`)
- **Mobile menu:** toggles the menu and keeps `aria-expanded` in sync.
- **Scroll reveal:** sections with the `.reveal` class fade in as they enter the viewport, using `IntersectionObserver`. Browsers without the API show them immediately.
- **Footer year:** the copyright year updates automatically via `new Date().getFullYear()`.
- **Contact form:**
  - If a Formspree endpoint is configured, the form is submitted with `fetch` and success/error states are shown inline.
  - If not, it falls back to a `mailto:` link that pre-fills the message in the visitor's email client.

### Zero-JS Components
- **FAQ:** built with native `<details>` / `<summary>` elements, so it is keyboard accessible and needs no JavaScript.
- **Map:** a Google Maps `output=embed` iframe, which needs no API key. `loading="lazy"` keeps it from slowing down the initial page load.
- **WhatsApp button:** a fixed `wa.me` link on every page; the pulse ring is pure CSS.
- **Founder photo fallback:** if the image is missing, an `onerror` handler removes it and a monogram with the founder's initials is shown instead.

### SEO
- Each page has its own `<title>` and `<meta name="description">`.
- Correct language attribute (`lang="tr"`), semantic elements (`header`, `section`, `article`, `footer`) and a consistent heading hierarchy.

## External Dependencies

Nothing to install. The following are loaded from CDNs:

| Resource | Used for |
|---|---|
| [Google Fonts](https://fonts.google.com) | *Playfair Display* (headings), *Inter* (body text) |
| [Font Awesome 6.5.0](https://fontawesome.com) via cdnjs | Icons |
| Google Maps Embed | Map on the contact page |
| [Formspree](https://formspree.io) *(optional)* | Delivering contact form submissions by email |

## Project Structure

```
.
├── index.html
├── kurucumuz.html
├── hizmetler.html
├── sss.html
├── iletisim.html
├── gizlilik.html
├── style.css        # Shared stylesheet
├── script.js        # Menu, animations and form handling
├── justiceimg.jpg   # Hero and page header background
├── favicon.svg      # Browser tab icon
└── img/
    └── gunesyildiz.jpg   # Founder photo (to be added)
```

## Running Locally

There is no build step: opening `index.html` in a browser is enough. To test the form and map in a setup closer to production, serve the folder with a simple local server:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deployment (GitHub Pages)

1. Go to **Settings → Pages** in the repository.
2. Set **Source** to *Deploy from a branch*, choose the `main` branch and the `/ (root)` folder.
3. After a few minutes the site is live at `https://<username>.github.io/<repository>/`.

All asset paths are relative, so the site also works when served from a subdirectory.

## Configuration

| What | Where | How |
|---|---|---|
| Contact form | `iletisim.html` → `<form action="...">` | Create a form on Formspree and replace `FORM_KODU` with your form ID. |
| Social media links | `iletisim.html` → `.social` | Replace `href="#"` with the account URLs. |
| Founder photo | `img/gunesyildiz.jpg` | Add a portrait photo (4:5 ratio) with this name in `img/`. |
| Theme colors | `style.css` → `:root` | Change variables such as `--gold`, `--bg` and `--surface`. |
| Phone / WhatsApp | All pages | Update the `tel:+905326954012` and `wa.me/905326954012` links. |

## Browser Support

Targets current versions of Chrome, Edge, Firefox and Safari, on desktop and mobile.

## Contact

**Güneş Yıldız Akgüneş Hukuk ve Danışmanlık Bürosu**
Savaş Mah. M. Çakmak Cad. No:11, Kat:1, Daire:5, Dağlı İş Merkezi – İskenderun/Hatay, Türkiye
+90 532 695 40 12 · av.gunesyildiz@gmail.com

---

© Güneş Yıldız Akgüneş Hukuk ve Danışmanlık Bürosu. All rights reserved.
