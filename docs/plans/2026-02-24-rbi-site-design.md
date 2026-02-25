# RBI Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build the Robust Business Investments parent corp website — a corporate prestige single-page site + contact page.

**Architecture:** Static HTML + Tailwind CDN + vanilla JS. Light/white-dominant design with navy `#1b2a5e` and red `#c63a2b` brand colors. Same ecosystem patterns as raybedford.com and rbtechs.us but elevated parent-company feel.

**Tech Stack:** HTML, Tailwind CSS (CDN), vanilla JS, Web3Forms, Cloudflare Pages

---

### Task 1: Create project directory and initialize git repo

**Files:**
- Create: `/Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/`
- Create: `/Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/.gitignore`

**Step 1: Create directory**

```bash
mkdir -p /Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/contact
```

**Step 2: Create .gitignore**

```
.DS_Store
.wrangler/
.venv/
.idea/
node_modules/
```

**Step 3: Initialize git**

```bash
cd /Users/206750536@BWT3.COM/PycharmProjects/rbinvestments
git init
git add .gitignore
git commit -m "Initial commit: project setup"
```

---

### Task 2: Build index.html — head, nav, hero

**Files:**
- Create: `/Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/index.html`

**Reference:**
- Business card colors: navy `#1b2a5e`, red `#c63a2b`
- Logo: abstract architectural building forms (CSS recreation)
- Business card image at `/tmp/rbi_card-1.png` and `/tmp/rbi_card-2.png`
- Pattern reference: raybedford.com `index.html` and rbtechs.us `index.html`

**Step 1: Create the full index.html**

Build the complete page with all sections. The file should include:

**Head:** SEO meta tags for rbinvestments.us, OG/Twitter cards, Tailwind CDN, Font Awesome CDN, Google Fonts (Space Grotesk + Inter).

**Tailwind config:** Custom colors:
```js
tailwind.config = {
    theme: {
        extend: {
            colors: {
                rbi: {
                    navy: '#1b2a5e',
                    'navy-light': '#243572',
                    'navy-dark': '#121d40',
                    red: '#c63a2b',
                    'red-light': '#d94f40',
                    'red-dark': '#a82f22',
                }
            }
        }
    }
}
```

**Custom CSS:**
- Body: `font-family: 'Inter', sans-serif` on white/light bg
- `.heading-font`: Space Grotesk
- `.glass-nav`: white/frosted glass nav (`rgba(255,255,255,0.92)`, blur, subtle border)
- `.gradient-text`: navy-to-red gradient text
- Hero pattern: subtle geometric dots in navy at low opacity
- Brand card hover effects

**Navigation (fixed):**
- Left: CSS logo mark (abstract building shapes in navy + red, matching business card) + "ROBUST BUSINESS INVESTMENTS" text
- Right: About, Portfolio, Advisory links (dark text), Contact CTA button (navy bg, white text)
- Mobile hamburger menu

**Hero section (white bg with subtle pattern):**
- Pill badge: "Strategic Holding Company — Houston, TX"
- H1: "Building Resilient **Ventures.**" (red gradient on "Ventures")
- Subtext: RBI value prop about strategic investment and infrastructure
- CTAs: "Our Portfolio" (navy bg) + "Advisory Services" (outlined)
- Right side: decorative card with the RBI logo mark, quote, and company info (similar pattern to other sites)

**Step 2: Verify in browser**

```bash
open /Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/index.html
```

Verify: nav renders, hero looks correct, mobile menu works.

**Step 3: Commit**

```bash
cd /Users/206750536@BWT3.COM/PycharmProjects/rbinvestments
git add index.html
git commit -m "feat: add index.html with nav and hero"
```

---

### Task 3: Build index.html — about, portfolio, advisory, CTA, footer sections

**Files:**
- Modify: `/Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/index.html`

**About/Mission section (light gray `#f8f9fc` bg):**
- Heading: "Our Mission" with navy accent bar
- Narrative text about RBI's strategic investment philosophy
- Two narrative blocks with red left borders (matching pattern from other sites)

