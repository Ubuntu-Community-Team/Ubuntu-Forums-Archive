---
title: "Another Thread about mounting NTFS partitions"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by khanfahad on 2007-11-02
I've read through previous ones and got no help. Here's what I get for "sudo fdisk -l":

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x377edb7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32046   242267728+   7  HPFS/NTFS
/dev/sda2           32047       41345    70300409    f  W95 Ext'd (LBA)
/dev/sda5           32047       41075    68259208+  83  Linux
/dev/sda6           41076       41345     2041168+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1       38913   312568641    7  HPFS/NTFS

I can see the main HD from my windows partition both on desktop and in /media folder. But I can't access the other harddrive... any help would be appreciated... Thanks

---

### Post by khanfahad on 2007-11-02
Here's /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0dc2910f-6999-47ad-8f33-587941305c86 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5AAC0B06AC0ADC7F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
                /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=c9cf0326-b2dd-406e-aabd-86b95ee40c62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sdb /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0

---

### Post by lyndaj70 on 2007-11-02
What version of Ubuntu are you running?  

Try this tutorial and see if it helps: [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

Good luck!
~Lynda

---

### Post by khanfahad on 2007-11-02
it's the latest... I just installed it today... 7.10

---

### Post by khanfahad on 2007-11-02
oh and I've tried that link won't help...

---

### Post by louieb on 2007-11-02
Is there any data on sdb?
Can you see the data from widows?
If no then use GParted to delete the partition and add it back.
IF there is data on the drive then the fdisk message 
>  This doesn't look like a partition table
Probably you selected the wrong device.
 is bad news.
Get the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and run testdisk on it and see if that fixes it.

---

