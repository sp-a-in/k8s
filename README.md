# k8s
Practicing k8s




**********************************************************************************Removing kube-scheduler.yaml from /etc/kubernetes/manifests/ inside sparsh-control-plane node ////////////////////////////////////

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get all -A
NAMESPACE            NAME                                               READY   STATUS    RESTARTS       AGE
kube-system          pod/coredns-6f6b679f8f-kbmkd                       1/1     Running   1 (36h ago)    7d2h
kube-system          pod/coredns-6f6b679f8f-qb2xm                       1/1     Running   1 (36h ago)    7d2h
kube-system          pod/etcd-sparsh-control-plane                      1/1     Running   0              36h
kube-system          pod/kindnet-4xq6t                                  1/1     Running   1 (36h ago)    7d2h
kube-system          pod/kindnet-xhf7j                                  1/1     Running   1 (36h ago)    7d2h
kube-system          pod/kindnet-xtdd8                                  1/1     Running   1 (36h ago)    7d2h
kube-system          pod/kube-apiserver-sparsh-control-plane            1/1     Running   0              36h
kube-system          pod/kube-controller-manager-sparsh-control-plane   1/1     Running   33 (10h ago)   7d2h  
kube-system          pod/kube-proxy-6htwq                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-proxy-kpj45                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-proxy-svrgm                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-scheduler-sparsh-control-plane            1/1     Running   40 (10h ago)   7d2h  
local-path-storage   pod/local-path-provisioner-57c5987fd4-m6gzb        1/1     Running   2 (36h ago)    7d2h  

NAMESPACE     NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)                  AGE
default       service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP                  7d2h        
kube-system   service/kube-dns     ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   7d2h        

NAMESPACE     NAME                        DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
kube-system   daemonset.apps/kindnet      3         3         3       3            3           kubernetes.io/os=linux   7d2h
kube-system   daemonset.apps/kube-proxy   3         3         3       3            3           kubernetes.io/os=linux   7d2h

NAMESPACE            NAME                                     READY   UP-TO-DATE   AVAILABLE   AGE
kube-system          deployment.apps/coredns                  2/2     2            2           7d2h
local-path-storage   deployment.apps/local-path-provisioner   1/1     1            1           7d2h

NAMESPACE            NAME                                                DESIRED   CURRENT   READY   AGE       
kube-system          replicaset.apps/coredns-6f6b679f8f                  2         2         2       7d2h      
local-path-storage   replicaset.apps/local-path-provisioner-57c5987fd4   1         1         1       7d2h      

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl delete pod/kube-scheduler-sparsh-control-plane
Error from server (NotFound): pods "kube-scheduler-sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl delete pod/kube-scheduler-sparsh-control-plane -n kube-system
pod "kube-scheduler-sparsh-control-plane" deleted

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get all -A
NAMESPACE            NAME                                               READY   STATUS    RESTARTS       AGE
kube-system          pod/coredns-6f6b679f8f-kbmkd                       1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/coredns-6f6b679f8f-qb2xm                       1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/etcd-sparsh-control-plane                      1/1     Running   0              36h   
kube-system          pod/kindnet-4xq6t                                  1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kindnet-xhf7j                                  1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kindnet-xtdd8                                  1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-apiserver-sparsh-control-plane            1/1     Running   0              36h   
kube-system          pod/kube-controller-manager-sparsh-control-plane   1/1     Running   33 (10h ago)   7d2h  
kube-system          pod/kube-proxy-6htwq                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-proxy-kpj45                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-proxy-svrgm                               1/1     Running   1 (36h ago)    7d2h  
kube-system          pod/kube-scheduler-sparsh-control-plane            1/1     Running   40 (10h ago)   3s    
local-path-storage   pod/local-path-provisioner-57c5987fd4-m6gzb        1/1     Running   2 (36h ago)    7d2h  

NAMESPACE     NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)                  AGE
default       service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP                  7d2h        
kube-system   service/kube-dns     ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   7d2h        

NAMESPACE     NAME                        DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
kube-system   daemonset.apps/kindnet      3         3         3       3            3           kubernetes.io/os=linux   7d2h
kube-system   daemonset.apps/kube-proxy   3         3         3       3            3           kubernetes.io/os=linux   7d2h

NAMESPACE            NAME                                     READY   UP-TO-DATE   AVAILABLE   AGE
kube-system          deployment.apps/coredns                  2/2     2            2           7d2h
local-path-storage   deployment.apps/local-path-provisioner   1/1     1            1           7d2h