**Portfolio/Brands section (white bg):**
- Heading: "Our Portfolio"
- CSS grid of brand cards (`grid md:grid-cols-2 lg:grid-cols-3 gap-8`)
- Card 1: **RB Technical Solutions** — orange accent (`#e8621a`), microchip icon, description, link to rbtechs.us
- Card 2: **raybedford.com** — sky-blue accent (`#38bdf8`), shield icon, description, link to raybedford.com
- Cards have: colored icon container, brand name, description, "Visit Site →" link
- Grid scales naturally — adding a 3rd card fills the row

**Advisory Services section (white bg):**
- Heading: "Advisory Services"
- Three cards in a grid:
  1. Tech Acquisitions — briefcase icon
  2. Infrastructure Scaling — server icon
  3. Strategic Advisory — chart-line icon
- Navy + red palette, each card links to /contact

**CTA section (navy `#1b2a5e` bg):**
- White text heading: "Ready to Build Something **Resilient?**"
- Subtext
- Two CTAs: "Get in Touch" (white bg, navy text) + phone number (outlined white)

**Footer (navy bg):**
- Logo + "ROBUST BUSINESS INVESTMENTS"
- Contact: 917.426.8207, ray@rbinvestments.us
- Links: About, Portfolio, LinkedIn
- Copyright: © 2026 Robust Business Investments

**JS at bottom:**
- `toggleMenu()` for mobile nav (same pattern as other sites)

**Step 1: Add all remaining sections to index.html**

**Step 2: Verify in browser**

Check: all sections render, brand cards look right, links work, mobile responsive.

**Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add about, portfolio, advisory, CTA, and footer sections"
```

---

### Task 4: Build contact/index.html

**Files:**
- Create: `/Users/206750536@BWT3.COM/PycharmProjects/rbinvestments/contact/index.html`

**Reference:** raybedford.com `/contact/index.html` — adapt the same two-column layout but with RBI's light theme and brand colors.

**Structure:**
- Same head setup as index.html (SEO for rbinvestments.us/contact)
- Navigation identical to index.html (nav link shows "Contact" as active)
- Left column: heading "Let's Build Together.", subtext, contact channels (LinkedIn, phone, email cards)
- Right column: Web3Forms form with:
  - Hidden access_key: `13d70201-919c-4463-885d-8ffb572b87f8`
  - Hidden subject: "New inquiry from rbinvestments.us"
  - Fields: Full Name, Email, Service Interest (dropdown: Strategic Advisory, Tech Acquisition Consulting, Infrastructure Scaling, Partnership Inquiry, Other), Message
  - Submit button in navy
- Footer same as index.html
- JS: `toggleMenu()` + `handleSubmit()` (same Web3Forms pattern)

**Key difference from raybedford.com contact:** Light backgrounds instead of dark. Navy/red accents instead of sky-blue. Form fields have white bg with navy borders.

**Step 1: Create contact/index.html**

**Step 2: Verify form submission works**

Open in browser, fill out test data, verify Web3Forms integration.

**Step 3: Commit**

```bash
git add contact/index.html
git commit -m "feat: add contact page with Web3Forms integration"
```

---

### Task 5: Create GitHub repo and deploy to Cloudflare Pages

**Step 1: Create GitHub repo**

```bash
cd /Users/206750536@BWT3.COM/PycharmProjects/rbinvestments
gh auth switch --user raybedford
gh repo create raybedford/rbinvestments --public --source=. --push
```

**Step 2: Deploy to Cloudflare Pages**

```bash
npx wrangler pages project create rbinvestments --production-branch main
npx wrangler pages deploy . --project-name rbinvestments
```

Expected: site live at `https://rbinvestments.pages.dev`

**Step 3: Verify deployment**

Open `https://rbinvestments.pages.dev` in browser and confirm all pages work.

---

### Task 6: Update project memory

**Files:**
- Modify: `/Users/206750536@BWT3.COM/.claude/projects/-Users-206750536-BWT3-COM-PycharmProjects-raybedfordwebsite/memory/MEMORY.md`

Add RBI site entry with location, GitHub URL, Cloudflare Pages project name, brand colors, and domain info.
