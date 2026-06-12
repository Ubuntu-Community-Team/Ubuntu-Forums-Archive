---
title: "Xen BomU kernel boot from NFS"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by m_atif on 2007-07-26
Hi
I am trying to boot Xen 3.1 guests using NFS for migration purpose and have tried to follow [http://www.debian-administration.org/articles/505]("[URL="http://www.debian-administration.org/articles/505")"][http://www.debian-administration.org/articles/505]("http://www.debian-administration.org/articles/505")[/URL]
This includes compiling the guest domain (domU) kernel with CONFIG_ROOT_NFS support inside the kernel. I am not sure if that is compiled inside or not, but Config files suggests that 
CONFIG_ROOT_NFS=y and all other necessary things are build inside. 

Now once i try to boot the virtual machine (vm), it waits for root file system and then drops to the initram shell. Once VM drops to shall, i am able to ping it from the NFS server (Ip y.y.y.y)
Upon a closer look i saw that kernel boot data is not correct i.e.
Bootdata ok (command line is ip=xx.xx.x.x:y.y.y.y::255.255.255.0:mvp1:eth0:off nfsroot=y.y.y.y:nfs/xen-mig/vp ). I think it is missing root=/dev/nfs. 
The config file of my virtual machine has the correct entries. 
NFS server (y.y.y.y) is exporting the file /nfs/xen-mig/vp and is visible. Once in the init shell I am able to mount the nfs/xen-mig/vp to /root but not /. 

My kernel version is 2.6.18 (Xen) and NFS server is running on 2.6.16.13. 
Can anyone help me? :confused:
I apologize if i have missed out on details.

---

