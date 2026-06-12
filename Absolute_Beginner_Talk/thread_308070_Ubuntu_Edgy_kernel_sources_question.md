---
title: "Ubuntu Edgy kernel sources question"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by chetroia on 2006-11-27
Just installed dual boot Xp/Edgy on toshiba tecra m3 and everything worked even wireless. By default are kernel sources installed with Edgy? I installed Cico vpn client and had no problem it must look for kernel sources somewhere. I have tried with Fed 5 and had to patch a file in order to get Vpn client to work. 
By default are kernel sources installed with Edgy? and How do I upgrade to newer kernels? Will source install too or do I need to install source myself like in Fedora?

Thanks!

---

### Post by qscgz on 2006-11-28
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

"Browsing the package database"

[https://wiki.ubuntu.com/KernelSourceDriver](https://wiki.ubuntu.com/KernelSourceDriver) (?)

---

### Post by nickburns on 2006-11-28
To pull down the headers from repos use:

sudo apt-get install linux-headers-`uname -r` 

then the headers are at

/usr/src/kernel/include

---

