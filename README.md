# LostKeys

[![Deploy](https://github.com/tzer0m/LostKeys/actions/workflows/deploy.yml/badge.svg)](https://github.com/tzer0m/LostKeys/actions/workflows/deploy.yml)

Help keys get back to their owners. A tiny landing page for a keyring tag: if someone finds a lost keyring with an NFC tag linking to this site's URL and a phone number in the query string, they land on a page with a tap-to-call link.

## Purpose

- `GET /?number=<digits>` displays "Call: +\<formatted number>" as a `tel:` link.
- `GET /` with no number shown just displays the site name and tagline.

That's the entire feature set — one Razor Page, one query parameter, no database, no auth.

## Tech stack

- ASP.NET Core Razor Pages on .NET 8

## Deployment

Deployed via GitHub Actions on push to `master`, using a self-hosted runner on Tyrion. The workflow stops the `LostKeys.service` systemd unit, publishes a fresh build to `/home/tzer0m/Services/LostKeys`, and restarts the service.
