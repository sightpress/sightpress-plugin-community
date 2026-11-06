# SightPress community helper

`sightpress/plugin-community-helper`: the official SightPress plugin for comments,
likes, share links and saved pages. Licensed GPL-2.0-or-later.

> **Status:** M0 scaffolding in place (manifest, bundle, quality gates, CI);
> features arrive in milestone M11.

It attaches to any content type through the core's `content.after_body` slot,
so it works on pages, articles or any other type a site has enabled — there is
no separate commenting or sharing plugin. It adds:

- **Threaded comments**, members-only, public or private (site staff only), with
  a moderation queue and notifications raised through `NotifierPort`.
- A **like button** with `aria-pressed` state and cached counts.
- **Server-rendered share links**, per-network Open Graph extras and the Web
  Share API where supported, with no third-party scripts or tracking.
- A **save button** and a "Saved pages" section in the member's account.

Comments, likes and saving all need a member account; none needs a CAPTCHA or
other cognitive test. Once a site turns the plugin on, comments and likes
default to on and share links and saved pages default to off; site admins
switch each feature independently, and a feature that's off renders nothing and
its routes 404.

## Development

```bash
composer install
vendor/bin/phpunit          # on PluginTestCase, enabled and disabled
vendor/bin/phpstan analyse
npx playwright test         # every manifest route, with axe-core
```

Check out `sightpress/core` as a sibling and require it with
`COMPOSER=composer.dev.json composer install` to run the test kernel.
