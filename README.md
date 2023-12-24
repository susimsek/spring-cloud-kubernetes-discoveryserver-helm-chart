<!--- app-name: Spring Cloud Kubernetes Discovery Server -->

# Spring Cloud Kubernetes Discovery Server Helm Chart

The Spring Cloud Kubernetes Discovery Server provides HTTP endpoints apps can use to gather information about services available within a Kubernetes cluster. The Spring Cloud Kubernetes Discovery Server can be used by apps using the spring-cloud-starter-kubernetes-discoveryclient to provide data to the DiscoveryClient implementation provided by that starter.

[Overview of Spring Cloud Kubernetes Discovery Server](https://docs.spring.io/spring-cloud-kubernetes/reference/spring-cloud-kubernetes-discoveryserver.html)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.

## TL;DR

```console
helm install my-release oci://registry-1.docker.io/bitnamicharts/spring-cloud-kubernetes-discoveryserver
```

## Introduction

This charts for Helm are carefully engineered, actively maintained and are the quickest and easiest way to deploy containers on a Kubernetes cluster that are ready to handle production workloads.

This chart can be used with [Kubeapps](https://kubeapps.dev/) for deployment and management of Helm Charts in clusters.

## Prerequisites

- Kubernetes 1.23+
- Helm 3.8.0+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release oci://REGISTRY_NAME/REPOSITORY_NAME/spring-cloud-kubernetes-discoveryserver
```

> Note: You need to substitute the placeholders `REGISTRY_NAME` and `REPOSITORY_NAME` with a reference to your Helm chart registry and repository. For example, in the case of Bitnami, you need to use `REGISTRY_NAME=registry-1.docker.io` and `REPOSITORY_NAME=bitnamicharts`.

These commands deploy a Spring Cloud Kubernetes Discovery Server application on the Kubernetes cluster in the default configuration.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

### Global parameters

| Name                      | Description                                     | Value |
| ------------------------- | ----------------------------------------------- | ----- |
| `global.imageRegistry`    | Global Docker image registry                    | `""`  |
| `global.imagePullSecrets` | Global Docker registry secret names as an array | `[]`  |
| `global.storageClass`     | Global StorageClass for Persistent Volume(s)    | `""`  |

### Common parameters

| Name                     | Description                                                                             | Value           |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `kubeVersion`            | Force target Kubernetes version (using Helm capabilities if not set)                    | `""`            |
| `nameOverride`           | String to partially override common.names.fullname                                      | `""`            |
| `fullnameOverride`       | String to fully override common.names.fullname                                          | `""`            |
| `namespaceOverride`      | String to fully override common.names.namespace                                         | `""`            |
| `commonLabels`           | Labels to add to all deployed objects                                                   | `{}`            |
| `enableServiceLinks`     | If set to false, disable Kubernetes service links in the pod spec                       | `true`          |
| `commonAnnotations`      | Annotations to add to all deployed objects                                              | `{}`            |
| `dnsPolicy`              | DNS Policy for pod                                                                      | `""`            |
| `dnsConfig`              | DNS Configuration pod                                                                   | `{}`            |
| `clusterDomain`          | Default Kubernetes cluster domain                                                       | `cluster.local` |
| `extraDeploy`            | Array of extra objects to deploy with the release                                       | `[]`            |
| `diagnosticMode.enabled` | Enable diagnostic mode (all probes will be disabled and the command will be overridden) | `false`         |
| `diagnosticMode.command` | Command to override all containers in the the statefulset                               | `["sleep"]`     |
| `diagnosticMode.args`    | Args to override all containers in the the statefulset                                  | `["infinity"]`  |

### Spring Cloud Kubernetes Discovery Server parameters

| Name                             | Description                                                                                                                  | Value                         |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| `image.registry`                 | Spring Cloud Kubernetes Discovery Server image registry                                                                                                     | `REGISTRY_NAME`               |
| `image.repository`               | Spring Cloud Kubernetes Discovery Server image repository                                                                                                   | `REPOSITORY_NAME/spring-cloud-kubernetes-discoveryserver`    |
| `image.digest`                   | Spring Cloud Kubernetes Discovery Server image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                    | `""`                          |
| `image.pullPolicy`               | Spring Cloud Kubernetes Discovery Server image pull policy                                                                                                  | `IfNotPresent`                |
| `image.pullSecrets`              | Specify docker-registry secret names as an array                                                                             | `[]`                          |
| `tls.enabled`                    | Enable TLS encryption. Required for HTTPs traffic.                                                                           | `false`                       |
| `command`                        | Override default container command (useful when using custom images)                                                         | `[]`                          |
| `args`                           | Override default container args (useful when using custom images)                                                            | `[]`                          |
| `extraEnvVars`                   | Extra environment variables to be set on Spring Cloud Kubernetes Discovery Server container                                                                 | `[]`                          |
| `extraEnvVarsCM`                 | Name of existing ConfigMap containing extra env vars                                                                         | `""`                          |
| `extraEnvVarsSecret`             | Name of existing Secret containing extra env vars                                                                            | `""`                          |

### Deployment parameters

| Name                                                | Description                                                                                                              | Value            |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| `replicaCount`                                      | Number of Spring Cloud Kubernetes Discovery Server replicas to deploy                                                                                    | `1`              |
| `containerPorts.http`                               | Spring Cloud Kubernetes Discovery Server HTTP container port                                                                                             | `8080`           |
| `containerPorts.https`                              | Spring Cloud Kubernetes Discovery Server HTTPS container port                                                                                            | `8443`           |
| `containerPorts.infinispan`                         | Spring Cloud Kubernetes Discovery Server infinispan container port                                                                                       | `7800`           |
| `extraContainerPorts`                               | Optionally specify extra list of additional port-mappings for Spring Cloud Kubernetes Discovery Server container                                         | `[]`             |
| `podSecurityContext.enabled`                        | Enabled Spring Cloud Kubernetes Discovery Server pods' Security Context                                                                                  | `true`           |
| `podSecurityContext.fsGroup`                        | Set Spring Cloud Kubernetes Discovery Server pod's Security Context fsGroup                                                                              | `1001`           |
| `containerSecurityContext.enabled`                  | Enabled containers' Security Context                                                                                     | `true`           |
| `containerSecurityContext.runAsUser`                | Set containers' Security Context runAsUser                                                                               | `1001`           |
| `containerSecurityContext.runAsNonRoot`             | Set container's Security Context runAsNonRoot                                                                            | `true`           |
| `containerSecurityContext.privileged`               | Set container's Security Context privileged                                                                              | `false`          |
| `containerSecurityContext.readOnlyRootFilesystem`   | Set container's Security Context readOnlyRootFilesystem                                                                  | `false`          |
| `containerSecurityContext.allowPrivilegeEscalation` | Set container's Security Context allowPrivilegeEscalation                                                                | `false`          |
| `containerSecurityContext.capabilities.drop`        | List of capabilities to be dropped                                                                                       | `["ALL"]`        |
| `containerSecurityContext.seccompProfile.type`      | Set container's Security Context seccomp profile                                                                         | `RuntimeDefault` |
| `resources.limits`                                  | The resources limits for the Spring Cloud Kubernetes Discovery Server containers                                                                         | `{}`             |
| `resources.requests`                                | The requested resources for the Spring Cloud Kubernetes Discovery Server containers                                                                      | `{}`             |
| `livenessProbe.enabled`                             | Enable livenessProbe on Spring Cloud Kubernetes Discovery Server containers                                                                              | `true`           |
| `livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                                                  | `300`            |
| `livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                                         | `1`              |
| `livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                                        | `5`              |
| `livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                                      | `3`              |
| `livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                                      | `1`              |
| `readinessProbe.enabled`                            | Enable readinessProbe on Spring Cloud Kubernetes Discovery Server containers                                                                             | `true`           |
| `readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                                                 | `30`             |
| `readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                                        | `10`             |
| `readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                                       | `1`              |
| `readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                                                     | `3`              |
| `readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                                                     | `1`              |
| `startupProbe.enabled`                              | Enable startupProbe on Spring Cloud Kubernetes Discovery Server containers                                                                               | `false`          |
| `startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                                                   | `30`             |
| `startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                                          | `5`              |
| `startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                                         | `1`              |
| `startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                                       | `60`             |
| `startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                                       | `1`              |
| `customLivenessProbe`                               | Custom Liveness probes for Spring Cloud Kubernetes Discovery Server                                                                                      | `{}`             |
| `customReadinessProbe`                              | Custom Rediness probes Spring Cloud Kubernetes Discovery Server                                                                                          | `{}`             |
| `customStartupProbe`                                | Custom Startup probes for Spring Cloud Kubernetes Discovery Server                                                                                       | `{}`             |
| `lifecycleHooks`                                    | LifecycleHooks to set additional configuration at startup                                                                | `{}`             |
| `hostAliases`                                       | Deployment pod host aliases                                                                                              | `[]`             |
| `podLabels`                                         | Extra labels for Spring Cloud Kubernetes Discovery Server pods                                                                                           | `{}`             |
| `podAnnotations`                                    | Annotations for Spring Cloud Kubernetes Discovery Server pods                                                                                            | `{}`             |
| `podAffinityPreset`                                 | Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                      | `""`             |
| `podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                 | `soft`           |
| `nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard`                                | `""`             |
| `nodeAffinityPreset.key`                            | Node label key to match. Ignored if `affinity` is set.                                                                   | `""`             |
| `nodeAffinityPreset.values`                         | Node label values to match. Ignored if `affinity` is set.                                                                | `[]`             |
| `affinity`                                          | Affinity for pod assignment                                                                                              | `{}`             |
| `nodeSelector`                                      | Node labels for pod assignment                                                                                           | `{}`             |
| `tolerations`                                       | Tolerations for pod assignment                                                                                           | `[]`             |
| `topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains. Evaluated as a template | `[]`             |
| `podManagementPolicy`                               | Pod management policy for the Spring Cloud Kubernetes Discovery Server statefulset                                                                       | `Parallel`       |
| `priorityClassName`                                 | Spring Cloud Kubernetes Discovery Server pods' Priority Class Name                                                                                       | `""`             |
| `schedulerName`                                     | Use an alternate scheduler, e.g. "stork".                                                                                | `""`             |
| `terminationGracePeriodSeconds`                     | Seconds Spring Cloud Kubernetes Discovery Server pod needs to terminate gracefully                                                                       | `""`             |
| `updateStrategy.type`                               | Spring Cloud Kubernetes Discovery Server statefulset strategy type                                                                                       | `RollingUpdate`  |
| `updateStrategy.rollingUpdate`                      | Spring Cloud Kubernetes Discovery Server statefulset rolling update configuration parameters                                                             | `{}`             |
| `extraVolumes`                                      | Optionally specify extra list of additional volumes for Spring Cloud Kubernetes Discovery Server pods                                                    | `[]`             |
| `extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for Spring Cloud Kubernetes Discovery Server container(s)                                       | `[]`             |
| `initContainers`                                    | Add additional init containers to the Spring Cloud Kubernetes Discovery Server pods                                                                      | `[]`             |
| `sidecars`                                          | Add additional sidecar containers to the Spring Cloud Kubernetes Discovery Server pods                                                                   | `[]`             |

### Exposure parameters

| Name                               | Description                                                                                                                      | Value                    |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| `service.type`                     | Kubernetes service type                                                                                                          | `ClusterIP`              |
| `service.http.enabled`             | Enable http port on service                                                                                                      | `true`                   |
| `service.ports.http`               | Spring Cloud Kubernetes Discovery Server service HTTP port                                                                                                       | `80`                     |
| `service.ports.https`              | Spring Cloud Kubernetes Discovery Server service HTTPS port                                                                                                      | `443`                    |
| `service.nodePorts`                | Specify the nodePort values for the LoadBalancer and NodePort service types.                                                     | `{}`                     |
| `service.sessionAffinity`          | Control where client requests go, to the same pod or round-robin                                                                 | `None`                   |
| `service.sessionAffinityConfig`    | Additional settings for the sessionAffinity                                                                                      | `{}`                     |
| `service.clusterIP`                | Spring Cloud Kubernetes Discovery Server service clusterIP IP                                                                                                    | `""`                     |
| `service.loadBalancerIP`           | loadBalancerIP for the SuiteCRM Service (optional, cloud specific)                                                               | `""`                     |
| `service.loadBalancerSourceRanges` | Address that are allowed when service is LoadBalancer                                                                            | `[]`                     |
| `service.externalTrafficPolicy`    | Enable client source IP preservation                                                                                             | `Cluster`                |
| `service.annotations`              | Additional custom annotations for Spring Cloud Kubernetes Discovery Server service                                                                               | `{}`                     |
| `service.extraPorts`               | Extra port to expose on Spring Cloud Kubernetes Discovery Server service                                                                                         | `[]`                     |
| `ingress.enabled`                  | Enable ingress record generation for Spring Cloud Kubernetes Discovery Server                                                                                    | `false`                  |
| `ingress.ingressClassName`         | IngressClass that will be be used to implement the Ingress (Kubernetes 1.18+)                                                    | `""`                     |
| `ingress.pathType`                 | Ingress path type                                                                                                                | `ImplementationSpecific` |
| `ingress.apiVersion`               | Force Ingress API version (automatically detected if not set)                                                                    | `""`                     |
| `ingress.hostname`                 | Default host for the ingress record (evaluated as template)                                                                      | `spring-cloud-kubernetes-discoveryserver.local`         |
| `ingress.path`                     | Default path for the ingress record (evaluated as template)                                                                      | `""`                     |
| `ingress.servicePort`              | Backend service port to use                                                                                                      | `http`                   |
| `ingress.annotations`              | Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations. | `{}`                     |
| `ingress.labels`                   | Additional labels for the Ingress resource.                                                                                      | `{}`                     |
| `ingress.tls`                      | Enable TLS configuration for the host defined at `ingress.hostname` parameter                                                    | `false`                  |
| `ingress.selfSigned`               | Create a TLS secret for this ingress record using self-signed certificates generated by Helm                                     | `false`                  |
| `ingress.extraHosts`               | An array with additional hostname(s) to be covered with the ingress record                                                       | `[]`                     |
| `ingress.extraPaths`               | Any additional arbitrary paths that may need to be added to the ingress under the main host.                                     | `[]`                     |
| `ingress.extraTls`                 | The tls configuration for additional hostnames to be covered with this ingress record.                                           | `[]`                     |
| `ingress.secrets`                  | If you're providing your own certificates, please use this to add the certificates as secrets                                    | `[]`                     |
| `ingress.extraRules`               | Additional rules to be covered with this ingress record                                                                          | `[]`                     |

### RBAC parameter

| Name                                          | Description                                               | Value   |
| --------------------------------------------- | --------------------------------------------------------- | ------- |
| `serviceAccount.create`                       | Enable the creation of a ServiceAccount for Spring Cloud Kubernetes Discovery Server pods | `true`  |
| `serviceAccount.name`                         | Name of the created ServiceAccount                        | `""`    |
| `serviceAccount.automountServiceAccountToken` | Auto-mount the service account token in the pod           | `true`  |
| `serviceAccount.annotations`                  | Additional custom annotations for the ServiceAccount      | `{}`    |
| `serviceAccount.extraLabels`                  | Additional labels for the ServiceAccount                  | `{}`    |
| `rbac.create`                                 | Whether to create and use RBAC resources or not           | `false` |
| `rbac.rules`                                  | Custom RBAC rules                                         | `[]`    |

### Other parameters

| Name                       | Description                                                    | Value   |
| -------------------------- | -------------------------------------------------------------- | ------- |
| `autoscaling.enabled`      | Enable autoscaling for Spring Cloud Kubernetes Discovery Server                                | `false` |
| `autoscaling.minReplicas`  | Minimum number of Spring Cloud Kubernetes Discovery Server replicas                            | `1`     |
| `autoscaling.maxReplicas`  | Maximum number of Spring Cloud Kubernetes Discovery Server replicas                            | `11`    |
| `autoscaling.targetCPU`    | Target CPU utilization percentage                              | `""`    |
| `autoscaling.targetMemory` | Target Memory utilization percentage                           | `""`    |