---
title: "Strange error on update"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-03-04
I keep getting the following error when i try to run any updates on gusty. I havent a clue what it means or how to fix it. Can someone help please.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by jan quark on 2008-03-04
run```
 sudo dpkg --configure -a
```
in terminal and post any error message you get

---

### Post by Tek-Noir on 2008-03-04
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by Tek-Noir on 2008-03-05
Anyone any ideas on how to solve this?

---

### Post by Tek-Noir on 2008-03-05
Anyone? Or does anyone know if i reinstall ubuntu will i loose all my settings and programs i have installed?

---

