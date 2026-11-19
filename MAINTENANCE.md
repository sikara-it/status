# Maintenance (Sikara)

Status page https://status.sikara-it.com, Upptime (GitHub Actions + Issues + Pages).
Runs as the GitHub App `sikara-status-page` (installed on this repository only; vars `GH_APP_ID`
= client ID, secret `GH_APP_PRIVATE_KEY`).

## Rules of the sikara-it organisation
- Third-party actions are allowed **by exact commit only** (infra `stacks/github/terraform.tfvars`):
  `upptime/uptime-monitor@74f0683…` (v1.46.5), `peaceiris/actions-gh-pages@84c30a8…` (v4.1.0),
  `benc-uk/workflow-dispatch@d004979…` (v1.3.3). A tag (`@v1.46.5`, `@master`) is refused.
- No automatic template updates: `update-template.yml` and `updates.yml` are deleted on purpose
  (they would pull and commit new workflow code from upstream).

## Changing the monitored sites
1. Edit `.upptimerc.yml` and push.
2. Run **Setup CI** by hand (Actions tab). It regenerates every workflow with version tags.
3. Re-pin: replace each `uses: <action>@<tag>` with the commit SHAs above (+ `actions/*` SHAs as in
   the current files), delete `update-template.yml` and `updates.yml`, keep `setup.yml` manual-only.
4. Upgrading Upptime = new SHAs here AND in the infra allowlist (PR), on purpose.
