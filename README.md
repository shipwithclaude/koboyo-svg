# Koboyo SVG

A large, hand-organized library of **261,737 monochrome SVG illustrations and icons**, grouped into five top-level collections and more than 120 topic folders. Every file is a self-contained SVG that inherits its color from CSS (`fill="currentColor"`), ships with an `aria-label`, and needs no external fonts, scripts, or raster assets.

## Collections

| Folder | Files | Contents |
|--------|------:|----------|
| `face/` | 2,756 | Facial expressions and portraits: emotions, ages, hairstyles, accessories |
| `mark/` | 23,343 | UI icons, symbols, math notation, status markers, solid glyphs, textures |
| `object/` | 151,489 | Objects and concepts across 80 topics: animals, food, vehicles, tech, science, business, and more |
| `people/` | 79,886 | People in context: poses, gestures, professions, sports, groups, workplace scenes |
| `scene/` | 4,263 | Composed vignettes and UI empty/success/error states |

Each collection is split into topic folders, for example `object/animal`, `object/logistics`, `people/profession`, `mark/math`, `scene/uistate`.

## Styles

Many subjects are available in several rendering styles. The style is encoded as a filename prefix:

| Prefix | Style |
|--------|-------|
| *(none)* | Clean line and fill illustration, the default look |
| `cartoon-` | Rounded, playful cartoon strokes |
| `inkbrush-` | Loose brush and ink texture |
| `blockprint-` | Bold woodcut / linocut look |

Example: `face/face/laughing-face.svg`, `face/face/cartoon-laughing-face.svg`, `face/face/inkbrush-laughing-face.svg`.

A numeric suffix such as `-2` marks an alternate take on the same subject.

## Usage

### Inline in HTML

```html
<span style="color: #1f6feb; width: 48px; display: inline-block;">
  <!-- paste the contents of object/animal/air-stone.svg here -->
</span>
```

Because every path uses `currentColor`, the icon takes whatever `color` the parent element has.

### As an image

```html
<img src="mark/icon/account-deletion-request-drawn.svg" alt="Account deletion request" width="32" height="32">
```

### In React

```jsx
import { ReactComponent as Laugh } from './face/face/cartoon-laughing-face.svg';

<Laugh style={{ width: 40, color: 'tomato' }} />
```

### In CSS as a mask

```css
.icon {
  width: 24px;
  height: 24px;
  background: currentColor;
  mask: url("mark/icon/account-deletion-request-drawn.svg") no-repeat center / contain;
}
```

## File conventions

- One `<svg>` root per file with an explicit `viewBox`, no fixed `width` / `height`.
- `fill="currentColor"` on the root so color is controlled by CSS.
- Descriptive `aria-label` on the root for accessibility.
- Kebab-case filenames that describe the subject, for example `person-beard-smiling-warmly.svg`.
- No embedded raster images, fonts, or scripts.

## Finding things

The folder tree is the index. A quick way to search by subject from the command line:

```bash
# every inkbrush-style illustration of a bicycle
find . -name 'inkbrush-*bicycle*.svg'

# everything in the logistics topic
ls object/logistics
```

## Repository size

The library is about 1.9 GB uncompressed. To fetch only one collection, use a sparse checkout:

```bash
git clone --filter=blob:none --sparse https://github.com/shipwithclaude/koboyo-svg.git
cd koboyo-svg
git sparse-checkout set mark face
```

## License

No license has been declared for this repository yet. Contact the repository owner before redistributing the assets.
