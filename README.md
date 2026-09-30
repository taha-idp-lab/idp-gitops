# idp-gitops

Desired state of the Kubernetes cluster for the [Internal Developer Platform](https://github.com/taha-idp-lab/idp-platform).

🚧 **Status:** work in progress.

## How it works

- **ArgoCD** watches this repo (GitOps: Git is the source of truth).
- An **ApplicationSet** with a Git directory generator turns every `apps/<service>/` folder into an ArgoCD Application — no manual setup per service.
- New services are added **automatically** by a Backstage template, through a pull request.

## Structure

```
bootstrap/                  # ArgoCD ApplicationSet definitions
apps/
  <service>/
    values-dev.yaml         # Helm values per environment
    values-staging.yaml
```

The Helm chart itself lives in each service repo; this repo only holds environment-specific values.
