# ibm-festival-argocd-gitops
This repository contains YAML files that you need for your first own ArgoCD. It also contains the ArgoCD resources that were used in the IBM Talk.

## Rollout openshift-group & Cluster-Read-Permissons

First you have to edit the group in the file "cluster-group.yaml" and add your name and maybe those of your friends. After that you have to ask nicely a cluster admin if he can roll out the group and the cluster-reader rights for the service account of your ArgoCD. If you have the rights yourself execute the following commands:

```bash
$ oc apply -f cluster-group.yaml
$ oc apply -f cluster-rbac.yaml
```

## Rollout ArgoCD & AppProject and Applications
Nachdem nun die lästigen Clusterregeln ausgerollt wurden, könnt Ihr über Kustomize den gesamten Stack ausrollen:

```bash
$ oc apply -k ./
```

IMPORTANT!
After you rollout the ArgoCD Stack, Go Inside your ArgoCD instance go to the ArgoCD cluster settings and add the namespaces from the applications or from the example. 
(Settings > Clusters > in-cluster > namespaces)

You´ve finished! (: 