# bb-plugin-flexoki — Standalone Context

BB theme plugin that ports Steph Ango's Flexoki palette: UI palettes in
`themes/flexoki.css`, code themes `themes/flexoki-{light,dark}.json`.

## Critical Rules

1. **Check both palettes.** Every CSS change is verified with a screenshot in
   light and dark, because each palette sets its own composer and accent
   variables.
2. **Keep the Flexoki values.** Colours come from the Flexoki base and accent
   scales; a new colour must be one of them, with its Flexoki name in a comment,
   so the port stays faithful to upstream.
3. **Screenshots are public.** `screenshots/` ships in the package and in the
   BB marketplace: before committing, replace real thread, project and host
   names in the captured UI with neutral ones.
4. **Other plugins can restyle the UI.** When a colour looks wrong live, check
   `bb plugin list` first: a third-party plugin (for example a chat restyler)
   may override the theme's selectors.

## Commands

- Check: `npm ci && npm run typecheck && npm run build`.
- Live test from the checkout: `bb plugin install "$PWD"` and
  `bb theme set plugin:flexoki:flexoki`.

## Repository and release contract

- Ownership: personal, public (`ponomr/bb-plugin-flexoki`), MIT.
- Checks: the command above; there is no CI yet.
- Release: bump `version` in `package.json` and `package-lock.json` in the PR,
  merge it, then tag the merge commit `vX.Y.Z` and push the tag.
- Distribution: the BB marketplace entry (`entries/flexoki.json` in
  get-bb/marketplace) tracks the git source with range `^0.1.0`, so a `0.1.x`
  tag reaches users without a marketplace PR. A marketplace PR is needed for a
  `0.2.0` range change or new screenshots, description or icon.
- Verification: `bb plugin install "git:https://github.com/ponomr/bb-plugin-flexoki.git@^0.1.0" --yes`,
  then `bb plugin source flexoki` must show the new tag.
- Recovery: reinstall the previous tag with `@X.Y.Z`; no persistent data.
