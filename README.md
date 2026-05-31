# Urban Roti — Catering Inquiry Form

A single-file web form. Customers fill it in and tap **Send on WhatsApp** or **Send via Email** — the form opens a pre-filled message addressed to the restaurant with every detail formatted. No server, database, or login required.

## 1. Set your contact details (one-time)

Open `index.html` and edit these two lines near the bottom (in the `CONFIG` block):

```js
const RESTAURANT_WHATSAPP = "919999999999"; // your WhatsApp number, international format, no + or spaces
const RESTAURANT_EMAIL    = "admin@urbanroti.com.sg"; // your inquiry inbox (already set)
```

- Email is already set to `admin@urbanroti.com.sg`.
- WhatsApp still needs your number: country code + number, digits only. Singapore example: `65` + `81234567` → `6581234567`.

## Logo — add the real artwork (one step)

The form looks for a file named **`logo.png`** in this same folder and shows it at the top. Until that file exists, it displays a built-in on-brand SVG recreation so nothing looks broken.

To use the real logo, save the image file here:

```
C:\Users\swam9\Desktop\catering inquiry form\logo.png
```

Easiest way:
1. Open the logo image (the one you have).
2. Right-click → **Save image as…** (or in an editor, **Export / Save As**).
3. Navigate to the `catering inquiry form` folder, name it `logo.png`, save.
4. Refresh the form — the real logo replaces the placeholder automatically.

A PNG with a transparent background looks best on the white header. (A `.jpg` works too — just rename the reference in `index.html` from `logo.png` to `logo.jpg`.)

## 2. Try it locally

Just double-click `index.html` to open it in any browser.

## 3. Live weblink (auto-deployed via GitHub Pages)

This repo includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that
**automatically publishes the form every time you push to `main`**.

**One-time setup:** in the repo, go to **Settings → Pages → Build and deployment**
and set **Source = GitHub Actions**. After the next push, the workflow deploys the site.

Live URL:

```
https://swam90.github.io/Urban_Roti_Inquiry_form/
```

You can watch deploys under the repo's **Actions** tab.

## 4. Share the weblink

- **WhatsApp:** paste the URL into any chat, or your Business catalog / status.
- **Email:** add the URL to your signature or campaigns.
- **QR code:** print `qr-code.png` (or `qr-code.svg` for sharp large prints) on flyers,
  menus, and table cards. It points straight to the live form. Regenerate it any time with:

  ```bash
  python -m pip install segno
  python -c "import segno; segno.make('https://swam90.github.io/Urban_Roti_Inquiry_form/', error='h').save('qr-code.png', scale=12, border=4, dark='#3a2317', light='#ffffff')"
  ```

## How submissions reach you

When a customer submits, **their** phone opens WhatsApp (or email) with the inquiry pre-filled and your number/address as the recipient. They tap send, and it lands in your inbox like a normal message — including name, contact, event type, slot, date (dd/mm/yyyy), time (12-hr), pax (adults + kids), venue, menu, and notes.
