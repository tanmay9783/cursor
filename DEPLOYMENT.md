# Deployment Guide

## Quick Start - GitHub Pages Deployment

### Step 1: Create GitHub Repository

1. Go to GitHub.com and log in
2. Click the "+" icon in the top-right corner
3. Select "New repository"
4. Name it: `cursor-landing-page` (or any name you prefer)
5. Make it **Public** (required for free GitHub Pages)
6. Do NOT initialize with README (we already have one)
7. Click "Create repository"

### Step 2: Push Your Code

Open terminal in your project folder and run:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit: Cursor landing page recreation"

# Add GitHub remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/cursor-landing-page.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click "Settings" tab
3. Scroll down to "Pages" in the left sidebar
4. Under "Source", select "main" branch
5. Click "Save"
6. Wait 1-2 minutes for deployment

Your site will be live at:
```
https://YOUR_USERNAME.github.io/cursor-landing-page/
```

## Alternative Deployment - Netlify

### Option 1: Drag & Drop

1. Go to [netlify.com](https://netlify.com)
2. Sign up or log in
3. Drag your project folder to the upload area
4. Get instant deployment URL

### Option 2: GitHub Integration

1. Push code to GitHub (see Step 2 above)
2. Go to Netlify and click "Add new site"
3. Choose "Import from Git"
4. Connect to GitHub
5. Select your repository
6. Click "Deploy"

Benefits:
- Automatic deployments on git push
- Custom domain support
- HTTPS enabled
- Fast CDN

## Alternative Deployment - Vercel

1. Push code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Sign up with GitHub
4. Click "Import Project"
5. Select your repository
6. Click "Deploy"

Benefits:
- Zero configuration
- Fast global CDN
- Automatic HTTPS
- Preview deployments

## Pre-Deployment Tasks

Before deploying, make sure to:

### 1. Add Missing Images

Replace placeholder images with actual screenshots:

```bash
# Download images from Cursor website or create your own
# Save them in the images/ folder with correct names:

images/
├── hero-screenshot.jpg
├── feature-agent.jpg
├── feature-tab.png
├── feature-ecosystem.jpg
├── models-screenshot.png
├── search-screenshot.png
├── team-photo.jpg
├── team-photo-main.jpg
└── [avatars and logos...]
```

### 2. Update Meta Tags

Add to `<head>` section in index.html:

```html
<!-- SEO Meta Tags -->
<meta name="description" content="Cursor landing page recreation - A pixel-perfect HTML/CSS implementation">
<meta name="keywords" content="Cursor, IDE, AI code editor, landing page, HTML, CSS">
<meta name="author" content="Your Name">

<!-- Open Graph Meta Tags (for social sharing) -->
<meta property="og:title" content="Cursor Landing Page Recreation">
<meta property="og:description" content="A pixel-perfect recreation of the Cursor IDE landing page">
<meta property="og:image" content="https://your-url.com/images/hero-screenshot.jpg">
<meta property="og:url" content="https://your-url.com">
<meta property="og:type" content="website">

<!-- Twitter Card Meta Tags -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Cursor Landing Page Recreation">
<meta name="twitter:description" content="A pixel-perfect recreation of the Cursor IDE landing page">
<meta name="twitter:image" content="https://your-url.com/images/hero-screenshot.jpg">
```

### 3. Add Favicon

Create a favicon and add to `<head>`:

```html
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```

### 4. Add Analytics (Optional)

If you want to track visitors, add Google Analytics:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=YOUR_GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'YOUR_GA_ID');
</script>
```

## Post-Deployment Checklist

After deployment, verify:

- [ ] Page loads without errors
- [ ] All images display correctly
- [ ] All links work (or go to appropriate anchors)
- [ ] CSS loads properly
- [ ] Fonts display correctly
- [ ] Page looks identical to local version
- [ ] No console errors in browser
- [ ] Mobile view works (if added)
- [ ] Page speed is acceptable (use PageSpeed Insights)

## Custom Domain Setup

### GitHub Pages

1. Buy domain from provider (Namecheap, GoDaddy, etc.)
2. Add DNS records:
   ```
   Type: CNAME
   Host: www
   Value: YOUR_USERNAME.github.io
   ```
3. In GitHub Settings → Pages, add custom domain
4. Wait for DNS propagation (up to 48 hours)

### Netlify/Vercel

1. Go to domain settings in Netlify/Vercel
2. Click "Add custom domain"
3. Follow the DNS setup instructions
4. Wait for SSL certificate generation

## Troubleshooting

### Images Not Loading

- Check file paths (case-sensitive on Linux servers)
- Verify images exist in images/ folder
- Check image file extensions match HTML

### CSS Not Loading

- Verify styles.css is in root folder
- Check link tag in HTML
- Clear browser cache

### Fonts Not Loading

- Check Google Fonts link in `<head>`
- Verify internet connection
- Check browser console for errors

### GitHub Pages 404 Error

- Check repository is public
- Verify Pages is enabled in settings
- Wait a few minutes for deployment
- Check branch name matches (main or master)

## Performance Optimization

Before going live, optimize:

1. **Compress Images**
   - Use TinyPNG or ImageOptim
   - Convert to WebP format
   - Reduce file sizes

2. **Minify CSS**
   ```bash
   # Using cssnano
   npm install cssnano-cli -g
   cssnano styles.css styles.min.css
   ```

3. **Enable Caching**
   - Add `.htaccess` for Apache
   - Configure cache headers

4. **Use CDN**
   - GitHub Pages includes CDN
   - Netlify/Vercel have built-in CDN

## Monitoring

Track your site's performance:

1. **Google PageSpeed Insights**
   - https://pagespeed.web.dev/

2. **GTmetrix**
   - https://gtmetrix.com/

3. **WebPageTest**
   - https://www.webpagetest.org/

## Support

If you encounter issues:

1. Check browser console for errors
2. Verify all files are uploaded
3. Test in incognito mode
4. Clear cache and hard reload
5. Check deployment logs

---

**Remember**: This is a static site, so deployment is simple. Just upload the files and you're done! No server configuration needed.

Good luck with your deployment! 🚀