NAMESPACE            NAME                                                DESIRED   CURRENT   READY   AGE       
kube-system          replicaset.apps/coredns-6f6b679f8f                  2         2         2       7d2h      
local-path-storage   replicaset.apps/local-path-provisioner-57c5987fd4   1         1         1       7d2h      

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get nodes
NAME                   STATUS   ROLES           AGE    VERSION
sparsh-control-plane   Ready    control-plane   7d2h   v1.31.0
sparsh-worker          Ready    <none>          7d2h   v1.31.0
sparsh-worker2         Ready    <none>          7d2h   v1.31.0

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane --bash
error: unknown flag: --bash
See 'kubectl exec --help' for usage.

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -sh
error: you must specify at least one command for the container

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane --sh
error: unknown flag: --sh
See 'kubectl exec --help' for usage.

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec --help
Execute a command in a container.

Examples:
  # Get output from running the 'date' command from pod mypod, using the first container by default
  kubectl exec mypod -- date

  # Get output from running the 'date' command in ruby-container from pod mypod
  kubectl exec mypod -c ruby-container -- date

  # Switch to raw terminal mode; sends stdin to 'bash' in ruby-container from pod mypod
  # and sends stdout/stderr from 'bash' back to the client
  kubectl exec mypod -c ruby-container -i -t -- bash -il

  # List contents of /usr from the first container of pod mypod and sort by modification time
  # If the command you want to execute in the pod has any flags in common (e.g. -i),
  # you must use two dashes (--) to separate your command's flags/arguments
  # Also note, do not surround your command and its flags/arguments with quotes
  # unless that is how you would execute it normally (i.e., do ls -t /usr, not "ls -t /usr")
  kubectl exec mypod -i -t -- ls -t /usr

  # Get output from running 'date' command from the first pod of the deployment mydeployment, using
the first container by default
  kubectl exec deploy/mydeployment -- date

  # Get output from running 'date' command from the first pod of the service myservice, using the
first container by default
  kubectl exec svc/myservice -- date

Options:
    -c, --container='':
        Container name. If omitted, use the kubectl.kubernetes.io/default-container annotation for
        selecting the container to be attached or the first container in the pod will be chosen

    -f, --filename=[]:
        to use to exec into the resource

    --pod-running-timeout=1m0s:
        The length of time (like 5s, 2m, or 3h, higher than zero) to wait until at least one pod
        is running

    -q, --quiet=false:
        Only print output from the remote session

    -i, --stdin=false:
        Pass stdin to the container

    -t, --tty=false:
        Stdin is a TTY

Usage:
  kubectl exec (POD | TYPE/NAME) [-c CONTAINER] [flags] -- COMMAND [args...] [options]

Use "kubectl options" for a list of global command-line options (applies to all commands).

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -- bash
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -- sh
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -n kube-system -- sh
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it po/pod/kube-scheduler-sparsh-control-plane  -n kube-system -- sh
error: arguments in resource/name form may not have more than one slash

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it pod/kube-scheduler-sparsh-control-plane  -n kube-system -- sh
error: Internal error occurred: Internal error occurred: error executing command in container: failed to exec in container: failed to start exec "70c4b21300e567cbf019574241c3a12be829d90c76aa672a08e47c3f2ff25184": OCI runtime exec failed: exec failed: unable to start container process: exec: "sh": executable file not found in $PATH: unknown

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it pod/kube-scheduler-sparsh-control-plane  -n kube-system -- bash
error: Internal error occurred: Internal error occurred: error executing command in container: failed to exec in container: failed to start exec "3f08865f7452ff650a250fb25eda885b001513ae0cc5cdf5fc13336c8a3a9bbc": OCI runtime exec failed: exec failed: unable to start container process: exec: "bash": executable file not found in $PATH: unknown

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po -n kube-system | grep schedular

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po all | grep schedular
Error from server (NotFound): pods "all" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po | grep schedular
No resources found in default namespace.

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po | grep scheduler
No resources found in default namespace.

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po -n kube-system | grep scheduler
kube-scheduler-sparsh-control-plane            1/1     Running   40 (10h ago)   6m45s

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po/kube-scheduler-sparsh-control-plane -o wide
Error from server (NotFound): pods "kube-scheduler-sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl get po/kube-scheduler-sparsh-control-plane -n kube-system -o wide
NAME                                  READY   STATUS    RESTARTS       AGE    IP           NODE                
   NOMINATED NODE   READINESS GATES
