---
title: "ext3 to ext2"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-17
I just formatted an external drive to ext3.  No problem.

I have started copying data to that drive.   The copy fails about 10% into the process with an I/O error message.

If I then look at the drive with gparted I find that the file system has changed from ext3 to ext2.

Any idea why this has happened?  I formatted again and the same thing happened ....

---

### Post by HermanAB on 2007-09-18
Ext3 is Ext2 with an added journal.  The journal mechanism was developed by Dr Tweedie and provides robustness to Ext2.  So some older utilities may identify Ext3 as Ext2.

'Hope that helps!

H.

---

### Post by expatCM on 2007-09-18
but why the change ......   formatted with gparted ....  copy started .....  failed ..... gparted shows the changed file system......

---

### Post by expatCM on 2007-09-18
Well ... it failed yet again .... sadly this time it is the source drive which is affected.  There was an error message which said look at dmesg | tail,  so I did ....


dmesg | tail
[  174.785439] sdd: Mode Sense: 00 38 00 00
[  174.785441] sdd: assuming drive cache: write through
[  174.786429] SCSI device sdd: 1465149168 512-byte hdwr sectors (750156 MB)
[  174.787178] sdd: Write Protect is off
[  174.787182] sdd: Mode Sense: 00 38 00 00
[  174.787184] sdd: assuming drive cache: write through
[  174.787188]  sdd: sdd1
[  174.799505] sd 4:0:0:0: Attached scsi disk sdd
[  174.799557] sd 4:0:0:0: Attached scsi generic sg5 type 0
[  175.152068] EXT2-fs: corrupt root inode, run e2fsck

The man file says do not run (e2fsck) on a mounted system which is handy since the drive will not mount.  But what command should I use to do this since I presumably do not now know the name of the device or is it safe to assume sdd1?

---

### Post by splintercellguy on 2007-09-18
fsck /dev/sdd1

---

### Post by expatCM on 2007-09-18
$ fsck /dev/sdd1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by splintercellguy on 2007-09-18
Try fsck with no param then.

---

### Post by expatCM on 2007-09-18
sorry ....  I do not understand.  Without what parameter?  If I just enter the command it will ask to check all the drives but since they are mounted this is not a good idea?

---

### Post by splintercellguy on 2007-09-18
Can you show me the output of sudo fdisk -l? I just want to see what devices you've got, so I can give you the proper paramter.

---

### Post by expatCM on 2007-09-18
sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        2805     2048287+  82  Linux swap / Solaris
/dev/sda3            2806        9052    50179027+  83  Linux
/dev/sda4            9053        9729     5438002+   f  W95 Ext'd (LBA)
/dev/sda5            9053        9729     5437971   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12493   100349991   83  Linux
/dev/sdb2           12494       24321    95008410    f  W95 Ext'd (LBA)
/dev/sdb5           12494       19946    59866191   83  Linux
/dev/sdb6           19947       20711     6144831    b  W95 FAT32
/dev/sdb7           20712       24321    28997293+   b  W95 FAT32

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9023    72477216    c  W95 FAT32 (LBA)
/dev/sdc2            9024       24321   122881185    f  W95 Ext'd (LBA)
/dev/sdc5            9024       24321   122881153+  83  Linux

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   83  Linux


Please don't worry about the drive now showing as sde1, I powered off the drive to see what would happen and it changed from sdd to sde on return.  Still cannot mount it of course :)

---

### Post by expatCM on 2007-09-18
hmmm .....  this looks like a hard question then .....

---

### Post by expatCM on 2007-09-18
any ideas anyone ?

---

### Post by expatCM on 2007-09-28
In case anyone finds this thread .....  it seems that the problem is caused by reading or writing large volumes of data to the drive (there are lots of related obscure threads on google sort of hard to understand).  Break the copy or delete down into small volumes of data and the problem does not appear.

If you are lucky fsck /dev/drivename will work and fix the problem but not every time.  From my experience if this does not solve the problem first time round then you are toast.

---

