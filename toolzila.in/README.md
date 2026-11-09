# Toolzila (HTML, CSS, JavaScript) - 34 tools, no API key needed

Every tool runs in the visitor's browser. No server, database or API key is required.

## Shared header and footer (edit once, changes everywhere)
- `components/header.html`  the navigation bar, search and menu
- `components/footer.html`  the footer (logo, email, Popular Tools, Categories, Company) and the phone tab bar
- `components/components.js`  loads both files with the Fetch API and puts them into every page

Every page only contains two empty placeholders, `<div id="site-header">` and `<div id="site-footer">`.
To change a menu link, the footer email or the Popular Tools list, edit header.html or footer.html only.
The files are loaded from `/components/...`, so the site must run at the root of the domain (https://toolzila.in/).
If these files cannot be loaded (for example the server is down), components.js shows a small built-in header and footer so visitors can still move around.
Opening the pages straight from a folder (file://) will not load them. Use a server (see below) or upload to your hosting.

## Local test
    python -m http.server 8000      then open http://localhost:8000

## Deploy
- Hostinger / cPanel: upload everything in this folder to public_html (include the hidden .htaccess file).
  It turns on compression and long caching. After your SSL certificate is active, open .htaccess and remove the
  # in front of the three HTTPS redirect lines at the bottom.
- Netlify / Vercel / Cloudflare Pages: upload or connect the folder.
- Point toolzila.in to it and use HTTPS.
- After you update header.html, footer.html or components.js, upload all three together.

## Already set up
- Google Analytics 4 (G-B7CHFPN4ZD) is in the head of every page.
- Contact email: toolzilaofficial@gmail.com (contact page, footer on every page, privacy policy).
- Your logo files: favicon.svg, og-image.png and the icons folder.

## Install like an app (phones)
Android Chrome: menu > Install app / Add to Home screen. iPhone Safari: Share > Add to Home Screen.

## Libraries (all hosted inside this site, in assets/vendor)
js-beautify, Terser, pdf-lib, pdf.js, heic2any, qrcodejs, ONNX Runtime Web (Background Remover, with the U2-Net-P model in assets/models).
Only Image to Text loads tesseract.js and its language data from a CDN on first use. Google Fonts load without blocking the page.

## SEO included
Unique title and description on every page, canonical links, Open Graph and Twitter cards with a share image,
sitemap.xml, robots.txt, breadcrumb, WebApplication and FAQ structured data. The files in /components are marked noindex.
The header and footer are added by JavaScript. Google can read them, and a plain-link fallback is inside each page for visitors without JavaScript.

## Before you apply for AdSense
- Search Console: add the site and submit /sitemap.xml.
- Add your own helpful content (guides, tips) so pages are not thin.
- After approval: paste the AdSense script inside the head of each page, below the Google Analytics code,
  put ad code at the "AD SLOT" comments, and add your line to ads.txt.
