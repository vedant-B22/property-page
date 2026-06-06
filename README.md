"# property-page" 
# 🏠 Property Page — Scroll-Driven Frame Animation

A luxury real estate landing page where scrolling plays a cinematic frame-by-frame animation — like Apple's iPhone product pages, but for property.

---

## 📁 Folder Structure

```
C:\property-page\
│
├── index.html           ← The entire website (single file)
└── combined_frames.zip  ← Your 452 PNG frames packed into a ZIP
```

That's it. Two files. Nothing else needed.

---

## 🚀 How to Run It

### Step 1 — Open Terminal in the project folder
- Open **Command Prompt**
- Type: `cd C:\property-page`
- Press Enter

### Step 2 — Start the local server
```bash
python -m http.server 8080
```

### Step 3 — Open in browser
Go to:
```
http://localhost:8080
```

Leave the terminal open while you're using the site. If you close it, the site stops working.

---

## ⚠️ Common Errors & Fixes

### ❌ `404 — combined_frames.zip not found`
The HTML is looking for the ZIP in the wrong place.

**Fix:** Open `index.html` in Notepad → press `Ctrl+H` → Find & Replace:
- Find: `/mnt/user-data/uploads/combined_frames.zip`
- Replace with: `combined_frames.zip`

Save and refresh the browser.

---

### ❌ Page loads but animation doesn't start
The frames haven't finished preloading yet. Wait for the gold progress bar to reach 100% — animation unlocks automatically after that.

---

### ❌ Progress bar stuck at 0%
The ZIP file is either missing from the folder or named differently.

**Check:** Make sure the file is named exactly `combined_frames.zip` (all lowercase, no spaces) and is sitting inside `C:\property-page\` — same folder as `index.html`.

---

### ❌ Animation is choppy or laggy
Your browser is decoding 452 frames into memory. Give it 10–15 seconds after the progress bar hits 100% before scrolling. Chrome works best for this.

---

## 🎞️ How the Animation Works

1. Page loads → JSZip extracts all 452 PNG frames from the ZIP
2. Each frame is converted to a base64 data URL and stored in a `frames[]` array
3. A fullscreen `<canvas>` is pinned to the viewport
4. As you scroll, your scroll position maps to a frame index:
   ```
   frameIndex = Math.floor((scrollY / maxScroll) * 452)
   ```
5. The matching frame is drawn on the canvas on every scroll event
6. After the animation zone ends (~1356px of scroll), the rest of the page appears normally below

---

## 🎨 Design Palette

| Name | Hex | Used For |
|---|---|---|
| Beige | `#f5f0e8` | Page background |
| Deep Beige | `#e8dfd0` | Card fills, section alternates |
| Gold | `#C9A84C` | Accents, borders, highlights |
| Silk | `#faf7f2` | Canvas backdrop, loading screen |
| Brown | `#5c3d2e` | Labels, dividers, footer text |
| Deep Brown | `#3a2318` | Headlines |
| Text | `#2e1f0f` | Body copy |

---

## 📦 What's Inside `index.html`

| Section | Description |
|---|---|
| Loading screen | Silk background + gold progress bar while frames load |
| Scroll animation | 452-frame canvas scrub pinned fullscreen |
| Hero text overlay | Fades in over the last 30 frames — serif italic headline + tagline |
| Property stats | 4 metric cards — area, bedrooms, price, location |
| Contact form | Frosted glass card with name, email, phone, message |
| Footer | Hairline gold border, brown text |

---

## 🛠️ How to Swap Your Own Frames

1. Export your video as PNG frames using ffmpeg:
   ```bash
   ffmpeg -i your-video.mp4 -vf fps=24 frames/ezgif-frame-%03d.png
   ```
2. ZIP all the frames into one file named `combined_frames.zip`
3. Replace the old ZIP in `C:\property-page\`
4. Update the frame count in `index.html` if it's not 452:
   - Search for `452` in the file and replace with your actual frame count

---

## 💻 Tech Stack

| Tool | Purpose |
|---|---|
| Vanilla HTML/CSS/JS | Entire page — no frameworks |
| JSZip (CDN) | Extracts PNG frames from ZIP in the browser |
| HTML5 Canvas | Draws frames fullscreen on scroll |
| Google Fonts | Cormorant Garamond (headlines) + Jost (body) |
| Python http.server | Local development server |

---

## 🌐 Deploying to Netlify (Go Live)

1. Go to [netlify.com](https://netlify.com) and log in
2. Drag and drop the entire `C:\property-page\` folder onto the Netlify dashboard
3. Netlify gives you a live URL instantly

> **Note:** The ZIP file (348 MB) may be large for Netlify's free tier limit. If it fails, compress your frames further or reduce frame count using ffmpeg before uploading.

---

## 📞 Built by

**Vesa Studios** — Creative Branding & Design, Pune
- 🌐 [vesastudios.site](https://vesastudios.site)
- 📧 vesastudios1@gmail.com
- 📱 +91 92266 34637"# property-page" 
"# property-page" 
