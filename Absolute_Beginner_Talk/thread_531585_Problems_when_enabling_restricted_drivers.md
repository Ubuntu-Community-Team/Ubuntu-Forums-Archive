---
title: "Problems when enabling restricted drivers"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Wanderlei on 2007-08-21
I was trying to enable the restricted drivers and got this error message

E: linux-image-2.6.20-16-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.20-16-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

any ideas on what this means and can offer any suggestions?

---

### Post by overdrank on 2007-08-21
> **Wanderlei said:**
> I was trying to enable the restricted drivers and got this error message

E: linux-image-2.6.20-16-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.20-16-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

any ideas on what this means and can offer any suggestions?

HI can you post the out put of the commands 
```
sudo apt-get update
sudo apt-get upgrade 
```
From the terminal and it is located under applications, accessories, terminal

---

### Post by Wanderlei on 2007-08-21
yeah,  got all sorts of errors from sudo apt-get upgrade as well

Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
/bin/sh: Can't open sha1sum
Failed to create initrd image.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Wanderlei on 2007-08-21
bump for great justice

:P

---

### Post by overdrank on 2007-08-22
Hi sorry for the late response I am at a lost and have not seen that error before, I think maybe you can go to synaptic manager and search for that kernel
2.6.20-16-generic
If it is make for as installed then try and reinstall it. Synaptic manger is located under system, administration, synaptic

---

