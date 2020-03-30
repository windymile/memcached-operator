# Steps
```
$ operator-sdk new memcached-operator --repo=github.com/windymile/memcached-operator
$ cd memcached-operator/
$ git init
$ git remote add origin https://github.com/windymile/memcached-operator.git
$ git push -u origin master
$ operator-sdk add api --api-version=cache.example.com/v1alpha1 --kind=Memcached
- (edit scheme)
$ operator-sdk generate k8s
$ operator-sdk generate crds
$ git push -u origin master
$ operator-sdk add controller --api-version=cache.example.com/v1alpha1 --kind=Memcached
- (edit controller)
$ git push -u origin master
$ operator-sdk build quay.io/windymile/memcached-operator:v0.0.1
$ docker push quay.io/windymile/memcached-operator:v0.0.1
- (edit yaml files)
$ kubectl apply -f deploy/crds/cache.example.com_memcacheds_crd.yaml
$ kubectl apply -f deploy/service_account.yaml 
$ kubectl apply -f deploy/role.yaml 
$ kubectl apply -f deploy/role_binding.yaml 
$ kubectl apply -f deploy/operator.yaml
$ kubeclt get pods
$ kubectl apply -f deploy/crds/cache.example.com_v1alpha1_memcached_cr.yaml
$ kubectl logs memcached-operator-b6dd55bf6-7z2h6
$ kubectl delete -f deploy/crds/cache.example.com_v1alpha1_memcached_cr.yaml 
$ kubectl delete -f deploy/operator.yaml 
$ kubectl delete -f deploy/role_binding.yaml 
$ kubectl delete -f deploy/role.yaml 
$ kubectl delete -f deploy/service_account.yaml 
$ kubectl delete -f deploy/crds/cache.example.com_memcacheds_crd.yaml 
```