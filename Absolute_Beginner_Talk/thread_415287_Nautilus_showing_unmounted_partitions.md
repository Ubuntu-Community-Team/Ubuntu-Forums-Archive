---
title: "Nautilus showing unmounted partitions"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by gcha on 2007-04-20
Hi, 

I just did a clean upgrade to Feisty 7.04
Everything went pretty well expect :

On my Dell Inspirion 6400 I have 2 recovery partitions
DellRestore and DellUtility

I specifically said in the installation to not mount them.
The fstab makes no mention of my /dev/sda1 and /dev/sda1 (the two dell partitions.)
If I run Gnome Partition Editor, it mounts the two partition automatically and on the desktop.

I can't find a way to hide these two partitions. I tried to introduce some errors in the fstab so they couldn't mount properly, but it still show up in the places menu. 

I want these two partition to get out of my life, but not out of my HD, like it was before with Edgy.

Thank you.

---

### Post by taurus on 2007-04-20
Post your /etc/fstab here then.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by gcha on 2007-04-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a7f6457c-e8d3-40d3-a0f9-b791bcc93fd5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=66d3dc43-47d0-4299-a802-18b5bc8d7151 /boot           ext3    defaults        0       2
# /dev/sda8
UUID=bd179d5d-91ab-4f5c-87e8-f3c2bfb7fd5f /home           ext3    defaults        0       2
# /dev/sda2
UUID=B6E89B58E89B15A9 /mnt/winxp      ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=856aa473-4377-44ce-94de-51132e478784 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Here is my fstab

with a small partition for the /boot
a partition for the / and another for the /home (so in the future it will be easier to do clean upgrades) 
and a ntfs partition

---

### Post by taurus on 2007-04-20
You don't want to mount /dev/sda2, ntfs?

---

### Post by gcha on 2007-04-20
I don't want to mount /dev/sda1 and /dev/sda3 which are fat16 and fat 32 respectively

However these two partition show in nautilus under the "Places menu"

and they are automatically mounted if I start Gparted

---

### Post by gcha on 2007-04-23
Alright I solved my problem by forcing it to mount in a hidden directory 

/mnt/.DellRestore
/mnt/.DellUtiliy

in my fstab

and they don't show up as different drives on nautilus.

---

