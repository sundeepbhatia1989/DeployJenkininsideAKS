


Follow: https://www.jenkins.io/doc/book/installing/kubernetes/
Installed jenkins in aks cluster
Follow above link
I have done two changes requires in service.yaml file and deployment.yaml file
-----------------------------
service.yaml

type: NodePort
  ports:
    - port: 8080
      targetPort: 8080
      nodePort: 32000
      
Replace with 
type: LoadBalancer
  ports:
    - port: 8080
      targetPort: 8080
 --------------------------------
 deployment.yaml
 volumes:
        - name: jenkins-data
          persistentVolumeClaim:
              claimName: jenkins-pv-claim
              
 Replace with 
 

volumes:
- name: jenkins-data
emptyDir: \{}

--------
kubectl logs <PODS Name> --namespace=devops-tools
Through is command you will get password of jenkin
 
Now: you can access your jenkin publicily. 
  

http://<node>:8080


