# Handoff: Oh Shit, Did We Just Kill a Guy? — Promotional Film Site

## Overview
A minimal, cinematic promotional website for the micro short film "Oh Shit, Did We Just Kill a Guy?" created by Taylor Drew and directed by Oscar Monroy. The site is a single-page app with hash-based routing across 5 sections: Film (home), Cast, Crew, Awards, and Contact.

## About the Design Files
The files in this bundle are **design references created in HTML** — prototypes showing intended look and behavior, not production code to copy directly. The task is to **recreate these designs** in the target codebase's existing environment (React, Next.js, Astro, etc.) using its established patterns. If no environment exists yet, a static site generator like Astro or a simple Next.js app would be ideal given the site's simplicity.

## Fidelity
**High-fidelity.** The prototype uses final colors, typography, spacing, and interactions. Recreate the UI faithfully using the codebase's libraries and patterns.

---

## Site Structure

The site is a **single-page application** with 5 views, navigated via hash routing (`#home`, `#cast`, `#crew`, `#awards`, `#contact`). Arrow keys also cycle between pages.

Every page shares the same structure:
1. **Full-bleed background still** — a film frame filling the entire viewport via `background-size: cover`
2. **Top navigation bar** — thin, evenly spaced horizontal row of section links
3. **Centered title block** — film title + optional eyebrow/subtitle + page-specific content
4. **Laurels row** — festival laurels displayed at the bottom, each clickable (linking to FilmFreeway)
5. **Footer credit line** — small text at very bottom

The **Awards page** has a unique layout: title shrinks to the top, laurels expand into a 3-column grid filling the viewport.

---

## Screens / Views

### All Pages (Shared Structure)

#### Top Navigation
- **Layout**: Centered horizontal flex row, max-width 980px
- **Border**: 1px bottom border, `rgba(243,239,231,0.22)`
- **Links**: FILM | CAST | CREW | AWARDS | CONTACT
- **Typography**: Oswald, 12.5px, weight 500, letter-spacing 0.32em, uppercase
- **Color**: `rgba(243,239,231,0.72)` default, `#f3efe7` on hover and active
- **Active indicator**: 1px solid bottom border in `#f3efe7`
- **Separators**: 1px × 11px vertical bars between links, same color as border
- **Responsive**: On narrow screens (<540px), nav scrolls horizontally; separators hidden <720px

#### Background Still
- **Behavior**: `position: absolute; inset: 0; background-size: cover; background-position: center`
- **Transition**: 700ms opacity ease on page change
- **Vignette overlay** (via `::after` on `.stage`):
  - Top-to-bottom gradient: 55% black → 18% → 18% → 62% black
  - Radial vignette: transparent center → 42% black edges

#### Centered Content Block
- **Position**: Absolute, fills viewport, flex column centered
- **Padding**: 70px top (clears nav), 140px bottom (clears laurels), 24px sides
- **Eyebrow**: Oswald italic, 14px, letter-spacing 0.18em, lowercase, `rgba(243,239,231,0.72)`
- **Title**: Anton, `clamp(28px, 5.4vw, 86px)`, uppercase, white-space nowrap on desktop (one line), wraps to max 2 lines on mobile (<900px) at `clamp(32px, 8vw, 64px)`
- **Title text**: "OH SHIT, DID WE JUST KILL A GUY?"
- **Text shadow**: `0 2px 28px rgba(0,0,0,0.65)`
- **Subtitle**: Oswald, `clamp(13px, 1.2vw, 16px)`, weight 400, letter-spacing 0.36em, uppercase, dimmed color. 36px top margin.

#### Laurels Row (non-Awards pages)
- **Position**: Absolute, bottom 56px, full width
- **Layout**: Flex row, wrap, centered, gap `clamp(14px, 2.6vw, 36px)`, padding 0 32px
- **Laurel images**: Height `clamp(54px, 7.2vh, 84px)`, auto width, opacity 0.95
- **Hover**: opacity 1, translateY(-2px), 200ms ease
- **Each laurel is a link** opening the festival's FilmFreeway page in a new tab

