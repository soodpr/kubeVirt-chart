# kubeVirt-chart
# Prerequisite:
1. K3s cluster and Kubevirt/CDI is deployed on it
2. PVC is already available which contains the .qcow2 image for Seed/RDA node.
3. Helm3 is already installed on your VM.

# To deploy a VM using Helm chart, execute below command on your Dev machine:
#This is to test the render of the manifest files which are going to get executed on the cluster
$helm3 install kubevirt-chart --dry-run --debug ./kubeVirt-chart
$helm3 install kubevirt-chart ./kubeVirt-chart

Once above command executes successfully, you can check the status of vmi and svc in the cluster:
$Kubectl get vmi -A
$Kubectl get svc -A

# Take the nodePort from above command of the service deployed to expose the VM and do ssh to the newly created VM:
$ssh -i ~/.ssh/id_rsa glcgadmin@<Cluster_IP>-p <NodePort>
