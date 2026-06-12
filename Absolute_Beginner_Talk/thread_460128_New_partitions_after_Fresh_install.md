---
title: "New partitions after Fresh install"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-31
Well, I had to try 3 times but I don't know if I got it right.  So here are the new partitions.  I won't start updating until I am sure that this is ok.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1337    10739421   83  Linux
/dev/sda2            1338        4012    21486937+  83  Linux
/dev/sda3            4013        5592    12691350   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         256     2056288+   7  HPFS/NTFS
/dev/sdb2             257        7644    59344110    7  HPFS/NTFS
/dev/sdb3           10173       14589    35477922+   f  W95 Ext'd (LBA)
/dev/sdb4            7645       10172    20304530+  83  Linux
/dev/sdb5           10173       14589    35477891   83  Linux

Partition table entries are not in disk order

---

### Post by Inxsible on 2007-05-31
Looks great other than the fact that it doesnt show a boot flag on your sda1. Maybe it got erased while copy pasting.
 
I am on [EMAIL="XP@work"]XP@work[/EMAIL] right now, so I am not completely sure if Linux shows the boot flag on its drive.
 
Can you log in to Ubuntu ? If yes, you should be A OK !!

---

### Post by Inxsible on 2007-05-31
Your sda looks good.
 
In your sdb however, 
I notice that /dev/sdb3 is an Extended partition of FAT32 and then you have /dev/sdb5 as EXT3 ?
 
I am wondering how you have FAT32 and EXT3 under the same partition.
 
Maybe i am wrong or I just dont know enough ! :rolleyes:

---

### Post by Inxsible on 2007-05-31
Could you post the output of 
```
gksudo gedit /etc/fstab
```

---

### Post by ICUR2Ys on 2007-05-31
OK thanks, I booted up on ubuntu without a problem.  I hope that I have it right this time.  I am glad that I asked about the partitions.  I want the system to be correct so I won't have too many mysteries happening.

I really appreciate everyones input.

---

### Post by ICUR2Ys on 2007-05-31
OK here is the output.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bfae8937-c4ae-47a6-9646-542a05bb65b1 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=c57662a6-cd5d-44fe-85b0-104669bba44e /home           ext2    defaults        0       2
# /dev/sdb1
UUID=4A2C0C3D2C0C2693 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=88AC6CCBAC6CB57A /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=06825b54-be92-461d-b1d0-52fd74292211 /media/sdb4     reiserfs defaults        0       2
# /dev/sdb5
UUID=cf19ca5c-ad4e-48ec-90c1-d328c7e88025 /media/sdb5     reiserfs defaults        0       2
# /dev/sda3
UUID=1f8d1662-1403-43de-93d8-37fd8ce94962 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Inxsible on 2007-05-31
> **ICUR2Ys said:**
> OK here is the output.
 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=bfae8937-c4ae-47a6-9646-542a05bb65b1 / ext2 defaults,errors=remount-ro 0 1
# /dev/sda2
UUID=c57662a6-cd5d-44fe-85b0-104669bba44e /home ext2 defaults 0 2
# /dev/sdb1
UUID=4A2C0C3D2C0C2693 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb2
UUID=88AC6CCBAC6CB57A /media/sdb2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb4
UUID=06825b54-be92-461d-b1d0-52fd74292211 /media/sdb4 reiserfs defaults 0 2
# /dev/sdb5
UUID=cf19ca5c-ad4e-48ec-90c1-d328c7e88025 /media/sdb5 reiserfs defaults 0 2
# /dev/sda3
UUID=1f8d1662-1403-43de-93d8-37fd8ce94962 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
 
 
Was there any reason for you to go with the EXT2 filesystem as opposed to EXT3 ?
 
EXT3 is the newer version which offers journalling and its pretty stable. Also your sdb4 and sdb5 are in reiserfs filesystem. Any particular reason for that ?
And lastly....do you have 2 CD Drives?

---

### Post by ICUR2Ys on 2007-05-31
Yes my reason was total and complete ignorance. Should I redo it with all being ext3?

I  didn't touch the second drive, I only modified the first drive.  The system assigned every thing to the second driver before.

---

### Post by Inxsible on 2007-05-31
> **ICUR2Ys said:**
> Yes my reason was total and complete ignorance. Should I redo it with all being ext3?
 
Ok. This is what you wanna do.
 
On sda:
Re-install with the same partition sizes..but format it to EXT3. Swap never has any filesystem
 
On sdb :
1) Leave sdb1 and sdb2 AS IS. DO NOT CHANGE !
2) Delete sdb5, since sdb3 and sdb5 are of the same size ...i.e. you have only one Logical partition (sdb5) under the Extended Partition(sdb3)
3) Format sdb3 and sdb4 with EXT3
 
Of course, before changing anything on sdb3 and sdb4 and sdb5, make sure you BACKUP all the data on those three drives -- if any.
 
Good Luck

---

### Post by Inxsible on 2007-05-31
Of course, you can create multiple logical partitions under an Extended partition. So if you think that in the future you will need more partitions, then let the extended partition (sdb3) remain as is except - format it to EXT3
 
Do a google search on extended partitions or primary partitions or just partitions in general for more information. It'd be too much to explain on the forum :)

---

### Post by ICUR2Ys on 2007-05-31
Thank You, I just concerned about getting the first drive right.  I will completely reformat the second drive to linux there isn't anything on it that didn't copy before installing linux the first time.

---

### Post by Inxsible on 2007-05-31
> **ICUR2Ys said:**
> Thank You, I just concerned about getting the first drive right.  I will completely reformat the second drive to linux there isn't anything on it that didn't copy before installing linux the first time.

So you will no longer keep windows then?

Do you have no need for Windows ?

---

### Post by Inxsible on 2007-05-31
Here's some info on what primary and extended partitions are :

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by ICUR2Ys on 2007-06-01
I didn't have windows on this system.  The installer left NTSF on the second drive because there was data and media files there.  But I had copied those to an external before I loaded linux.

I still have a need for windows, so xp pro is the operating system on my other computer.  I have been updating the system and installing programs trying to get this system back to where it was before the fresh install.

The partitioning on this system is much cleaner now.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            1338        4012    21486937+  83  Linux
/dev/hda3            4013        4208     1574370   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux
dace@dace-desktop:~$ 

I thank you for all of your help.  My understanding is increased through this effort.  I read the wiki reference on partitions.  Thank you.

I really do appreciate your taking the time to help me.

---

### Post by Inxsible on 2007-06-01
No problem at all. Glad to see that you got it all fixed and the way you like it :)

---

