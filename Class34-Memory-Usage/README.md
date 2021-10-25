# Find Out Memory Usage


## Prerequisites

1.	**server.cnl.com** – 1 CPU – 1GB RAM (Python 2.7) - **Ansible Server**
2.	**node1.cnl.com** – 1 CPU – 1GB RAM ( python 2.6 and above) - **Ansible Client 1**
3.	**node2.cnl.com** – 1 CPU – 1GB RAM ( python 2.6 and above) - **Ansible Client 2**

from ansible server login as an ansible user as per class 4.From ansible user execute below command

ansible all -m ping

this above ping command should return with ping / pong green color.





## How to Monitor LINUX Memory Utilization Using Ansible Playbook*********

# Step 1: Make your you have installed "sysstat & bc" rpms on all the Linux systems to access the "sar/bc" commands

```
sudo yum install sysstat -y 
sudo yum install sysstat -y 
```

# Step 2: Crete a playbook to check the Memory Usage for 3 intervals (3 sec)
 
```
vi memory-monitoring.yml
```

 
#Step 3: Apply the logic using ansible "WHEN" condition and print message accordingly 



  IF 
    - MEMORY Used percentage less than 90 (MEMORY Usage < 90 %)                 =====> Normal
  ELSE
    - MEMORY Used percentage greater than or equal to 90 (MEMORY Usage >= 90 %) ====> Abnormal
-------------------------------------------------------------------------------- 


# Step 4: Perform ansible playbook syntax checks

```
ansible-playbook memory-monitoring.yml --syntax-check
```


# Step 5: Execute MEMORY utilization monitoring playbook and see the results

```
ansible-playbook -e "HOSTS=all" memory-monitoring.yml
```



***For Testing Purpose stress" 585 Mb for 2 minutes***

- in node1

```
cat <( </dev/zero head -c 585m) <(sleep 120) | tail
```

# Step 6: Send Ansible Email notification if MEMORY usage more than 90% (or) (MEMORY Usage >= 90 %)

```
ansible-playbook -e "HOSTS=all" MEMORY-monitoring.yml --ask-vault-pass
```


#Step 7: Check your Gmail Inbox.

#Step 8: Download playbook for your Reference using description link