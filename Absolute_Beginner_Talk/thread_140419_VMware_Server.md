---
title: "VMware Server"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by arjanhs on 2006-03-06
I'm trying to install VMware Server, afther running the install i'm running vmware-config.pl, the following line appears afther running this:

The directory of kernel headers (version 2.6.12) does not match your running
kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

With debian i was able to apt-get kernel-headers, but can't find the package in Ubuntu.

Arjan

---

### Post by alamba on 2006-03-06
uname -a would give you your current kernel version. Then using synaptic download the headers for that version. Incase you don't have a gui, search the repositories for ubuntu via http and you'll get the complete name for the package to download via apt-get.

A

---

### Post by arjanhs on 2006-03-06
Found it, thanks, think i used the wrong syntax.

Arjan

---

