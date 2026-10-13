# PokeAPI data archive

This repository is an archive of [PokeAPI](https://pokeapi.co)'s raw data, forked from
[PokeAPI/api-data](https://github.com/PokeAPI/api-data). Every file under `data/api/v2/` is the
JSON PokeAPI serves for that endpoint, unchanged.

[HoopaDex](https://willhoop.github.io/hoopadex/app/) reads pokeapi.co first. If a request to
pokeapi.co fails, the same request is answered from this archive instead. When pokeapi.co is
working, this archive is not used.

## How it is kept current

`.github/workflows/archive-sync.yml` runs every Monday. It copies every file PokeAPI has added or
changed since the last run, and it **never removes a file**, even when PokeAPI does. It is never
force-pushed, so every earlier version of every file stays in the git history. A run that would
remove anything stops instead.

Do not use GitHub's **Sync fork** button on this repository. It would merge PokeAPI's deletions.

## Changes from the fork

- Added `ARCHIVE.md` (this file) and `.github/workflows/archive-sync.yml`.
- Moved PokeAPI's two server-update workflows (`update-gql-v1beta-data.yml`,
  `update-gql-v1beta2-data.yml`) to `.github/workflows-upstream-disabled/`. They deploy to
  PokeAPI's own servers with PokeAPI's credentials, and do nothing useful in an archive. They are
  moved, not deleted.

The data is PokeAPI's, under its BSD 3-Clause licence (`LICENSE.txt`).
