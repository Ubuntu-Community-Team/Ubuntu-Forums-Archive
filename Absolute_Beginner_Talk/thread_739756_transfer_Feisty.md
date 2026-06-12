---
title: "transfer Feisty"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-03-30
Can somebody please help me out here, I'm still fairly new to my Feisty. I'm on a dual boot system with WinXP and Feisty on seperate disks. I've freed up a partition on Win disk & I'd like to transfer Feisty, as it is (I've added a lot of software and absolutely do not want a new install) here. I've made an image („Acronis“) of Ubuntu but this obviously holds old info on grub loader. How do I go about this please?

---

### Post by Inxsible on 2008-03-30
You can use the shell comand dd to create a bit by bit copy on your other drive.
Type in ```
man dd
``` in a terminal to get more info on how to use the command

---

### Post by c-ron on 2008-03-30
Hi. First off, I don't believe this belongs in the Absolute Beginner Talk forum. However, if you really want to do this, check out this post:

HowTo: Transfer your bootable Ubuntu installation between hard drives
[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

---

### Post by stoppage on 2008-03-30
Thank you both for your help. Ive just spent the last twelve hours trying to get this transfer right, followed instructions on supplied link but used an Image instead of dd. Cloned Feisty from hda (80GB) to larger sda ( 320GB)....precisely from hda5 to sda7 for dual boot with Windoze where it now sits sulking (recognised by live cd as disk) refusing to mount and with an identical Fstab to the other disk. Windowze was still booting up to the grub part of instructions on link. Dual boot menu did come up.....booting Linux rendered....Error 17..cannot mount selected partition.
Booting XP....selected disk does not exist. I resurrected XP with the help of Super Grub Disk but no sign of cloned Feisty although I can still boot it from its other disk. Im missing something here and I dont know what it is. If it helps, fdisk output using live disk...


ubuntu@ubuntu:~$ sudo fdisk -ls 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       12749   102406311    7  HPFS/NTFS 
/dev/sda2           12750       28368   125459617+   5  Extended 
/dev/sda5           12750       22311    76806733+   7  HPFS/NTFS 
/dev/sda6           22312       25499    25607578+   7  HPFS/NTFS 
/dev/sda7           25500       28049    20482843+  83  Linux 
/dev/sda8           28050       28368     2562336   82  Linux swap / Solaris 

Disk /dev/sdb: 1014 MB, 1014497280 bytes 
65 heads, 32 sectors/track, 952 cylinders 
Units = cylinders of 2080 * 512 = 1064960 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1         953      990704    6  FAT16 
Partition 1 has different physical/logical endings: 
     phys=(967, 64, 32) logical=(952, 39, 32) 
ubuntu@ubuntu:~$ 

Any ideas please....

---

