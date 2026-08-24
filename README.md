# kg13.manager

Internal, members-only management app for KG13 — replaces our old Google Sheet as the source of truth for locations, people, gear, fixed event dates, and merch.

## What it does

- **Map** — real OpenStreetMap view of our sites, with pins showing gear counts and flagged items at a glance
- **Locations** — venues/spaces we use, with capacity, notes, and a sensitivity flag for anything that shouldn't be widely visible
- **People** — crew and lineup contacts
- **Gear** — full equipment inventory, with a location-history log per item (know where something is *now*, and where it's been)
- **Dates** — our fixed annual dates (day/month, recurring every year)

## Access

Two roles, enforced at the database level (not just hidden in the UI):

- **Core Crew** — full access to everything, including sensitive locations and flagged gear
- **Member** — can view and manage gear/dates, but not locations or people; sensitive/flagged records are invisible to this role entirely

New sign-ups default to Member. A Core Crew member has to manually promote someone in the Supabase `profiles` table.

## Stack

- **Frontend**: single static `index.html` — vanilla JS, no build step, styled to match our visual identity
- **Backend**: [Supabase](https://supabase.com) — Postgres database, auth, and row-level security
- **Map**: Leaflet + OpenStreetMap tiles (no API key required)

## Running it

Just open `index.html` in a browser — it talks directly to our Supabase project's API. No server or build step needed.

## Status

Live and in use. Planned next: hosting at `kg13tlv.com`.
