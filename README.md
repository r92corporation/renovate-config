# renovate-config

The shared Renovate preset for every R92 repo (plan 0.9, R92-10). A repo opts in with a `renovate.json`:

```json
{
  "extends": ["github>r92corporation/renovate-config"]
}
```

`default.json` encodes skill `r92-dependencies`: latest stable at least 3 days old, security fixes at once and
to the newest safe release, exact pins, images by digest, GitHub Actions by SHA, minor and patch grouped per
ecosystem, weekly lockfile maintenance, Node LTS only, Workers `compatibility_date` kept under 180 days, theme
tarballs left to theme releases, never automerged. Every PR body carries the evidence table and the scan step.

The bot runs weekly on nexus-prod-01 as the GitHub App `r92-renovate` (r92-server-ops, component `renovate`,
runbook `docs/runbooks/renovate.md`). Validate a change with
`npx --yes --package renovate@44.186.8 renovate-config-validator --strict --no-global default.json`
(the version the runner image pins).
