# Carried Patches — thisisbramiller/terraform-provider-unifi `patches` branch

Base: upstream `ubiquiti-community/terraform-provider-unifi` @ `f5d6a42f` (2026-03-13).
Patches are a linear series on top, ordered most-likely-to-merge-first so they
fall out as empty on rebase when upstream lands them. Each commit carries DEP-3
trailers (`Forwarded:`/`Origin:`/`Applied-Upstream:`). Off-ramp: when a patch's PR
merges AND releases upstream, drop it on the next rebase + `terraform init -upgrade`.

| # | Patch (commit subject) | Upstream PR | Status | Retires when |
|---|---|---|---|---|
| 1 | fix: reconcile unifi_client state after create (incl. review fixup) | [#139](https://github.com/ubiquiti-community/terraform-provider-unifi/pull/139) | open-PR | #139 merges + releases |
| 2 | fix(client): zero-diff for blocked/groups/qos_rate | [#174](https://github.com/ubiquiti-community/terraform-provider-unifi/pull/174) | open-PR | #174 merges + releases |
| 3 | fix(logging): per-subsystem masking (concurrent-map race) | [#168](https://github.com/ubiquiti-community/terraform-provider-unifi/pull/168) | ported-from-PR | #168 merges + releases |
| 4 | feat(provider): clarify controller-connection error | — | local-only (`Forwarded: no`) | submit upstream or carry indefinitely |

## Rebuild / rebase
- Build + install + lock: `FusionCloudX Infrastructure/scripts/build-unifi-provider.sh`.
- Bump upstream base: `git rebase --onto <new-upstream-sha> f5d6a42f patches`, re-run the deps gate, bump the synthetic version (`fcx2`…), rebuild, re-lock.

## Exit
Migrate to `filipowm/terraform-provider-unifi` (registry-published, framework rewrite) when this ledger is near-empty AND a v1.0.0 state migration is budgeted (NOT a drop-in).
