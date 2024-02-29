# monitoring setup for kubenetes

helm upgrade --install websitesecret ./helm-charts/websitesecret

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

          

# install prometheus    

helm upgrade -install prometheus prometheus-community/prometheus --namespace monitoring

# install grafana
helm upgrade -install grafana grafana/grafana --namespace monitoring

# install grafan ingress
          kubectl apply -f vs-grafana.yaml
          
# get grafana admin password - initial
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

#
import 6417 number dashboard for kubenetes cluster details"