kube-scheduler-sparsh-control-plane   1/1     Running   40 (10h ago)   8m1s   172.18.0.8   sparsh-control-plane   <none>           <none>

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane  -n kube-system -- bash
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -n kube-system -- bash
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ docker exec -it sparsh-control-plane -n kube-system -- bash
OCI runtime exec failed: exec failed: unable to start container process: exec: "-n": executable file not found in $PATH: unknown

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug sparsh-control-plane
    Learn more at https://docs.docker.com/go/debug-cli/

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ docker exec -it sparsh-control-plane -- bash
OCI runtime exec failed: exec failed: unable to start container process: exec: "--": executable file not found in $PATH: unknown

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug sparsh-control-plane
    Learn more at https://docs.docker.com/go/debug-cli/

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$  docker debug sparsh-control-plane
Docker Debug requires a Pro, Teams, or Business Subcription. Learn more at https://docs.docker.com/subscription/details/

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -- bash
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane //bin//sh
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ docker exec -it sparsh-control-plane //bin//sh
# ^C
# exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug sparsh-control-plane
    Learn more at https://docs.docker.com/go/debug-cli/

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec -it sparsh-control-plane -- bash
Error from server (NotFound): pods "sparsh-control-plane" not found

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ docker exec -it sparsh-control-plane //bin//sh
# ls
LICENSES  boot  etc   kind  lib64  mnt  proc  run   srv  tmp  var
bin       dev   home  lib   media  opt  root  sbin  sys  usr
# cd /etc/   
# ls
10-network-magic.conf     dpkg          insserv.conf.d  modules         python3               shadow-
10-network-security.conf  e2scrub.conf  iproute2        modules-load.d  python3.11            shells
adduser.conf              environment   iscsi           motd            rc0.d                 skel
alternatives              ethertypes    issue           mtab            rc1.d                 ssl
apt                       fstab         issue.net       netconfig       rc2.d                 subgid
bash.bashrc               fuse.conf     kernel          network         rc3.d                 subuid
bindresvport.blacklist    gai.conf      keyutils        networks        rc4.d                 sysctl.conf      
binfmt.d                  group         kubelet         nfs.conf        rc5.d                 sysctl.d
ca-certificates           group-        kubernetes      nfs.conf.d      rc6.d                 system
ca-certificates.conf      gshadow       ld.so.cache     nftables.conf   rcS.d                 systemd
cni                       gshadow-      ld.so.conf      nsswitch.conf   request-key.conf      terminfo
config.toml               gss           ld.so.conf.d    opt             request-key.d         timezone
containerd                host.conf     libaudit.conf   os-release      resolv.conf           tmpfiles.d       
crictl.yaml               hostname      localtime       pam.conf        resolv.conf.original  ucf.conf
cron.d                    hosts         login.defs      pam.d           rmt                   udev
cron.daily                hosts.allow   logrotate.d     passwd          rpc                   update-motd.d    
debconf.conf              hosts.deny    machine-id      passwd-         security              xattr.conf       
debian_version            idmapd.conf   mime.types      profile         selinux               xdg
default                   init.d        mke2fs.conf     profile.d       services
deluser.conf              inputrc       modprobe.d      protocols       shadow
# cd /kubernetes
//bin//sh: 4: cd: can't cd to /kubernetes
# cd /kubernetes/
//bin//sh: 5: cd: can't cd to /kubernetes/
# cd manifests
//bin//sh: 6: cd: can't cd to manifests
# cd ..         
# ls
LICENSES  boot  etc   kind  lib64  mnt  proc  run   srv  tmp  var
bin       dev   home  lib   media  opt  root  sbin  sys  usr
# cd /etc/kubernetes/manifests/
# ls
etcd.yaml  kube-apiserver.yaml  kube-controller-manager.yaml  kube-scheduler.yaml
# mv kube-scheular.yaml /tmp/
mv: cannot stat 'kube-scheular.yaml': No such file or directory
# mv kube-schedular.yaml ./../../tmp/
mv: cannot stat 'kube-schedular.yaml': No such file or directory
# mv kube-schedular.yaml /../
mv: cannot stat 'kube-schedular.yaml': No such file or directory
# mv kube-schedular.yaml /tmp
mv: cannot stat 'kube-schedular.yaml': No such file or directory
# mv kube-scheduler.yaml /tmp
# ls
etcd.yaml  kube-apiserver.yaml  kube-controller-manager.yaml
# mv /tmp/kube-scheduler.yaml .
# ls
etcd.yaml  kube-apiserver.yaml  kube-controller-manager.yaml  kube-scheduler.yaml
# exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug sparsh-control-plane
    Learn more at https://docs.docker.com/go/debug-cli/

Sparsh Jain@DESKTOP-T7TR2ID MINGW64 ~/Desktop/k8s/k8s (main)
$ kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Error from server (NotFound): pods "[POD]" not found





********************************************************************************** Taints and Tolderations ////////////////////////////////////












