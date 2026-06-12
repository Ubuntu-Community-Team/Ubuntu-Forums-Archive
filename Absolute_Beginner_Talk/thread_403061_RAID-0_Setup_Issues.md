---
title: "RAID-0 Setup Issues"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by petersolson on 2007-04-06
Greetings all.  I am having extraordinary difficulty setting up a RAID-0 configuration with 2 320gb SATA (150) drives.  I am using a Silicon Image 3114 RAID PCI card as the controller (fakeraid).  In the card's BIOS, I have not created any RAID sets.

I have installed Feisty beta 64bit (2.6.20-12 kernel) on a SATA drive running off the motherboard's SATA controller.

I have run fdisk to create partitions on /dev/sdc and /dev/sdd.  When I run fdisk -l it reports as follows:

> Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect

This appears to be perfect.  However, when I run ls /dev/s*, it reports as follows:

> /dev/sda   /dev/sdb   /dev/sdb2  /dev/sdd        /dev/sequencer2  /dev/sg1  /dev/sg3       /dev/sndstat  /dev/stdin
/dev/sda1  /dev/sdb1  /dev/sdc   /dev/sequencer  /dev/sg0         /dev/sg2  /dev/snapshot  /dev/stderr   /dev/stdout

/dev/shm:

/dev/snd:
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer

The partitions /sdc1 and /sdd1 are nowhere to be seen.

Thus, when I run  mdadm --create --verbose /dev/md1 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1, I get the following:

> mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sdc1: No such file or directory
mdadm: Cannot open /dev/sdd1: No such file or directory
mdadm: create aborted


I have tried to create these partitions as type 83, and I have the same problem - mkfs cannot see them either.

Can anybody help with this problem?  Thanks in advance.

---

### Post by NICU on 2007-04-06
I had a slightly different problem using MDADM to create an array, I just needed to add "auto=yes" to my RAID creation string after --create.  Let me know if that helps.

---

### Post by petersolson on 2007-04-06
Thanks for the reply.  I gave that a shot, and tried several locations in the command line for auto=yes.  Unfortunately, none of them worked.  Oh well.

---

