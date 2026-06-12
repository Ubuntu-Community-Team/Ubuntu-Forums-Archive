---
title: "help me run ubuntu plz"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-03-14
for someone to be able to help he needs to know about grub... im noobish at it...

this is the situation.. i have ubuntu installed in a SATA  EXT HDD which is /dev/sdc
my BIOS wont load from SATA drives so i made a partition in my IDE primary drive which is  /dev/sda (the partition is in sda2) and in the partition i installed grub... so i can run from there... what i am missing is to configure grub so it will load my ext.. it is possible i have done it before... but i dont remember... its something like this but i dont know what to replace where..

grub
grub> device (hd0) /dev/hda
grub> root (hd0,1)
grub> setup (hd0)
grub> quit




help plz

---

### Post by glennric on 2008-03-14
Can you post the output of "sudo fdisk -l"
Also when you run grub try
```
grub> find /boot/grub/stage1
```
and post what that returns.

---

### Post by patchido on 2008-03-14
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb72fb72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9710    77995543+   7  HPFS/NTFS
/dev/sda2            9711        9729      152617+  83  Linux

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed260086

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6992    56163208+  83  Linux
/dev/sdc2            6993        7296     2441880    5  Extended
/dev/sdc5            6993        7296     2441848+  82  Linux swap / Solaris



grub>
         Device Boot      Start         End      Blocks   Id  System

Error 27: Unrecognized command

grub>
      /dev/sdc1   *           1        6992    56163208+  83  Linux

Error 27: Unrecognized command

grub>
      /dev/sdc2            6993        7296     2441880    5  Extended

Error 27: Unrecognized command

grub>
<swap / Sol
           aris

Error 27: Unrecognized command

grub>

---

### Post by glennric on 2008-03-14
What is going on with your grub? How did you run grub?  Try
```
sudo grub
```
and then the command I gave you before inside grub.  

As to your grub stuff try
```
grub> device (hd0) /dev/sda
grub> device (hd1) /dev/sdc
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```

---

### Post by patchido on 2008-03-14
grub> find /boot/grub/stage1

Error 15: File not found

grub>

---

### Post by glennric on 2008-03-14
Are you currently running the live cd?

---

### Post by glennric on 2008-03-14
By the way, you don't actually need a linux partition on the first drive to install grub to it.  Grub can install the the MBR.  If you don't want to change the MBR then you will need the partition, but you also need to change the command in grub to
```
setup (hd0,1)
```
(at least that is what it seems like the numbering should be based on your fdisk output.)

---

### Post by patchido on 2008-03-14
> **glennric said:**
> Are you currently running the live cd?

yes i am... but i cant get it to work.. not even with what u told me... for some reason it changed sdc into sdb now...

---

### Post by glennric on 2008-03-14
What do you mean it changed sdc to sdb?  Do you mean the output of fdisk?  Did you reboot?  There is another way using the live cd to change things.  You could mount the partitions you want to be root and chroot to them.  Then try running grub from there.  I can walk you through it if you want.  It may be that you need to change some files in your /boot/grub directory.  We can do that with this method.

---

### Post by patchido on 2008-03-14
im still not able to make it work... and it is called sdb now.. dont know why....

---

### Post by patchido on 2008-03-16
anyone has any idea?

---

### Post by patchido on 2008-03-16
i need ubuntu back.. come on plz...

---

