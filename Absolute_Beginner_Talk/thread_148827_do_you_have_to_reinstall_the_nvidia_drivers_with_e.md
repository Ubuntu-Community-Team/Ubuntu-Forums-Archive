---
title: "do you have to reinstall the nvidia drivers with every kernel update?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by weatherman on 2006-03-22
Let's say I do a apt-get upgrade and this upgrades my kernel. Will apt take care of upgrading the nvidia drivers as well or do I have to do that by hand?
Tnx.

---

### Post by deBaas on 2006-03-22
If there is a new version of the nvidia drivers as well, it will.

---

### Post by weatherman on 2006-03-23
so basically I don't have to bother? just run "apt-get update && apt-get upgrade" once in a while to keep my system up to date?

---

### Post by codejunkie on 2006-03-23
yep if you installed the driver package with synaptic/apt-get, and not the one from [www.nvidia.com](www.nvidia.com) all the packages will be updated automatically.

---

### Post by weatherman on 2006-03-23
great thanks!
I installed them through 
"sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`"
following this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Cheers, weatherman

---

