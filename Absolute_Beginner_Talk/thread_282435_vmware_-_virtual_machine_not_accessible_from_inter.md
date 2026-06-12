---
title: "vmware - virtual machine not accessible from internet"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by m2all on 2006-10-22
Hello,

i have setup the latest Ubuntu 6.06 LAMP server package and the vmware server 1.01 - the installation was successfull. Both the ubuntu server and the virtual machine have (external) static ip adresses, furthermore the virtual machine runs in bridged network mode.

The problem is that i cannot reach the virtual machine from the internet (e.g. ping, http), but i can reach the virtual machine  from the host (ubuntu server) itself and the host is also accessible from the internet.

What i have forgotten to conifigure?

Any help would be great. Thanks.

---

### Post by ojasvi rajpal on 2006-10-22
I had a similar problem whike using vmware in windows ( I used windows to host linux). I could ping the windows via net but not the host os ( linux). I think is a bug or a safety feature ( not sure ) but it is not a ubuntu specific problem

---

### Post by hyper_ch on 2006-10-22
Is it set up as bridged networking or NAT?

---

### Post by vinnn on 2006-10-22
Switch the VM's networking to NAT

---

### Post by m2all on 2006-10-23
> **sjau said:**
> Is it set up as bridged networking or NAT?

bridged networking!

---

