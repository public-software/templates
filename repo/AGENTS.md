# AGENTS.md — {{REPO}}

<!-- agents:generated — rendered by `{{CLI}} new` and the bootstrap kit from the catalog entry, config/org.env and RFC-0001; do not edit by hand, `{{CLI}} check` fails when it drifts -->
This is `{{REPO}}`, one repository of [{{ORG_DISPLAY_NAME}}]({{ORG_URL}}): a spec-first cleanroom Rust suite built by people and coding agents together. Read this file before the README; it is the contract every agent works under here.

**Ring:** {{RING}} · **Layers:** {{LAYERS}} · **Wave:** {{WAVE}} · {{PURPOSE}} Planned components: {{CONTENTS}}.

## Build and test

- Rust {{MSRV}} or newer, edition {{EDITION}}, licence `{{LICENSE_SPDX}}`. One Cargo workspace; every crate lives under `crates/`.
- What CI runs, so run it before a pull request: `cargo nextest run --workspace --all-features` (or `cargo test --workspace --all-features`), `cargo clippy --workspace --all-targets -- -D warnings`, `RUSTDOCFLAGS=-Dwarnings cargo doc --workspace --no-deps`, `cargo fmt --all --check`.
- `{{CLI}} check` — the organization's conventions (layout, crate names, provenance, the commit trailer). Install: `cargo install --git https://github.com/{{ORG}}/{{CLI}} {{CLI}}-cli`.
- A new crate is `{{CLI}} new <kind> <name>` with a kind from lib, app, service, plugin, spec; it lands in `crates/{{CRATE_PREFIX}}-{{REPO}}-<name>/` and gets a `[[component]]` entry in `CATALOG.toml`.

## Conventions

- Crates are named `{{CRATE_PREFIX}}-{{REPO}}-<name>`; a service is the binary `{{DAEMON_PREFIX}}-<name>`; WIT interfaces live under `{{WIT_NAMESPACE}}:`.
- `#![forbid(unsafe_code)]` unless the crate's README says why not; `unsafe` is reviewed by `{{ORG}}/core` and runs under Miri in CI.
- Every public item is documented (`missing_docs` warns and rustdoc runs with `-Dwarnings`). No new dependency without an audit `cargo vet` accepts.
- Provenance: everything consulted (specifications, conformance suites, documentation, permissively licensed references) is listed in `PROVENANCE.md`; never read, and never point a prompt at, copyleft source of the module you touch (the two-team rule, Charter §09).
- Prose: write every public document (README, docs/, crate documentation, release notes) in Simplified Technical English (ASD-STE100). The rules and the names of the suite are in [WRITING.md](https://github.com/{{ORG}}/.github/blob/main/WRITING.md). Short sentences, one topic each, active voice, one word for one thing.

## Commits and pull requests (RFC-0001)

- Every commit an assistant helped write ends with `Assisted-by: <tool>:<model>`, one line per tool (for example `Assisted-by: claude-code:claude-fable-5-1`). Never add `Signed-off-by:` yourself and never `Co-authored-by:` for yourself: the human you work for signs off.
- A pull request carries a test that fails without the change and passes with it, the `PROVENANCE.md` entries, the trailer on every assisted commit, a conventional-commit title (squash merges use it), and a body with the sections What, Why and How this is verified that another agent can act on without reading the diff.
- The merge gates decide (`{{CLI}} check`, CI, the agent review `suite / policy`, the maintainer team `{{ORG}}/{{MAINT_TEAM}}`), not who or what wrote the change.
<!-- agents:end -->

## Repo notes

_Maintainers of `{{REPO}}` write here what the generated section cannot know: how the crates fit together, how to run the thing, which specifications matter, what not to touch. Everything above this heading is regenerated._
