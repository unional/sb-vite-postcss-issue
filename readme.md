# Storybook + Vite + PostCSS issue

## Reproduction steps

```sh
pnpm install

cd packages/pkg-b
pnpm storybook
```

Check the loaded `.../packages/pkg-b/tailwind.css` in the dev tool.

You will see the CSS contains:

```css
/* from pkg-a */
.p-0 {
  padding:0px
}

/* ... */

/* from this package */
.p-0 {
  padding:0px
}
```

Showing that while `postcss-import` is applied,
`postcss-discard-duplicates` is not.