#### Footer Line
- **Position**: Absolute, bottom 18px, centered
- **Text**: "Created by Taylor Drew · Directed by Oscar Monroy · 2026"
- **Typography**: Oswald italic, 11px, letter-spacing 0.28em, uppercase, `rgba(243,239,231,0.55)`

---

### Home (`#home`)
- **Background**: `stills/still-home.png` (overhead shot — body on shopping cart, two figures in orange vests)
- **Eyebrow**: "a micro short"
- **Title**: OH SHIT, DID WE JUST KILL A GUY?
- **Subtitle**: (empty)

### Cast (`#cast`)
- **Background**: `stills/still-cast.png` (golden-hour, two figures dragging body on roadside)
- **Eyebrow**: "the cast"
- **Subtitle**: "Cast"
- **Content**: Roster grid (2 columns on desktop, 1 on mobile)
  - Starring — TAYLOR DREW
  - Starring — ADIEL KAY
  - Featuring — EVAN KASH
- **Roster row**: Flex row, space-between, 6px padding, 1px bottom border `rgba(243,239,231,0.10)`
- **Role text**: Italic, weight 300, dimmed
- **Name text**: Uppercase, letter-spacing 0.12em, weight 500, 0.92em size

### Crew (`#crew`)
- **Background**: `stills/still-crew.png` (car window — bearded man and woman)
- **Eyebrow**: "the crew"
- **Subtitle**: "Crew"
- **Content**: Same roster grid format
  - Created by — TAYLOR DREW
  - Directed by — OSCAR MONROY
  - Director of Photography — MIKE CERISANO
  - Costume Design — TAYLOR DREW
  - Asst. Camera & Grip — MIGUEL DUSAUZAY
  - Music — JARED BAILEY

### Awards (`#awards`)
- **Background**: `stills/still-awards.png` (wide road shot with car and body)
- **Unique layout**: Title moves to top, shrinks; laurels become a large centered grid
- **Title**: `clamp(16px, 2vw, 24px)`, nowrap
- **Eyebrow**: 10px
- **Subtitle**: Hidden
- **Footer**: Hidden
- **Center content**: `padding-top: 70px`, flex-start alignment
- **Laurels grid**:
  - Position: absolute, top 140px, bottom 36px, full width
  - Display: grid, 3 columns, auto rows
  - Gap: `clamp(10px, 2vw, 32px)`
  - Padding: `0 clamp(32px, 6vw, 120px)`
  - Each laurel: width 100%, max-width 200px, auto height, object-fit contain
  - On mobile (<760px): still 3 columns, top 120px, gap 8px, padding 0 14px, max-width 140px

### Contact (`#contact`)
- **Background**: `stills/still-contact.png` (close-up car door scene)
- **Eyebrow**: "for press & bookings"
- **Subtitle**: "Contact"
- **Content**: Single centered link to FilmFreeway
  - Typography: `clamp(15px, 1.3vw, 19px)`
  - Link style: 1px bottom border, hover brightens border

---

## Interactions & Behavior
- **Page transitions**: Background stills cross-fade with 700ms opacity transition
- **Hash routing**: `hashchange` event drives navigation; default is `#home`
- **Keyboard navigation**: Left/Right arrow keys cycle pages
- **Nav active state**: Current page link gets bottom border + full white color
- **Laurel hover**: Slight lift (translateY -2px) + full opacity
- **No scrolling**: `overflow: hidden` on html/body — each page fits viewport exactly
- **Responsive**: Nav scrolls horizontally on narrow screens; title wraps to 2 lines max on mobile; laurels shrink and re-gap; roster goes single column

---

## Design Tokens

### Colors
| Token | Value | Usage |
|-------|-------|-------|
| `--fg` | `#f3efe7` | Primary text (warm white) |
| `--fg-dim` | `rgba(243,239,231,0.72)` | Secondary text |
| `--rule` | `rgba(243,239,231,0.22)` | Borders, separators |
| Background | `#000` | Page background (behind stills) |
| Vignette | `rgba(0,0,0,0.42)` at edges | Radial vignette over stills |

