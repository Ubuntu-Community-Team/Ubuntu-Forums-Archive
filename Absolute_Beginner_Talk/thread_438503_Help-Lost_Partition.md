---
title: "Help-Lost Partition"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by priority1 on 2007-05-09
Before upgrade to Feisty I had a fat32 partition I could access. There is a folder in /media for the partition, and the entry in fstab is the same as it was before. When I try to mount it I get a message: special device /dev/hdb1 does not exist. The partition does have data on it and can access it from windows. Here's the output from fdisk & fstab. I've read alot of the posts and none come close to this problem.
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9885    79401231    7  HPFS/NTFS
/dev/sda2            9886       19457    76887090    f  W95 Ext'd (LBA)
/dev/sda5            9886       19457    76887058+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9971    80092026    c  W95 FAT32 (LBA)
/dev/sdb2            9972       30401   164103975    f  W95 Ext'd (LBA)
/dev/sdb5            9972       23904   111916791    7  HPFS/NTFS
/dev/sdb6           25243       30401    41439636    7  HPFS/NTFS
/dev/sdb7           23905       25114     9719293+  83  Linux
/dev/sdb8           25115       25242     1028128+  82  Linux swap / Solaris
The output for fstab                                                                                                                                                # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb7
UUID=716b5a74-7b12-4a2a-9988-f20ea46ef34f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=01C652BD940FD540 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=01C652BD96847EC0 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=01C6470CBBB7C380 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=398EB0206E51976D /media/hdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb8
UUID=6ee11d84-def5-46e0-8235-20c5782520e0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0                                                                                              Are there any other places that might effect the partition from showing up? Thanks

---

### Post by Mitlik on 2007-05-09
Is the drive an ide drive or a sata drive?
You refer to it as **h**db but your fdisk shows **s**db. Maybe this is the problem.
Also, make sure that there is a folder in the /media directory that you are trying to mount to. I had a similar problem, and I created a folder in media and mounted the drive and now it works spiffy.

\\Edit: Sorry, I missed that you said there was already a folder. Hopefully you are trying to mount the drive to that directory then. Also re-reading I noticed that your fstab uses hda and hdb for all your drives but still your output from fdisk -l clearly shows sda's and sdb's. sdb1 having fat32 on it. So I would still try it with sdb1.

---

### Post by priority1 on 2007-05-09
The drives are ide. I saw the entry you are looking at. I don't know why it says it's sda. This system was working fine and the drive was accessible with an icon on the desktop. While the upgrade process was going on the screen flashed a couple of times, during one of the flashes the icon disappeared and now cannot access it. I've been working on this since the upgrade, and with all the posts I've read I'm not any closer to finding an answer. Also  when I mount it (sudo mount -a) it says: special device /dev/hdb1 does not exist.

---

### Post by alienexplorers on 2007-05-09
Are you sure your drives are IDE.  An easy way to check is to look at the drive cable.  If it is a wide flat grey cable you have IDE drives.  If it is a narow cable you have SATA drives.  I would check this out before going any farther.

---

### Post by priority1 on 2007-05-10
The drives I put in this computer when I built it were ide. I don't think they made sata drives 6 years ago.? Looking at other posts it seems like Feisty is using UUID. The entry doesn't have a UUID, but I don't know if Edgy used that. Looks like the only way to fix this problem may be to do a clean install.

---

### Post by annda on 2007-05-10
have you tried mounting /dev/sdb1 to /media/hdb1 ? it looks like it is the only FAT partition. what output do you get?

---

### Post by Najand on 2007-05-10
It is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314)
You can just mount them as /dev/sd's or just use the released fix.

---

### Post by priority1 on 2007-05-10
annda and Najand thank you. I've added an entry into fstab and am able to access the partition. But it doesn't show up in the computer -file browser or desktop yet, but I'll work on that. I was going to use the FAT partition as storage.

---

### Post by Najand on 2007-05-10
To be able to see mounted partitions, you must mount them under a directory in /media.

---

### Post by priority1 on 2007-05-11
even before the upgrade to Feisty I had a folder in /media that has the name of the partition (hdb1) I've been trying to mount. I must have it mounted because I can see the contents of the partition in that folder. What else do I need to do? Is there something I'm missing? I would like to finish fixing the problem by seeing the icon in the computer-file browser and the desktop. Any ideas??

---

### Post by Najand on 2007-05-11
Add "user" to the option of your partition in your fstab.

---

