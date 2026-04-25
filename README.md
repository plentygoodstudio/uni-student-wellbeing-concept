# Uni Student Wellbeing — 7-page Concept Redesign

A full concept redesign for [unistudentwellbeing.edu.au](https://unistudentwellbeing.edu.au/). No frameworks. Raw HTML, CSS, and ~20 lines of vanilla JS.

## File structure

```
/
├── index.html                  Hub homepage
├── research-project.html       USW Research Project
├── research-hub.html           USW Research Hub
├── learning.html               Learning modules catalogue
├── module-1.html               Module 1: Student Wellbeing (template)
├── about.html                  Program, team, funding
├── contact.html                Contact
├── styles/
│   ├── tokens.css              All design tokens (palette, type, spacing, motion)
│   ├── base.css                Reset, typography utilities, layout primitives
│   └── components.css          Every component — no raw hex values
├── assets/symbols/             5 custom SVG symbols (64×64, stroke-based)
├── scripts/
│   └── nav.js                  Mobile nav toggle + footer year
└── README.md
```

---

## Design direction

Modern education product — reference: Google Classroom, Coursera, Brilliant.org. Inter only (no serif). Pill buttons. Pronounced rounded corners (`--radius-xl: 28px`). Tinted surface colour instead of shadows. Card lift on hover (2px `translateY`). Motion serves feedback, not entertainment.

---

## Placeholder content (flag for production)

The following are illustrative placeholders and must be replaced with real content before any production use:

| Item | Location | Note |
|---|---|---|
| Events (3 upcoming) | `research-hub.html` | Dates and titles are invented |
| Past events list | `research-hub.html` | Titles are plausible but unverified |
| News items (4) | `research-hub.html` | Illustrative only |
| Publications (3) | `research-project.html` | Authors and titles are placeholder |
| Research questions (4) | `research-project.html` | Inferred from project scope — verify against ARC grant |
| Module reading times | `learning.html`, `module-1.html` | Estimated at ~16 min/lesson; measure against real content |
| ARC grant number | `research-project.html` | DP230100432 — verify |
| Latest update card | `index.html` | Illustrative |
| Hero stats: "20+ universities", "10 yrs research" | `learning.html` | Plausible figures based on project history; verify before launch |
| Project admin email `usw-admin@unimelb.edu.au` | `contact.html` | Placeholder — replace with the real shared mailbox |
| FAQ answers (6 items) | `contact.html` | Drafted from likely positions; review with the team before launch |
| Researcher cards: Sarah Mitchell, Wei Chen, Tom Bradley, Priya Sharma | `about.html` | Placeholder names + roles — replace with real team members |
| Institutional partners: University of Sydney, Monash University | `about.html` | Placeholder — confirm partnership status |
| Events 4 & 5: 12 Sep, 8 Oct | `research-hub.html` | Placeholder dates and titles |
| Hub stats: 24 events, 1,400+ practitioners, 12 universities, 8 collaborations | `research-hub.html` | Placeholder figures — replace with real Hub metrics |
| News items 5 & 6 (Aug 2024 partner network, Jul 2024 belonging milestone) | `research-hub.html` | Placeholder copy |

### How to replace placeholders

When real content arrives:
1. Find the row above and the file path it points to.
2. Replace the placeholder copy/figure in place — markup is already structured for the final shape.
3. Delete the README row once the placeholder is replaced. Anything still in this table is still placeholder.

---

## Typography

Inter variable font only. Loaded via Google Fonts `@import` in `base.css` with `display=swap`. The type scale uses the full optical size range (`opsz 14..32`).

Type classes (`.text-display-lg`, `.text-headline-md`, etc.) are utility classes defined in `base.css`. Apply them directly in HTML rather than styling headings globally — gives fine control without specificity fights.

## Palette

New palette introduced in this version. Notable decisions:

- **`--color-bg-tinted` (#E8F3F1)** used as hero blob, featured module bg, and date chips — keeps the primary teal in the palette without using it as a text background.
- **`--color-accent` (#FFB020)** only appears as: badge backgrounds (`.chip-accent`, `.event-card--paid`), the ARC funding highlight box on `about.html`, and the question number circles. Never as text on a light bg — contrast would fail WCAG.
- **`--color-surface-dark` (#0B1F1E)** used for footer and subscribe CTA block. Provides visual terminus without a border.
- **Module tints** (`--color-module-1` through `--color-module-5`) cycle teal → amber → lavender → purple → green across the 5 module cards on `learning.html`. Cohesive but not monotonous.

## SVG symbols

Five 64×64 symbols in `assets/symbols/`. All stroke-based, `stroke-width="2"`, `stroke-linecap="round"`. They use `currentColor` so they inherit the text colour of their parent container. Inlined in HTML via `<svg>` elements rather than `<img>` so `currentColor` resolves correctly.

| Symbol | Concept |
|---|---|
| `student-wellbeing.svg` | 4 overlapping circles at cardinal positions — a bloom radiating from centre |
| `curriculum-design.svg` | 3×3 dot grid with diagonal path — structure and design |
| `teaching-practice.svg` | Rounded speech bubble with forward arrow — delivery and guidance |
| `difficult-conversations.svg` | Venn diagram with node at intersection — meeting a student where they are |
| `your-wellbeing.svg` | Rounded square with compass cross — self-orientation |

## Module lesson counts

Counts are drawn from the original site navigation:

| Module | Lessons | Time |
|---|---|---|
| 1 · Student Wellbeing | 6 (incl. intro + quiz) | ~75 min |
| 2 · Curriculum Design | 6 (incl. intro) | ~70 min |
| 3 · Teaching Strategies | 6 (incl. intro) | ~70 min |
| 4 · Difficult Conversations | 5 (incl. intro) | ~60 min |
| 5 · Your Wellbeing | 5 (incl. intro) | ~55 min |

Total: 28 lessons, ~5.5 hours. Rounded to "~6 hours" in UI copy.

## Accessibility notes

- One `<h1>` per page.
- Skip-to-content link on every page.
- All SVG symbols marked `aria-hidden="true"` (decorative — text label carries meaning).
- Video placeholder has `role="img"` and `aria-label` describing the video.
- Avatar initials marked `aria-hidden="true"`.
- Focus styles use `outline: 2.5px solid --color-primary` with 3px offset.
- All accent-coloured text uses `--color-primary` or `--color-ink` on accent bg (never amber text on white — fails WCAG AA).

## Responsive breakpoints

- `≤ 1024px`: Project router stacks; module grid goes 1-col; team grid 2-col.
- `≤ 768px`: Mobile nav, event cards stack, news feed 1-col, footer 1-col.
- `≤ 600px`: Related modules 1-col; hero actions stack; cards reduce padding.

Content licensed under [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).

---

## Live preview

- **GitHub:** https://github.com/plentygoodstudio/uni-student-wellbeing-concept
- **Vercel (production):** https://uni-student-wellbeing.vercel.app
- Auto-deploys on push to main.
