# Kubernetes Interview Questions

Here’s a list of DevOps interview questions focused on Kubernetes, organized from easy to hard:

## Easy Questions

1. **What is Kubernetes?**  
   Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications.

2. **What is a Kubernetes pod?**  
   A pod is the smallest, most basic deployable unit in Kubernetes. It represents a single instance of a running process in a cluster and can contain one or more tightly coupled containers.

3. **What is a Kubernetes cluster?**  
   A cluster is a set of nodes running containerized applications managed by Kubernetes. It includes a control plane and worker nodes.

4. **What is a node in Kubernetes?**  
   A node is a physical or virtual machine that runs containerized applications. Each node is managed by the Kubernetes control plane.

5. **What is a kubelet?**  
   Kubelet is an agent that runs on each node in a Kubernetes cluster and ensures that the containers are running as defined by the cluster's desired state.

6. **What are the key components of the Kubernetes architecture?**  
   Key components include:
   - Master Node (Control Plane): API Server, etcd, Controller Manager, and Scheduler.
   - Worker Node: Kubelet, Container Runtime, Kube-Proxy.

7. **What is kubectl?**  
   kubectl is the command-line interface tool used to interact with a Kubernetes cluster, manage applications, and perform operations such as deploying pods and scaling applications.

8. **What is a service in Kubernetes?**  
   A service is an abstraction that defines a logical set of pods and a policy by which to access them (usually via a stable IP address and DNS name).

