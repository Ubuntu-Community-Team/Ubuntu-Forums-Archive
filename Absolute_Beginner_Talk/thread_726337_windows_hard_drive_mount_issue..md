---
title: "windows hard drive mount issue."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Patrick-Ruff on 2008-03-16
Hey all, I'm not a noob but this is a noob question.  I have my linux install on a 40GB hard dive and then I have my windows install on another.  I can't access my windows install as it says it couldn't identify the permissions.

what can I do in this situation? the windows hard drive isn't corrupted.

---

### Post by diablo75 on 2008-03-16
You have to tell Ubuntu that on boot you want it to mount your NTFS partition as a drive.  Here's a guide:

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by drubin on 2008-03-16
Install  NTFS Configuration Tool. From the application manager.

---

### Post by drubin on 2008-03-16
> **diablo75 said:**
> You have to tell Ubuntu that on boot you want it to mount your NTFS partition as a drive.  Here's a guide:

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

Not sure if this is needed, To get my ntfs support and mounting the drive at boot time, i only installed the  NTFS Configuration Tool, worked first time takes all the hard work of editing the fstab....

---

### Post by Patrick-Ruff on 2008-03-16
ok thanks I'll try rubinboy's first since it's faster, then I'll try yours diablo if it doesn't work :).

I'll let you guys know how it turns out

---

### Post by deadrodentyping on 2008-03-16
I'm having the same issue. The owner is listed as "unknown", although the partition does show up in "Computer".

This is the result of an fdisk -l :
max@max-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15000330240 bytes
255 heads, 63 sectors/track, 1823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb04aa912

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1741    13984551   83  Linux
/dev/hda2            1742        1823      658665    5  Extended
/dev/hda5            1742        1823      658633+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x976b4d08

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1             514        4595    32788665    7  HPFS/NTFS
/dev/hdb2            4596        4865     2168775    5  Extended
/dev/hdb3               1         513     4120641   83  Linux
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris
/dev/hdb6            4596        4660      522049+  83  Linux
-----------------------------------------------------------------------------------------------------------
Here's my current /etc/fstab file: 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ec0d8e55-73f9-41b2-bc1a-4f0ef6ead55b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=16e8a336-36bf-4eaf-aeaa-dfe4a0a0009d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/hdb1       /media/hdb1     ntfs-3g
defaults,nls=utf8,umask=0
----------------------------------------------------------------------------------------------------------------
I changed umask to 0 (according to the man page, 0 is the default for all users);
I deleted uid because I didn't understand how to use it.

The ntfs-3g driver is installed, and I'm running ubuntu 7.10 with the latest updates. (3/15/2008).
TIA.

---

