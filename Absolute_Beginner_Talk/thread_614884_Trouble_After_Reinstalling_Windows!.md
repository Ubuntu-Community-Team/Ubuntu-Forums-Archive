---
title: "Trouble After Reinstalling Windows!"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Nischal on 2007-11-16
I hv both windows xp and ubuntu on my laptop.As usual, xp crashed and I had to reinstall windows.
After that, I tried to install grub(using liveCD) as explained in many of the threads in this forum
The problem is this:
   The grub works fine.But when ubuntu is selected I get the following:
Error   15:File not found
press any key to continue...


PS:I actually first reinstalled grub in the wrong partition(hd0,0).I realized the mistake and reinstalled it in the correct partition(hd0,5).Is this causing problems:confused:



p;z help...

---

### Post by bumanie on 2007-11-16
When windoze is  installed after linux, windoze does not recognise grub and just overwrites everything with its mbr.
From terminal via live cd, please post output of 'sudo grub' --> enter 'find /boot/grub/stage1' --> enter (without the quotation marks)

---

### Post by Inxsible on 2007-11-16
Also post ```
sudo fdisk -l
``` -l is lowercase L, just to make sure you didnt overwrite your Linux partitions during the Windows Install.

---

### Post by Nischal on 2007-11-16
@Bumanie

Output of 'sudo grub'-->'find /boot/grub/stage1':

  (hd0, 5)

---

### Post by Nischal on 2007-11-16
@inxsible

Output of 'sudo fdisk - l '(-l with lowercase L):

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff02ff02

     Device Boot                Start            End               Blocks       Id      System
/dev/sda1    *                        1         1216         9767488+       7       HPFS/NTFS
/dev/sda2                       1217          4864       29302560          f       W95  Ext'd (LBA)
/dev/sda5                       1217          1338           979933+      82      Linux swap / Solaris
/dev/sda6                       1339          2554         9767488+      83      Linux
/dev/sda7                       2555          3040         3903763+      83      Linux
/dev/sda8                       3041          4864       14651248+        b      W95  FAT32

---

