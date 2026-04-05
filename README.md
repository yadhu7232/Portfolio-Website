# Portfolio-Website
Yadhu Krishna — Portfolio Website
A personal portfolio website built as a single self-contained HTML file with embedded CSS and JavaScript. No frameworks, no build tools, no dependencies beyond two Google Fonts.
---
File Structure
```
index.html        ← Everything lives here (HTML + CSS + JS + base64 photo)
README.md         ← This file
```
The entire site is one file. Styles are written inside a `<style>` block in the `<head>`, and scripts are in a `<script>` block just before `</body>`. The profile photo is embedded as a base64 data URI so no external image files are needed.
---
Page Sections
Section	ID	Description
Navigation	`nav`	Fixed top bar with logo and smooth-scroll links
Hero	`#home`	Name, tagline (typewriter), CTA buttons, quick profile card
About	`#about`	Bio text, portrait photo, quote, at-a-glance stats
Skills	`#skills`	Four skill cards — Languages, Frontend, CS Fundamentals, Tools
Education	`#education`	B.Tech at Amrita Vishwa Vidyapeetham
Projects	`#projects`	Three project cards with tags and links
Achievements	`#achievements`	Three achievement items on dark background
Contact	`#contact`	Email, location, Quick Links card, Send Email button
Footer	`footer`	Name, nav links, copyright
---
HTML Highlights
Semantic structure — `<nav>`, `<section>`, `<footer>` used throughout for clarity and accessibility
Single file — all assets (photo, favicon, fonts) are either embedded or loaded via CDN link
Favicon — inline SVG data URI in `<link rel="icon">`, renders a gold YK on dark background in the browser tab
External fonts only — one Google Fonts `<link>` loads Cormorant Garamond (serif headings) and DM Sans (body text)
Responsive meta tag — `<meta name="viewport">` ensures correct scaling on mobile
Working links — all contact links use `mailto:` or `https://` with `rel="noopener noreferrer"` on external targets
---
CSS Highlights
Design Tokens (CSS Custom Properties)
All colours and font stacks are defined as variables in `:root`:
```css
--bg: #f5f2ee        /\* warm parchment background \*/
--ink: #1a1714       /\* near-black text \*/
--gold: #b8955a      /\* primary accent \*/
--gold2: #d4b07a     /\* lighter gold for gradients \*/
--serif: 'Cormorant Garamond', Georgia, serif
--sans: 'DM Sans', sans-serif
```
Changing one variable updates every element that uses it across the whole page.
Layout
CSS Grid — used for the hero, about, and contact two-column layouts (`grid-template-columns: 1fr 1fr`)
auto-fit minmax — skills and projects grids are fully responsive without media queries (`repeat(auto-fit, minmax(240px, 1fr))`)
Fixed nav — `position: fixed` with `backdrop-filter: blur(12px)` for the frosted glass effect
Typography
`clamp()` used on hero name and section titles for fluid type scaling between viewport sizes
Section titles use a CSS gradient text technique (`background-clip: text` + `-webkit-text-fill-color: transparent`) to create the ink-to-gold gradient effect
Animations & Transitions
Feature	Technique
Scroll reveal	`IntersectionObserver` adds `.visible` class; CSS `opacity` + `translateY` transition
Staggered cards	`transition-delay` via `:nth-child()` selectors on grid children
Typewriter	JavaScript writes characters one by one into the span; blinking cursor via `@keyframes blink`
Magnetic buttons	`mousemove` event calculates offset from button centre and applies `translate()`
Parallax hero	`scroll` event updates `translateY` on the background circle at 25% scroll speed
Active nav	`IntersectionObserver` on each `<section>` adds `.active` to the matching nav link
Cursor dot	`mousemove` event positions a fixed gold `div`; scales up on hover over interactive elements
Scroll progress	`scroll` event sets `width %` on a fixed 2px gold bar at top of viewport
Glassmorphism (Contact Card)
```css
background: rgba(250, 248, 245, 0.6);
backdrop-filter: blur(18px);
border: 1px solid rgba(184,149,90,0.25);
```
Responsive Breakpoints
`max-width: 900px` — two-column grids collapse to single column; nav padding reduces
`max-width: 600px` — nav links hidden; hero card goes full width; education block reflows
---
JavaScript Summary
All JS is vanilla (no libraries). Three main concerns:
UI interactions — scroll progress bar, cursor dot, magnetic buttons, parallax
Scroll observation — `IntersectionObserver` used twice: once for reveal animations, once for active nav highlighting
Typewriter — a `setInterval` loop that slices the full string progressively into the element's `textContent`
---
Fonts Used
Font	Style	Used For
Cormorant Garamond	Light, Regular, SemiBold, Italic	Headings, logo, quotes, card values
DM Sans	Light, Regular, Medium	Body text, nav, buttons, labels
---
Contact Links
Channel	Value
Email	yadhu7232@gmail.com
GitHub	github.com/yadhu7232
University	amrita.edu
