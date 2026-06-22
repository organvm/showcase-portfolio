# Value Discovery — organvm/showcase-portfolio

**Date:** 2026-06-22
**Verdict:** REAL VALUE — promote to ranked tier (not archival).

## Value Thesis

`showcase-portfolio` is a **working, tested aggregation-and-rendering engine** (Python,
47 passing tests, functional `python -m src` CLI) that ingests a registry of creative
works — either the estate's own `registry-v2.json` (`collect_from_registry`) or a curated
`works.json` (`collect_from_works_file`) — and emits curated galleries in **Markdown, HTML,
and JSON**, plus summary statistics and keyword search across title/description/tags. The
elaborate TypeScript/React architecture described in the README is aspirational; the value
that actually ships today is the small, clean, dependency-light Python core (`gallery.py`
model, `collector.py` ingestion, `renderer.py` multi-format export). Its highest latent
value is as the **canonical presentation/aggregation layer for the entire ORGANVM estate**:
`collect_from_registry()` is already wired to read the estate repo registry and turn it into
a portfolio, so any organ can publish its works through one shared, machine-readable pipeline
instead of hand-maintaining repo lists. The differentiated product/revenue path — documented
in the README and corroborated by the `docs/source-materials/` trove (a real CV for Anthony
James Padavano, grant-submission lists, a Next.js "MET4" portfolio prototype) — is
**metadata → institutional-output generation**: turning a single structured `Work` record
into grant-application, residency, and academic-CV formats (Dublin Core, CV export). That is
the capability grant reviewers, residency committees, and curators actually pay attention to,
and it is the gap between what the README promises and what `src/` currently does.

## Highest-Value Capability (reusable across the estate)

The `registry-v2.json → Gallery → {markdown, html, json}` pipeline is a genuine cross-organ
capability: a single, tested way to render any organ's works into exhibition- and
API-ready surfaces. Promote it so build-out (the CV/grant exporter) can follow.

## Single Best First Task

**Implement a CV / grant-format exporter** — add a `src/exporters.py` module and a
`python -m src export --format {cv,grant,dublin-core}` CLI subcommand that generates an
academic-CV / grant-application / Dublin-Core document from the existing `Work`/`Gallery`
model, with tests. This is the one differentiated capability the README promises but the
code does not yet deliver, and the `docs/source-materials/` CV + grant-submission archive
provides ready ground-truth fixtures to build against. It converts the engine from
"renders a gallery" into "generates the institutional documents that win funding."

## Why Not Archival

The code runs, the tests pass, the engine ingests the estate's real registry format, and
there is a concrete, fundable product directly adjacent to what already works. This repo is
infrastructure with a clear build-out path, not a finished/dead artifact.
