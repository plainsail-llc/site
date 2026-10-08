# Plainsail LLC — Brand Guide

Reference for anything carrying the Plainsail name: the site, proposals and SOWs, invoices, decks,
one-pagers, email signatures, demo sites built for prospects.

**Source of truth:** the `:root` block in `index.html` (this repo). If a value changes there,
change it here in the same commit. Nothing else defines these colors — there is no design file.

A read-only mirror lives at `~/Vault/Research/Brand Guide.md` for the Obsidian KB; it carries its
own refresh command. Never edit the mirror.

---

## Color

### Palette

| Token | Hex | Role |
|---|---|---|
| `--sea` | `#175E73` | **Primary brand color.** Deep teal. Main sail in the mark, CTA buttons, link text. |
| `--sea-deep` | `#0F4557` | Pressed/hover state for anything `--sea`. Also safe for small text on light backgrounds. |
| `--gold` | `#B8891F` | Accent only. Second sail, eyebrow labels, card numerals, focus rings. Never a background for body text. |
| `--ink` | `#14303E` | Body text, hull in the mark, dark section backgrounds. |
| `--muted` | `#56707C` | Secondary text — ledes, kickers, card body. |
| `--paper` | `#FAF8F3` | Page background. Warm off-white, not pure white. |
| `--sail` | `#FFFFFF` | Card and surface fill, and text on dark backgrounds. |
| `--line` | `#E4DFD2` | Borders, rules, the horizon line. |

Two more hexes appear only inside the dark "principles" section and are not general tokens:
`#E9E4D8` (body text on `--ink`) and `#A9B8BF` (kicker on `--ink`).

### The one-color answer

If someone asks for *the* brand color — a single swatch for a vendor form, a Slack workspace, a
LinkedIn header — it is **`#175E73`**. RGB `23, 94, 115`. Naive CMYK `80 / 18 / 0 / 55` —
send the hex to the printer and let them convert for the actual stock; do not hand off these
numbers as final. Closest common Pantone is in the PMS 315 / 3155 range, but match a physical
chip before paying for a run.

Gold is the accent, not a co-equal. Roughly a 9:1 ratio of teal to gold by area; gold should read
as punctuation.

### Ratios that matter (WCAG 2.1)

| Foreground | Background | Ratio | Verdict |
|---|---|---|---|
| `--ink` | `--paper` | 13.0 | AAA |
| `--sea` | `--paper` | 6.86 | AA |
| `--sea` | `--sail` | 7.28 | AAA |
| `--sea-deep` | `--paper` | 9.85 | AAA |
| `--muted` | `--paper` | 4.94 | AA (body text only — do not go smaller than 16px) |
| `--sail` | `--sea` | 7.28 | AAA (white on teal buttons is safe) |
| `--gold` | `--sail` | 3.16 | Large text only (>=18.66px, or >=14px bold) |
| `--gold` | `--paper` | **2.98** | **Fails everything** |
| `--gold` | `--ink` | 4.36 | Large text only |

**Known issue:** the site's `.eyebrow` class puts `--gold` on `--paper` at 0.72rem bold — about
12px, at 2.98:1. That misses even the large-text floor. It is decorative and short, but it is a
real defect. Where gold has to carry small text on a light background, use **`#916C18`** instead
(4.54 on paper, 4.81 on white, same hue). For gold on `--ink`, **`#BC8C20`** reaches 4.54.

Do not invent new tints. If a design needs a step between two tokens, add it here first.

---

## Typography

- **Headings, wordmark:** `"Iowan Old Style", Charter, "Palatino Linotype", Palatino, Georgia, serif`
  at weight 600, line-height 1.15, `text-wrap: balance`.
- **Body, UI:** the system sans stack —
  `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`
  at 17px / 1.65.
- **Eyebrow labels:** uppercase, `letter-spacing: 0.18em`, 0.72rem, weight 700, gold.
- **Wordmark tracking:** `0.02em`. **Card numerals:** serif, weight 700, `0.08em`.

No webfonts are loaded and none should be — the stack degrades to Georgia everywhere and the page
stays a single request. In Google Docs or Word, substitute **Palatino** (headings) and the
document default sans (body). In Canva or a deck tool, **Palatino** or **Charter**; if neither is
available, Georgia.

---

## Mark

Three shapes on a 32x32 grid: a large teal sail, a smaller gold sail behind it to the right, and
an ink hull beneath both. No enclosing shape, no gradient, no outline.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <path d="M17 3v20H6z"        fill="#175E73"/>
  <path d="M19 8v15h8z"        fill="#B8891F"/>
  <path d="M3 26h26l-2.5 3H5.5z" fill="#14303E"/>
</svg>
```

That exact markup is both the favicon (inline data URI in `index.html`) and the header wordmark.

**Lockup:** mark at 26px beside "Plainsail" in the serif stack at 1.35rem, `--ink`, with a 0.6rem
gap. The wordmark is set in sentence case — "Plainsail", never "PLAINSAIL" or "plainsail". Legal
name "Plainsail LLC" is for contracts, invoices, and the site eyebrow; elsewhere just "Plainsail".

**Clear space:** at least the height of the hull on every side. **Minimum size:** 20px for the mark
alone, 24px when locked up with the word.

**Don't:** recolor the sails, flip or rotate the mark, add a drop shadow, place it on a busy photo,
or set it in a circle badge.

---

## Voice, as it shows up in layout

The site's own copy is the reference: "AI that earns its keep." Short sentences, no exclamation
marks, no stock photography of people pointing at laptops. Generous whitespace (sections at
4.5rem vertical padding), a 68rem max width, one idea per card. The thin `--line` horizon rule
with two tiny sails is the only ornament in the system — use it as a section break, sparingly.

Buttons: 4px radius. Cards: 6px radius, 1px `--line` border, `--sail` fill on `--paper` ground.
Focus rings: 3px `--gold`, 2px offset — keep them, they are the accessibility story.

---

## Applying it elsewhere

- **Proposals / SOWs (Better Proposals, DocuSeal, PandaDoc):** `--sea` for headers and accept
  buttons, `--ink` for body, `--paper` page ground, gold for section numerals only.
- **Invoices:** ink text on white, a single `--sea` rule under the header. No gold.
- **Email signature:** plain text or minimal HTML — name in `--ink`, "Plainsail LLC" and the
  plainsail.co link in `--sea`. No image logo (it trips spam filters and breaks in dark mode).
- **Demo sites built for prospects:** these carry the *prospect's* brand, not Plainsail's. The page
  above the fold is theirs entirely — palette, type, voice — and nothing of Plainsail's appears in it.
  **Carve-out, added 2026-08-26:** the Alexandria campaign demos end with a full-width closing note
  in Plainsail's own dark-context palette (`--ink` ground, `#E9E4D8` body, `#BC8C20` gold), set off by
  a 3px gold rule. It is not a credit line; it is the campaign's entire conversion mechanism, and it
  is deliberately built to read as a separate voice speaking *about* the page rather than as part of
  the business's site. The separation is the point — a small tasteful credit would have been read as
  the prospect's own footer. Everything above that rule still obeys the first sentence.
  Source of truth: `~/alexandria-redesigns/data/credit-block.json`.
- **Dark contexts:** `--ink` ground, `#E9E4D8` body, `--sail` headings, `#BC8C20` for gold accents.

---

*Last reviewed 2026-08-24. Palette extracted from `index.html` at commit 87478f9.*
