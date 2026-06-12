---
title: "mount to NFS server failed"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-18
I am trying to mount using the "mount" command but the system is giving me the following error message :

"mount to NFS server failed : server is down"

I pinged the IP of the NFS server and i can get the response from it . 

I dont know where the problem lies 

Thanks in advance.

---

### Post by digen on 2006-12-18
What is the output of the below command ?

> #showmount -e 192.168.0.1

replace 192.168.0.1 with your NFS server IP.But it appears that the NFS server is down.

---

### Post by lance_klusener on 2006-12-18
I get the output as "RPC mount unable to receive "

---

### Post by bodhi.zazen on 2006-12-18
See if this guide helps:

[NFS Easy Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

---

### Post by lance_klusener on 2006-12-18
yes i think the link would be helpful , i will come back with errors that i encounter ( if any )

---

