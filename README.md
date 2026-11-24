# VOSSBERG: native HTML

![VOSSBERG homepage preview](docs/preview/homepage.gif)

A static site in plain HTML, CSS and JavaScript, with no framework and no build step needed to view it.
Open `index.html` directly in Chrome, Edge or Firefox, or serve this folder with any static server.

## Structure

```
index.html               home
aquila.html              model page (scroll film, 3 chapters, ambient sound)
heritage.html            horizontal timeline (+ ?timeline=racing-history)
boutique.html            shop listing
product-*.html           11 product pages
news.html                news listing (+ ?category=Events …)
news-*.html              12 articles
contact.html             contact form (+ ?subject=sales …)
privacy.html terms.html cookies.html 404.html
assets/css/              fonts.css, main.css
assets/js/               main.js (shared) + one file per page type (home, model, heritage,
                         boutique, product, news, article, contact), data.js
assets/img|video|audio|fonts
```

33 HTML pages in total, all in the project root.

> The `build/` generator and `docs/` folders from earlier versions are no longer in this folder. The pages are now edited directly.

## Editing

Edit the HTML files directly. Header, menu, footer and cart markup is repeated in every page, so a change to one of them has to be made in all 33 files (a find-and-replace across the folder works well).
Styles and behaviour live in `assets/css/main.css` and `assets/js/`. `assets/js/data.js` holds the shared data (products, prices, timeline) used by the scripts.

## Interactive states included

- **Every page:** intro loader (first visit per session), page-transition curtain, smooth wheel scrolling, header that hides on scroll with two-tone clipping over dark sections, full-screen menu, bag drawer (empty and filled, quantities, remove, demo checkout message), newsletter drawer with validation, and cookie banner with Customize / Save preferences / Decline / Accept (reopen it from the footer "Cookie policy" link).
- **Home:** hero parallax, letter-by-letter reveals, button character roll, underline links, editorial parallax, the motto frame opening, the film player with sound (play/pause, seek, mute, fullscreen), heritage collage (reveals and mouse parallax), boutique autoplay slider, news hover zoom, inline newsletter.
- **Model page:**
  - three scroll-scrubbed films drawn on canvas, letterbox title cards and side panels;
  - ambient audio per chapter with crossfades, "Best experienced with sound Off/On" and the wave toggle;
  - clock dial that opens the chapter overview, Skip button, gallery lightbox (keyboard arrows), odometer-style stat counters.
- **Heritage, boutique, product, news, article and contact:**
  - Heritage: horizontal timeline, Heritage/Racing switch with URL, wheel/trackpad/arrow-key navigation.
  - Boutique: collection tabs, EUR/USD (saved), III/VI grid (saved), card image sliders.
  - Product: size select (keyboard accessible), add to cart → opens the bag, colour swatches, accordions.
  - News: category filter with sliding indicator.
  - Article: related slider (buttons and mouse drag).
  - Contact: custom select and inline validation.

Forms never send data anywhere. They validate and then show a thank-you message.

## Placeholders to replace

- **Brand:** VOSSBERG, the "V9 Aquila XXI Coupé", the motto "Fortes Fortuna Adiuvat" and all copy are invented.
- **Contact details:** `hello@` and `press@vossberg-coachworks.com`, the Haarlem address, the phone number and the "By Atelier Noord" credit are fictional (search the HTML files and `assets/js/data.js`).
- **Social links:** they point to `#`.
- **Photos:** from Unsplash (source list in `assets/img/CREDITS.json`). Some stock car photos may show the badges of real makes.
- **Videos:** from Mixkit (#35577 hero, #63 grill, #52427/#63/#20039 film, #66 morning, #20039 afternoon, #47615 evening). The scroll films were re-encoded with a short keyframe interval so they scrub smoothly.
- **Audio:** from Mixkit. Sound effects #2472 (morning birds), #1538 (car drive-by), #2678 (city at night); music #184 "Vastness" (film soundtrack).
- **Logo:** set in Mr Dafoe (free Google Font) as text, not a drawn mark.

## Checks

The audit and interaction-test scripts (`laudit.mjs`, `itest.mjs`) were removed from this folder. Before release, check manually at 1440 and 390 px width for console errors, failed requests, broken images and links, and horizontal overflow.
