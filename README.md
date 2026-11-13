# Middlesex County Maker Fest — Organizer CRM

Separate organizer-only CRM for the [public stakeholder map](https://racerblur.github.io/middlesex-maker-fest/). Both use the same Supabase project; no contact data is stored in this repository.

## Current features

- Email/password organizer sign-in with an allowlist lookup in `public.organizers`
- Searchable directory of stakeholder records
- Private CRM profiles: email, phone, role, referrals, interest, priority, relationship and participation status, next action and follow-up dates
- Private activity history: emails, calls, meetings and notes

## Privacy

GitHub Pages serves the **application code publicly**, even though CRM records require authorization. Supabase row-level security is the actual access control: `crm_profiles` and `crm_activities` are organizer-only. The app never embeds service-role keys. Do not place confidential information in `people` or `relationships` unless those fields are protected by database policy. Public stakeholder visibility is separately controlled with `people.public_approved`.

## Deploy

1. Open this repository's **Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**, branch **main**, folder **/(root)**, then **Save**.
3. Wait for GitHub Pages to finish publishing, then visit https://racerblur.github.io/maker-fest-crm/.
4. Sign in with an existing Supabase Auth user who has an `admin` or `editor` record in `public.organizers`.

Do not create a new organizer record without verifying the correct authenticated user ID. The published URL is reachable by anyone, but the CRM interface and private tables require organizer authorization.

## Testing still required

- Verify GitHub Pages deployment completes.
- Verify approved organizer login, directory count, profile save/reload and activity creation.
- Verify an anonymous visitor and a signed-in non-organizer cannot read private CRM tables.
- Confirm mobile layout and accessibility.

The original public stakeholder app is not modified by changes in this repository.
