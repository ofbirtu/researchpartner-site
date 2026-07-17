## Paper Pieces — how to build with this system

Paper Pieces is a **CSS-token + paper-art house style**, not a React component
library. There are **no importable components** on `window.PaperPieces` — it is an
empty namespace by design. You build on-brand work by composing plain HTML/JSX
and styling it with the design tokens below; the specimen cards under
`components/` are **reference patterns to copy**, not parts to import.

### Setup (the only wiring there is)
Link the stylesheet once. It `@import`s the tokens and the paper-art data-URIs and
loads the two webfonts from Google Fonts. No provider, no theme object, no root
wrapper.
```html
<link rel="stylesheet" href="styles.css">
```

### The styling idiom — CSS custom properties, no utility classes
Everything is expressed through `var(--*)` tokens. Never hardcode a hex or a font
name; never introduce a different colour or family.

**Colour (no pure white exists):** `--pp-ink` `#0A0A0A` · `--pp-paper` `#E8E8EC`
(the only "light" — cards/surfaces) · `--pp-line` `#DCDAD2` (borders + the greige
"paper" ground) · `--pp-muted` `#7E7C74`. **Accents (used as grounds AND as paper
pieces):** `--pp-chartreuse` `#CFD64B` (primary accent/highlight) · `--pp-khaki`
`#A2926A` · `--pp-peri` `#C2CBE9` · `--pp-peach` `#F4C3AB`. Heat ramp
`--pp-hm-1…--pp-hm-5` (chartreuse alpha, for matrix cells/glows). Semantic
aliases: `--text-body` `--text-muted` `--text-on-dark` `--surface-card`
`--surface-card-dark` `--border-line` `--accent-primary`. Grounds:
`--ground-neutral` `--ground-dark` `--ground-dark-glow`.
**Text-colour rule:** dark `--pp-ink` text on every coloured/peach/peri/khaki/grey
ground; **white (`--text-on-dark`) ONLY on the dark `--pp-ink` ground.**

**Type:** `--font-display` (Montserrat — all display + body) and `--font-mono`
(JetBrains Mono — the `[ LOGO ]` box, tickets, technical labels only). Weights
`--fw-display` 800 / `--fw-heading` 700 / `--fw-body` 500 / `--fw-body-strong` 600.
Scale (authored at 1920×1080) `--fs-display` … `--fs-stat-xl` … `--fs-h1`…`--fs-h3`
`--fs-lead` `--fs-body` `--fs-small` `--fs-eyebrow` `--fs-kicker` `--fs-logo`.
Tracking `--tracking-display` `--tracking-eyebrow` `--tracking-kicker`. Never set
title/body type at an angle.

**Paper art (the only illustration system):** 8 cut-out shapes ship as data-URI
custom properties — `--pp-form-flower` `--pp-form-pebble` `--pp-form-pebble-2`
`--pp-form-splatter` `--pp-form-torn-rect` `--pp-form-torn-rect-lg`
`--pp-form-ticket` `--pp-form-loop`. Use them **oversized, bleeding off the slide
edges**, as a `background-image` (or as a positioned `<img>` via the same files in
`forms/`); put the title/number **framed inside** the shape with margin. No
gradients (except `--ground-dark-glow`), no drop-shadows on cards (the paper shapes
carry the depth), no emoji, no hand-drawn SVG.

### Where the truth lives
Read `styles.css` and its imports — `tokens/colors.css`, `tokens/typography.css`,
`tokens/fonts.css`, `tokens/forms.css` — for the exact token set, and the
`components/<Colors|Type|Brand|Slides>/*/` cards for the layout archetypes (cover,
chapter divider, content, key-fact, and the colour/type/brand specimens). Each
card's `.html` is copy-ready markup; its `.prompt.md` explains when to use it.

### One idiomatic build (a cover slide)
```html
<section style="background:var(--pp-chartreuse);color:var(--pp-ink);
  font-family:var(--font-display);position:relative;overflow:hidden;padding:66px 80px">
  <span style="background:var(--pp-ink);color:var(--pp-chartreuse);padding:6px 14px;
    font-weight:var(--fw-heading);letter-spacing:var(--tracking-eyebrow);
    text-transform:uppercase">Section · Subject · Category</span>
  <h1 style="font-weight:var(--fw-display);font-size:94px;line-height:.95;
    letter-spacing:var(--tracking-display)">Presentation<br>title here</h1>
  <span style="font-family:var(--font-mono)">[ LOGO ]</span>
</section>
```

---

# paper-pieces 1.0.0

Paper Pieces design system — CSS tokens, paper-cut-out art, and 12 reference patterns. `window.PaperPieces` is intentionally empty (no importable components); style with the tokens in `styles.css` and copy the patterns below.

## Reference patterns

### Colors
- **CoreNeutrals** — Core neutral swatches — ink, paper, line, muted (no pure white).
- **Accents** — Accent colours — chartreuse, khaki, periwinkle, peach.
- **Grounds** — Slide grounds — one or two per deck; vary section grounds for rhythm.

### Type
- **Display** — Display type — Montserrat 800 for titles and big numbers.
- **HeadingsBody** — Headings & body — Montserrat 700/600/500.
- **EyebrowMono** — Eyebrows + JetBrains Mono technical labels.

### Brand
- **BrandDevices** — Brand devices — kicker chip, mono logo box, chartreuse highlight mark.
- **PaperForms** — Paper cut-outs — the only illustration system (forms/ + --pp-form-* tokens).

### Slides
- **Cover** — Cover slide — accent ground, kicker chip, big display title, mono ticket.
- **ContentCards** — Content slide — eyebrow, heading, supporting cards.
- **ChapterDivider** — Chapter divider — oversized blob bleeding off-edge, title framed inside.
- **KeyFact** — Key fact — one giant figure centred on a peach pebble.
