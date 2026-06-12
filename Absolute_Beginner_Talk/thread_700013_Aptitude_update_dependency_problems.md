---
title: "Aptitude update dependency problems"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2008-02-17
sudo aptitude update && sudo aptitude upgrade -y results in:
> Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following partially installed packages will be configured:
  linux-image-2.6.22-14-generic linux-restricted-modules-2.6.22-14-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...

Running depmod.

update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

Not updating initrd symbolic links since we are being updated/reinstalled 

(2.6.22-14.46 was configured last, according to dpkg)

Not updating image symbolic links since we are being updated/reinstalled 

(2.6.22-14.46 was configured last, according to dpkg)

Running postinst hook script /sbin/update-grub.

Searching for GRUB installation directory ... found: /boot/grub

Searching for default file ... found: /boot/grub/default

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

Searching for splash image ... none found, skipping ...

expr: non-numeric argument

User postinst hook script [/sbin/update-grub] exited with value 3

dpkg: error processing linux-image-2.6.22-14-generic (--configure):

 subprocess post-installation script returned error exit status 3

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:

 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:

  Package linux-image-2.6.22-14-generic is not configured yet.

dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 linux-image-2.6.22-14-generic

 linux-restricted-modules-2.6.22-14-generic

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...

What do I do?

---

### Post by Shazaam on 2008-02-17
Try this...
```
sudo dpkg --configure -a
```
Then try your code again.

---

### Post by AncientPC on 2008-02-18
sudo dpkg --configure -a:
> Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 3
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-restricted-modules-2.6.22-14-generic

---

### Post by oedha on 2008-02-18
mmm........it also happen with me.....and unil know...i dont know why
(it also happen to local repo installation)
but i did....update all except...that generic......
then later on...i just update that single file(re-download).....it work
but i didnt use terminal...........update manager

---

### Post by AncientPC on 2008-03-02
Bump.

---

