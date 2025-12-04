Установить **k3s** на свой Arch (или на ВМ в облаке):
```
curl -sfL https://get.k3s.io | sh -
```
Установить Argo CD
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
Получить пароль:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
Пробросить порт и зайди в UI:
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Открыть `https://localhost:8080`
Создать приложение через UI или `kubectl apply -f argocd-app.yaml`