9. **How do you expose a deployment in Kubernetes?**  
   Use the kubectl expose command:  
   ```bash
   kubectl expose deployment <deployment_name> --type=NodePort --port=80
   
10. **What is a Kubernetes deployment?**  
    A deployment is a higher-level abstraction for defining how pods should be created, updated, and scaled. It also enables rollback functionality.

## Intermediate Questions

1. **What is etcd in Kubernetes?**  
   etcd is a distributed key-value store used as the backing store for all cluster data. It stores the state and configuration of the cluster.

2. **What is the purpose of a ReplicaSet in Kubernetes?**  
   A ReplicaSet ensures that a specified number of pod replicas are running at any given time. It replaces failed pods with new ones to maintain the desired state.

3. **What is the difference between a Deployment and a StatefulSet?**  
   - **Deployment**: Used for stateless applications, provides updates and rollback features.
   - **StatefulSet**: Used for stateful applications that require unique, stable network identities, persistent storage, and ordered scaling (e.g., databases).

4. **What is a ConfigMap in Kubernetes?**  
   A ConfigMap is an API object used to store non-confidential configuration data in key-value pairs, which can be used by pods to configure applications.

5. **What is a PersistentVolume (PV) and PersistentVolumeClaim (PVC) in Kubernetes?**  
   - **PV**: A storage resource in the cluster.
   - **PVC**: A request for storage by a user, allowing pods to use storage defined in a PV.

6. **How do you perform scaling in Kubernetes?**  
   You can scale deployments either manually:
   ```bash
   kubectl scale deployment <deployment_name> --replicas=3
   ```
   Or automatically using the Horizontal Pod Autoscaler (HPA).

7. **What is a Kubernetes Ingress?**
  An Ingress is an API object that manages external access to services within a Kubernetes cluster, typically HTTP and HTTPS traffic. It provides load balancing and SSL termination.

8. **What is a DaemonSet in Kubernetes?**
  A DaemonSet ensures that a copy of a pod is running on all (or some) nodes in the cluster, commonly used for running system-level services such as logging and monitoring.

9. **How does Kubernetes handle application rollbacks?**
  Kubernetes stores previous versions of deployments, allowing you to rollback to a previous stable version with the command:
  ```bash
  kubectl rollout undo deployment <deployment_name>
  ```
10. **What is the Kubernetes Control Plane?**  
    The control plane consists of components like the API server, etcd, scheduler, and controller manager. It manages the overall state of the cluster, including deciding where to run pods and monitoring the cluster state.

11. **What is the purpose of namespaces in Kubernetes?**  
    Namespaces provide a way to divide cluster resources between multiple users or teams. It allows for resource isolation and enables efficient management in large environments.

12. **What is the Kubernetes Scheduler, and how does it work?**  
    The Kubernetes Scheduler is responsible for assigning pods to nodes. It considers factors like resource requirements, node health, and taints/tolerations to place pods on appropriate nodes.

13. **How does Kubernetes achieve high availability for the control plane?**  
    High availability is achieved by deploying multiple control plane nodes (replicated API servers, etcd clusters) and using load balancers to ensure requests are evenly distributed across them.

14. **Explain taints and tolerations in Kubernetes.**  
    - **Taints**: Applied to nodes to prevent certain pods from being scheduled on them.
    - **Tolerations**: Allow pods to be scheduled on nodes with matching taints.

15. **What is the Horizontal Pod Autoscaler (HPA)?**  
    The HPA automatically scales the number of pod replicas based on CPU utilization or custom metrics like memory or application-level metrics (e.g., request latency).

16. **What is a Kubernetes Job, and how does it differ from a CronJob?**  
    - **Job**: A resource that creates one or more pods and ensures a specific task is completed.
    - **CronJob**: A scheduled job that runs at regular intervals (like a Linux cron).

17. **What are Kubernetes secrets, and how are they different from ConfigMaps?**  
    Secrets are used to store sensitive data, such as passwords, tokens, or keys. Unlike ConfigMaps, secrets are stored in an encrypted form and should be used for sensitive information.

18. **What is the role of the kube-proxy in Kubernetes?**  
    kube-proxy maintains network rules on nodes and facilitates communication between services and pods by managing load balancing across multiple pod replicas.

19. **What is a Sidecar container, and when would you use one?**  
    A sidecar container runs alongside the main container in a pod, providing supplementary features such as logging, monitoring, or data synchronization.

20. **How does Kubernetes handle storage management with dynamic provisioning?**  
    Kubernetes allows for dynamic provisioning of storage using Storage Classes. When a user creates a PVC, Kubernetes automatically provisions a PV based on the storage class.

## Advanced Questions

21. **How does Kubernetes implement load balancing across pods?**  
    Kubernetes uses services (ClusterIP, NodePort, LoadBalancer) to distribute traffic across multiple pods. Ingress controllers can also provide external access with load balancing for HTTP(S) traffic.

22. **What are pod affinity and anti-affinity rules in Kubernetes?**  
    - **Affinity**: Ensures that certain pods are scheduled on nodes that are close to each other (e.g., for performance reasons).
    - **Anti-Affinity**: Ensures that certain pods are scheduled on different nodes to improve fault tolerance.

23. **What is Kubernetes Federation?**  
    Federation allows you to manage multiple Kubernetes clusters as a single entity, enabling consistent configuration and resource management across clusters.

24. **How does Kubernetes manage container networking (CNI)?**  
    Kubernetes uses the Container Network Interface (CNI) to configure networking for containers. Popular CNI implementations include Flannel, Calico, and WeaveNet, which provide networking features such as routing, policy enforcement, and network isolation.

25. **What is Helm in Kubernetes, and why is it used?**  
    Helm is a package manager for Kubernetes that allows users to define, install, and upgrade Kubernetes applications using charts, which are pre-configured Kubernetes resources.

26. **What is the difference between Blue-Green and Canary deployments in Kubernetes?**  
    - **Blue-Green**: Runs two environments (blue for production, green for the new version), switching traffic from blue to green once testing is successful.
    - **Canary**: Gradually introduces a new version of the application to a subset of users, monitoring performance before rolling out fully.

27. **How does Kubernetes implement RBAC (Role-Based Access Control)?**  
    RBAC in Kubernetes allows administrators to define fine-grained access control to cluster resources using roles, role bindings, cluster roles, and cluster role bindings.

28. **How does Kubernetes achieve zero downtime during updates?**  
    Kubernetes updates pods by creating new ones and gracefully terminating old ones through rolling updates. It ensures that a minimum number of pods are always running during the update process.

29. **Explain how to use Prometheus and Grafana for Kubernetes monitoring.**  
    Prometheus is used to collect and store metrics from Kubernetes components and applications. Grafana visualizes these metrics in real-time using customizable dashboards.

30. **What are the different strategies for managing stateful workloads in Kubernetes?**  
    Strategies include using StatefulSets for stable network IDs and persistent storage, using PersistentVolumes and Claims for long-term storage, and implementing backup and disaster recovery mechanisms.
    
## Summary of Difficulty Levels

- **Easy**: Basic Kubernetes components (pods, services, deployments).
- **Intermediate**: Resource management, scaling, networking.
- **Advanced**: Cluster management, load balancing, monitoring, security, and advanced configurations.

This progression covers most of the concepts you’ll encounter in Kubernetes interviews.

