# argocd-apps-of-apps

A Helm chart for managing Argo CD Projects, Applications, ApplicationSets, Clusters, Private CredentialsTemplates,PrivateGitRepositories,PublicHelmRepositories and PrivateHelmRepositories. Secrets managed by External Secrets Operator

To regenerate this document, from the root of this chart directory run:
```shell
docker run --rm --volume "$(pwd):/helm-docs" -u $(id -u) jnorwood/helm-docs:latest
```

## Prerequisites

- Helm v3.0.0+
- CRDs (Application and AppProject)
  - You need to install them via [argo-cd Helm chart](../argo-cd) or upstream.

## Installation

```console
$ helm repo add polarpoint https://polarpoint-io.github.io/polarpoint-helm
$ helm install my-release polarpoint/argocd-apps
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.defaultCluster | string | `"https://kubernetes.default.svc"` |  |
| global.namespace | string | `"cd"` |  |
| global.syncPolicy.automated.prune | bool | `false` |  |
| global.syncPolicy.automated.selfHeal | bool | `true` |  |
| privateGitRepositories[0].name | string | `"argocd-config"` |  |
| privateGitRepositories[0].url | string | `"git@github.com:polarpoint-io/argocd-app-of-apps.git"` |  |
| privateGitRepositories[1].name | string | `"argocd-tooling-applications"` |  |
| privateGitRepositories[1].url | string | `"git@github.com:polarpoint-io/argocd-tooling-applications.git"` |  |
| privateGitRepositories[2].name | string | `"argocd-foundational-applications"` |  |
| privateGitRepositories[2].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| privateGitRepositories[3].name | string | `"argo-workflows-library"` |  |
| privateGitRepositories[3].url | string | `"git@github.com:polarpoint-io/argow-template-library.git"` |  |
| projects[0].applications[0].name | string | `"argocd-config"` |  |
| projects[0].applications[0].path | string | `"./"` |  |
| projects[0].applications[0].targetRevision | string | `"main"` |  |
| projects[0].applications[0].url | string | `"git@github.com:polarpoint-io/argocd-app-of-apps.git"` |  |
| projects[0].applications[0].valuesFile | string | `"values.yaml"` |  |
| projects[0].destinations[0].name | string | `"default"` |  |
| projects[0].destinations[0].namespace | string | `"*"` |  |
| projects[0].destinations[0].server | string | `"https://kubernetes.default.svc"` |  |
| projects[0].name | string | `"argocd-config"` |  |
| projects[0].permissions.namespace | string | `"argocd"` |  |
| projects[0].permissions.ro.description | string | `"Read-Only Access"` |  |
| projects[0].permissions.ro.groups[0] | string | `"ARGOCD-CONFIG-RO"` |  |
| projects[0].permissions.rw.description | string | `"Read-Write Access"` |  |
| projects[0].permissions.rw.groups[0] | string | `"ARGOCD-CONFIG-RW"` |  |
| projects[0].urls[0].name | string | `"argocd-config"` |  |
| projects[0].urls[0].path | string | `"./"` |  |
| projects[0].urls[0].url | string | `"git@github.com:polarpoint-io/argocd-app-of-apps.git"` |  |
| projects[1].applicationSets.applications[0].name | string | `"prometheus"` |  |
| projects[1].applicationSets.applications[0].namespace | string | `"observability"` |  |
| projects[1].applicationSets.applications[0].path | string | `"releases/apps/observability/kube-prometheus-stack"` |  |
| projects[1].applicationSets.applications[0].targetRevision | string | `"HEAD"` |  |
| projects[1].applicationSets.applications[0].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].applicationSets.applications[0].valuesFile | string | `"values.yaml"` |  |
| projects[1].applicationSets.applications[1].name | string | `"certmanager"` |  |
| projects[1].applicationSets.applications[1].namespace | string | `"foundational"` |  |
| projects[1].applicationSets.applications[1].path | string | `"releases/apps/foundational/cert-manager"` |  |
| projects[1].applicationSets.applications[1].targetRevision | string | `"HEAD"` |  |
| projects[1].applicationSets.applications[1].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].applicationSets.applications[1].valuesFile | string | `"values.yaml"` |  |
| projects[1].applicationSets.applications[2].name | string | `"kuberhealthy"` |  |
| projects[1].applicationSets.applications[2].namespace | string | `"observability"` |  |
| projects[1].applicationSets.applications[2].path | string | `"releases/apps/observability/kuberhealthy"` |  |
| projects[1].applicationSets.applications[2].targetRevision | string | `"HEAD"` |  |
| projects[1].applicationSets.applications[2].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].applicationSets.applications[2].valuesFile | string | `"values.yaml"` |  |
| projects[1].applicationSets.applications[3].name | string | `"linkerd"` |  |
| projects[1].applicationSets.applications[3].namespace | string | `"foundational"` |  |
| projects[1].applicationSets.applications[3].path | string | `"releases/apps/foundational/linkerd"` |  |
| projects[1].applicationSets.applications[3].targetRevision | string | `"HEAD"` |  |
| projects[1].applicationSets.applications[3].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].applicationSets.applications[3].valuesFile | string | `"values.yaml"` |  |
| projects[1].applicationSets.applications[4].name | string | `"falco"` |  |
| projects[1].applicationSets.applications[4].namespace | string | `"security"` |  |
| projects[1].applicationSets.applications[4].path | string | `"releases/apps/security/sysdig-falco"` |  |
| projects[1].applicationSets.applications[4].targetRevision | string | `"HEAD"` |  |
| projects[1].applicationSets.applications[4].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].applicationSets.applications[4].valuesFile | string | `"values.yaml"` |  |
| projects[1].applicationSets.destinations[0].name | string | `"deploy"` |  |
| projects[1].applicationSets.destinations[0].namespace | string | `"*"` |  |
| projects[1].applicationSets.destinations[0].server | string | `"https://kubernetes.default.svc"` |  |
| projects[1].name | string | `"foundational"` |  |
| projects[1].permissions.ro.description | string | `"Read-Only Access"` |  |
| projects[1].permissions.ro.groups[0] | string | `"FOUNDATIONAL-RO"` |  |
| projects[1].permissions.rw.description | string | `"Read-Write Access"` |  |
| projects[1].permissions.rw.groups[0] | string | `"FOUNDATIONAL-RW"` |  |
| projects[1].urls[0].name | string | `"argocd-foundational-applications"` |  |
| projects[1].urls[0].url | string | `"git@github.com:polarpoint-io/argocd-foundational-applications.git"` |  |
| projects[1].urls[1].name | string | `"argocd-sysdig-falco-repo"` |  |
| projects[1].urls[1].url | string | `"https://falcosecurity.github.io/charts"` |  |
| projects[2].applications[0].name | string | `"tooling-argocd-applications"` |  |
| projects[2].applications[0].path | string | `"releases"` |  |
| projects[2].applications[0].targetRevision | string | `"main"` |  |
| projects[2].applications[0].url | string | `"git@github.com:polarpoint-io/argocd-tooling-applications.git"` |  |
| projects[2].applications[0].valuesFile | string | `"values.yaml"` |  |
| projects[2].applications[1].directory.recurseDirectory | bool | `false` |  |
| projects[2].applications[1].name | string | `"argow-template-library"` |  |
| projects[2].applications[1].path | string | `"releases/apps/workflows"` |  |
| projects[2].applications[1].targetRevision | string | `"main"` |  |
| projects[2].applications[1].url | string | `"git@github.com:polarpoint-io/argow-template-library.git"` |  |
| projects[2].destinations[0].name | string | `"default"` |  |
| projects[2].destinations[0].namespace | string | `"*"` |  |
| projects[2].destinations[0].server | string | `"https://kubernetes.default.svc"` |  |
| projects[2].name | string | `"tooling"` |  |
| projects[2].permissions.ro.description | string | `"Read-Only Access"` |  |
| projects[2].permissions.ro.groups[0] | string | `"TOOLING-RO"` |  |
| projects[2].permissions.rw.description | string | `"Read-Write Access"` |  |
| projects[2].permissions.rw.groups[0] | string | `"TOOLING-RW"` |  |
| projects[2].urls[0].name | string | `"argocd-tooling-applications"` |  |
| projects[2].urls[0].url | string | `"git@github.com:polarpoint-io/argocd-tooling-applications.git"` |  |
| projects[2].urls[1].name | string | `"argocd-crossplane-repo"` |  |
| projects[2].urls[1].url | string | `"https://charts.crossplane.io/stable"` |  |
| projects[2].urls[2].name | string | `"argocd-dependency-track-repo"` |  |
| projects[2].urls[2].url | string | `"https://evryfs.github.io/helm-charts/"` |  |
| projects[2].urls[3].name | string | `"backstage-repo"` |  |
| projects[2].urls[3].url | string | `"https://vinzscam.github.io/backstage-chart"` |  |
| projects[2].urls[4].name | string | `"argocd-argo-repo"` |  |
| projects[2].urls[4].url | string | `"https://argoproj.github.io/argo-helm"` |  |
| projects[2].urls[5].name | string | `"sonarqube-repo"` |  |
| projects[2].urls[5].url | string | `"https://SonarSource.github.io/helm-chart-sonarqube"` |  |
| projects[2].urls[6].name | string | `"jenkins"` |  |
| projects[2].urls[6].url | string | `"https://charts.jenkins.io"` |  |
| projects[2].urls[7].name | string | `"argo-workflows-library"` |  |
| projects[2].urls[7].url | string | `"git@github.com:polarpoint-io/argow-template-library.git"` |  |
| publicHelmRepositories[0].name | string | `"argocd-bitnami-repo"` |  |
| publicHelmRepositories[0].url | string | `"https://charts.bitnami.com/bitnami"` |  |
| publicHelmRepositories[1].name | string | `"argocd-argo-repo"` |  |
| publicHelmRepositories[1].url | string | `"https://argoproj.github.io/argo-helm"` |  |
| publicHelmRepositories[2].name | string | `"argocd-crossplane-repo"` |  |
| publicHelmRepositories[2].url | string | `"https://charts.crossplane.io/stable"` |  |
| publicHelmRepositories[3].name | string | `"argocd-dependency-track-repo"` |  |
| publicHelmRepositories[3].url | string | `"https://evryfs.github.io/helm-charts/"` |  |
| publicHelmRepositories[4].name | string | `"backstage-repo"` |  |
| publicHelmRepositories[4].url | string | `"https://vinzscam.github.io/backstage-chart"` |  |
| publicHelmRepositories[5].name | string | `"sonarqube-repo"` |  |
| publicHelmRepositories[5].url | string | `"https://SonarSource.github.io/helm-chart-sonarqube"` |  |
| publicHelmRepositories[6].name | string | `"jenkins"` |  |
| publicHelmRepositories[6].url | string | `"https://charts.jenkins.io"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs](https://github.com/norwoodj/helm-docs)