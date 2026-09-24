# hugolify-theme-uncinqify

Un Cinq branding for Hugolify: the theme module every Un Cinq site imports on top of the core theme.

## Install

Edit `config/_default/module.yaml`.

### V2

This module carries both styling layers, so it works with either design module. Declare it **before** the core theme and the styling module: its mounts have to shadow theirs.

```yml
imports:
  - path: github.com/sebousan/hugolify-theme-uncinqify/v2

  # Core theme
  - path: github.com/hugolify/hugolify-theme/v2

  # Styling — one of the two
  - path: github.com/hugolify/hugolify-theme-design-system # CSS + design tokens
  # - path: github.com/hugolify/hugolify-theme-bootstrap   # SASS + Bootstrap 5
```

With **hugolify-theme-design-system** the branding comes from `assets/css/` and `assets/tokens/`; with **hugolify-theme-bootstrap** it comes from `assets/sass/`, unchanged since v1.

### V1

```yml
imports:
  - path: github.com/sebousan/hugolify-theme-uncinqify
  - path: github.com/hugolify/hugolify-theme
```

## Documentation

- [Hugolify documentation](https://www.hugolify.io/docs/)
- [Migration from v1 to v2](https://www.hugolify.io/docs/getting-started/migration/) — what changes in a project moving to the v2 stack
- [Design modules](https://www.hugolify.io/docs/customization/design/) — design system and Bootstrap compared
- [Un Cinq design system](https://socle.uncinq.dev/docs/) — the token and CSS packages the design system builds on

## Design tokens

The design-system branding is authored as [DTCG](https://www.designtokens.org/) token files under `assets/tokens/theme/` and compiled to custom properties with [Style Dictionary](https://styledictionary.com/):

```bash
npm install
npm run build
```

This writes `assets/css/tokens/theme/**.css` plus the `assets/css/tokens/theme.css` barrel, both committed — Hugo reads the generated CSS, never the JSON. Run it after touching any token file.

Hand-written CSS lives in `assets/css/theme/` and is imported by `assets/css/theme.css`. Values that are design decisions belong in a token file, not in the CSS.

## Releasing

Tags are `v`-prefixed (`v2.0.0`): a `/v2` module path is only resolvable from a `v2.x.y` semver tag.

```bash
npx release-it
```

## Licensing

Hugolify is free for personal or commercial projects (MIT license)
