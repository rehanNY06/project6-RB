# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end -->

## Comment 1 — Rename
**What I did:** Renamed `save_to_watchlist()` to `add_to_watchlist()` in `services/watchlist_service.py` to match the verb_to_noun naming convention used by `add_to_collection()` in the collection service. Updated the import and call site in `routes/watchlist/watchlist.py` accordingly.
**How I verified:** Searched the project for any remaining references to `save_to_watchlist` (found none) and ran the full test suite to confirm nothing broke.

## Comment 2 — Deduplication
**What I did:** Added a check in `add_to_watchlist()` that queries for an existing `WatchlistEntry` matching the given `user_id` and `film_id` before creating a new one. If a match is found, it raises a new `AlreadyInWatchlistError` exception, mirroring the `AlreadyInCollectionError` pattern used in `add_to_collection()`.
**How I verified:** Manually tested via the running Flask server — POSTed the same film to a user's watchlist twice. The first request succeeded and created the entry (201 response). The second request correctly raised `AlreadyInWatchlistError`, confirming the duplicate was caught before a second row was created.

## Comment 3 — Missing test
**What I did:**
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end -->