### Typography
| Role | Font | Size | Weight | Spacing |
|------|------|------|--------|---------|
| Title | Anton | clamp(28px, 5.4vw, 86px) | 400 | 0.005em |
| Nav | Oswald | 12.5px | 500 | 0.32em |
| Eyebrow | Oswald italic | 14px | 400 | 0.18em |
| Subtitle | Oswald | clamp(13px, 1.2vw, 16px) | 400 | 0.36em |
| Footer | Oswald italic | 11px | 400 | 0.28em |
| Roster role | Oswald italic | inherit | 300 | — |
| Roster name | Oswald | 0.92em | 500 | 0.12em |

### Google Fonts
```
Anton (400)
Oswald (300, 400, 500, 600, 700)
```

---

## Festival Laurels (10 total)
All laurels have transparent backgrounds (black removed via threshold processing). Each links to the festival's FilmFreeway page.

| # | File | Festival | Award | FilmFreeway URL |
|---|------|----------|-------|-----------------|
| 1 | `altff-winner.png` | AltFF Alternative Film Festival | Winner — Best Writer, Super Short Category (Spring 2026) | filmfreeway.com/AltFFAlternativeFilmFestival |
| 2 | `jersey-devil.png` | The Jersey Devil Film Festival | Official Selection | filmfreeway.com/TheJerseyDevilFilmFestival |
| 3 | `lic-best-micro-short.png` | Long Island Cinema Festival | Best Micro Short 2026 | filmfreeway.com/LongIslandCinemaFestival |
| 4 | `altff-director.png` | AltFF Alternative Film Festival | Best Director Nominee 2026 | filmfreeway.com/AltFFAlternativeFilmFestival |
| 5 | `altff-selection.png` | AltFF Alternative Film Festival | Official Selection 2026 | filmfreeway.com/AltFFAlternativeFilmFestival |
| 6 | `east-village.png` | East Village New York Film Festival | Official Selection 2026 | filmfreeway.com/EastVillageNewYorkFilmFestival |
| 7 | `giggle-shitz.png` | Giggle Shitz Film Festival | Official Selection | filmfreeway.com/GiggleShitzFilmFestival |
| 8 | `lic-cinematographer.png` | Long Island Cinema Festival | Best Cinematographer 2026 | filmfreeway.com/LongIslandCinemaFestival |
| 9 | `lic-micro-short-nominee.png` | Long Island Cinema Festival | Best Micro Short Nominee 2026 | filmfreeway.com/LongIslandCinemaFestival |
| 10 | `lic-official-selection.png` | Long Island Cinema Festival | Official Selection 2026 | filmfreeway.com/LongIslandCinemaFestival |

---

## Assets

### Stills (full-bleed backgrounds)
| File | Description | Used on |
|------|-------------|---------|
| `stills/still-home.png` | Overhead — body on shopping cart, two figures in orange vests | Home |
| `stills/still-cast.png` | Golden-hour — two figures dragging body on roadside | Cast |
| `stills/still-crew.png` | Car window — bearded man and woman | Crew |
| `stills/still-awards.png` | Wide road shot — car, body, two figures | Awards |
| `stills/still-contact.png` | Close-up — car door, woman's face | Contact |

### Laurels
All in `laurels/` folder — 10 PNG files with transparent backgrounds (see table above).

---

## Files in This Bundle
- `README.md` — This file
- `Oh Shit Did We Just Kill A Guy.html` — Complete working prototype (single HTML file, hash-routed SPA)
- `stills/` — 5 background still images
- `laurels/` — 10 festival laurel images (transparent PNGs)

---

## Notes for Implementation
- The prototype is a vanilla HTML/JS single-page app. For production, consider a static site generator (Astro, Next.js static export) for better SEO and asset optimization.
- Images should be converted to WebP and served at appropriate sizes for performance.
- The laurel images have been processed to remove black backgrounds; originals are in the `uploads/` folder if re-processing is needed.
- The site has a Tweaks panel (for development only) exposing typeface, vignette intensity, and type tone — this should be removed in production.
- All external links (laurels, contact) open in new tabs with `rel="noopener"`.
- The site uses no third-party JS libraries — just vanilla JS with Google Fonts.
