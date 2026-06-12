---
title: "MINT 14 installation issue..."
date: 2013-03-12
forum: Any Other OS
---

### Post by vadertater on 2013-03-12
I'm trying to install MINT 14 and it keeps stopping at the "Installation Type" menu. I believe it's asking me for me to choose the parition I want to put Mint in, but it only recognizes there is /sda/dev and then it won't give me anymore options. I just get stuck there and it tells me to find a root file system... which I can't do because I have no other options!!! here's a picture [http://i.imgur.com/ylzVL.png](http://i.imgur.com/ylzVL.png)

I did a bit of research and it might be a RAID issue with the parition... not sure what has been done to this laptop (not mine). It's a Dell Inspiron 14z. It has Windows 8 (barf) installed already. Brand new, so not a whole lot has been done to it.

Here is the input to sudo fdisk -lu:

mint@mint ~ $ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x77e78847

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 32.0 GB, 32017047552 bytes
256 heads, 63 sectors/track, 3877 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4c67664

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT



Any help/insight would be appreciated! Thanks

---

### Post by pqwoerituytrueiwoq on 2013-03-12
open gparted to create your partition ```
gksu gparted
``` then try to install to that partition(s)

---

### Post by tgalati4 on 2013-03-12
Are you trying to install on /dev/sdb (which is the 32GB drive)?  Try switching the cables around and reboot the Live CD.  Also, put some partitions on the 500GB drive.  Don't forget to put a swap partition that is at least the size of your RAM or slightly larger.

I assume that this is not a dual-boot machine.  There will be no other operating system on this system except Mint.

---

### Post by buzzingrobot on 2013-03-13
The installer's partitioning routine has recognized /dev/sda as the boot drive, but it has not recognized either drive as available for partitioning.  It should list both /dev/sda and /dev/sdb and allow you to edit their partitions as you wish. You might try running parted/gparted from the LiveCD and either wiping out the current partitions or wiping them out and creating new partitions.  The presence or non-presence of partitions on the drives should not effect their visibility to the installer.

---

### Post by vadertater on 2013-03-14
Ok, thanks for the explanations... I can kind of see what the output was saying now. 

I will not be able to get to this issue any time soon (maybe later today or tomorrow). But thanks for the very quick responses! I think I may have not completed the partition for some reason. I'll try to fix the partition and then try to re-install MINT 14 and see if the same issue comes up. At which point I'll use your ideas.

Thanks again! I'll let you know if it works out.

---

