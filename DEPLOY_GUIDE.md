# Deploy automateloops.com to Vercel (Free)

This guide takes roughly 10 minutes and requires no credit card.

---

## Step 1 — Push the site to GitHub

1. Create a free account at [github.com](https://github.com) if you don't have one.
2. Create a **new repository** (e.g., `automateloops-site`). Set it to **Private** if you prefer.
3. Upload all files in this directory to the repository root:
   - `index.html`
   - `privacy.html`
   - `terms.html`
   - `support.html`
   - `style.css`
   - `vercel.json`

   **Quickest way via GitHub web UI:**
   - Open the repository → click **Add file → Upload files**
   - Drag all 6 files in → click **Commit changes**

   **Or via Git CLI:**
   ```bash
   cd /path/to/automateloops-site
   git init
   git add .
   git commit -m "Initial site"
   git remote add origin https://github.com/YOUR_USERNAME/automateloops-site.git
   git push -u origin main
   ```

---

## Step 2 — Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) and sign up / log in with your GitHub account.
2. Click **Add New… → Project**.
3. Find and select your `automateloops-site` repository → click **Import**.
4. On the configuration screen:
   - **Framework Preset:** leave as **Other**
   - **Root Directory:** leave as `/` (default)
   - No build command or output directory needed for a static site
5. Click **Deploy**.

Vercel will build and deploy in under 30 seconds. You'll get a free preview URL like `automateloops-site.vercel.app`.

---

## Step 3 — Connect your custom domain (automateloops.com)

1. In your Vercel project dashboard, go to **Settings → Domains**.
2. Type `automateloops.com` and click **Add**.
3. Also add `www.automateloops.com` and set it to redirect to the apex domain.
4. Vercel will show you the DNS records to add. You'll need to log in to your domain registrar (e.g., GoDaddy, Namecheap, Cloudflare).

### DNS records to add at your registrar

| Type  | Name | Value                        |
|-------|------|------------------------------|
| A     | @    | `76.76.21.21`                |
| CNAME | www  | `cname.vercel-dns.com`       |

> **Note:** If your registrar doesn't support CNAME flattening for the apex domain, use the A record above instead.

5. DNS propagation typically takes 5–30 minutes. Vercel will show a green checkmark once it's verified.
6. Vercel automatically provisions a free SSL certificate (HTTPS) — no action needed.

---

## Step 4 — Verify the live URLs

Once DNS propagates, confirm these URLs all work:

| URL | Expected |
|-----|----------|
| `https://automateloops.com` | Homepage |
| `https://automateloops.com/privacy` | Privacy Policy |
| `https://automateloops.com/terms` | Terms of Service |
| `https://automateloops.com/support` | Support / FAQ |

---

## Step 5 — Future updates

Any time you push a commit to your GitHub repository, Vercel will automatically redeploy the site within seconds. No manual steps needed.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| DNS not propagating | Wait up to 48 hours; check with [dnschecker.org](https://dnschecker.org) |
| `/privacy` returns 404 | Confirm `vercel.json` is in the repo root |
| SSL certificate pending | Wait 10–15 minutes after DNS verifies |
| Old content showing | Hard-refresh with Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows) |

---

## App Store / Play Store legal URL checklist

These URLs must be live before submitting to the app stores:

- [x] `https://automateloops.com/privacy` — required by Apple & Google
- [x] `https://automateloops.com/terms` — required by Apple & Google
- [x] `https://automateloops.com/support` — required by Apple (support URL field)
