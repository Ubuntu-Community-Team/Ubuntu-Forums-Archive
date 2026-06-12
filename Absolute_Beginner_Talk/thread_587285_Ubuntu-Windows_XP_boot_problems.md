---
title: "Ubuntu-Windows XP boot problems"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Jeeverz on 2007-10-22
I am having this problem of not being able to boot ubuntu which i have installed on my Slave HD

I even tried disabling my master drive and trying my slave to boot but it said no OS present

I would really like your help

<3 Jeev

---

### Post by arkara on 2007-10-22
how did you actually install your ubuntu copy during the instalation did you get a mesage about grub or something?
does grub even apear?
got you get an error msg?

---

### Post by Sef on 2007-10-22
> I am having this problem of not being able to boot ubuntu which i have installed on my Slave HD

I even tried disabling my master drive and trying my slave to boot but it said no OS present


Using the Live CD, open the Terminal.  (Applications > Accessories > Terminal)

then type or paste in this command:

sudo fdisk -l (that's l as in lucky)

next copy and paste the results here.

---

### Post by Jeeverz on 2007-10-22
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbd519ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   f  W95 Ext'd (LBA)
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris


thanx alot man ! really appreciate it

---

### Post by ajgreeny on 2007-10-22
Now let's see your /boot/grub/menu.lst file (mainly the menu bit at the bottom) and see if it points to the right partition.  I assume you can still boot into windows.

---

### Post by Jeeverz on 2007-10-22
Yeah hope you may see whats the reason i am not able to boot Ubuntu 

I keep gettin Error 21

The hard drives are Primary Master and Primary Slave

---

### Post by Jeeverz on 2007-10-22
> **ajgreeny said:**
> Now let's see your /boot/grub/menu.lst file (mainly the menu bit at the bottom) and see if it points to the right partition.  I assume you can still boot into windows.


would you be kind enough to give me a rough explanation on where to find that ?

---

### Post by logos34 on 2007-10-22
you'll have to boot the live cd, mount /dev/sdb1, and go to /boot/grub/menu.lst.  Copy and post it. 

You could also try this:

-boot to the grub menu screen, highlight the ubuntu kernel and press 'e' to edit.  Hit 'e' again on the 'root' line and change from (hd0,0) to (hd1,0) or vice-versa. If it works go to menu,lst and make the change permanent.

---

