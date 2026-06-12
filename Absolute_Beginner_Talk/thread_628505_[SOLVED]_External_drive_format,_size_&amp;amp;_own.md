---
title: "[SOLVED] External drive format, size &amp;amp; ownership problem"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by aridus on 2007-12-01
I have a 250 GB external USB drive. I wanted to change it from FAT to ext3 file system but I seem to have messed up using gparted. I thought I needed to add a disk label, and this added a partition, which I didn't want, and now the drive is only 232 GB and is owned by root (although it is ext3). I would greatly appreciate any help to:

(1) Return the drive to its full size. (2) Have it owned by me and not root.

I have tried to use fdisk and chown but can't seem what I need. 

With thanks to the more knowledgeable!

---

### Post by bingoUV on 2007-12-01
1. Size : The drive is still full size 250 GB. It is the difference between hard disk makers unit (1 GB = 1000 * 1000 * 1000 bytes) and file system's language (1GB = 1024 * 1024 * 1024 bytes). So  
250 GB in hard disk makers language =
 250 * 1000 * 1000 * 1000 / (1024 * 1024 * 1024) GB  in file system's language; which is very close to 232 GB.  

2. You will need to mount the hard disk somewhere. I am assuming it is /dev/sdb, but you can check in gparted : 
```

 sudo mkdir /media/TwoFiftyGB 
sudo mount /dev/sdb /media/TwoFiftyGB 
sudo chown -R <your-username> /media/TwoFiftyGB 
sudo chgrp  -R <your-groupname> /media/TwoFiftyGB 

```The  <your-groupname> is very likely your username. The chgrp step is optional, it won't matter very much.

---

### Post by aridus on 2007-12-01
Many thanks, now I understand the size and I have managed to format it to ext3 and establish myself as the owner. As it is an external drive (and will not necessarily always be connected) it seems I don't need to set a mount point - it is mounted automatically at boot if it is connected (as /media/disk)

My only remaining question is how could I have it automatically mounted with a given name (e.g. ext3backup) rather than 'disk' when it is connected. I tried to set up something in fstab but it really screwed everything up.

Thanks!

---

### Post by bingoUV on 2007-12-01
First you need to figure out the UUID of the device. Again assuming /dev/sdb.
```

sudo blkid /dev/sdb

```This will print some output like
```

/dev/sdb: UUID="72ef359a-b6bd-4e25-ac38-1de43a610b8d" SEC_TYPE="ext2" TYPE="ext3"

```Here, 72ef359a-b6bd-4e25-ac38-1de43a610b8d is the UUID of the disk. Now edit the /etc/fstab file, and add an entry like 
```

UUID=72ef359a-b6bd-4e25-ac38-1de43a610b8d /media/myFavoriteMountPointName ext3 user 1 2

```Now whenever you plug your drive, it will get mounted at 
/media/myFavoriteMountPointName.

---

### Post by aridus on 2007-12-01
Thank you - I think I am nearly there, but not quite. Here is the output of bikid:

martin@martin-laptop:~$ sudo blkid /dev/sdb
/dev/sdb: UUID="2a2a2b88-c229-4e26-829b-de4294fcfd8a" SEC_TYPE="ext2" TYPE="ext3" 

and I have added this to the end of fstab:

# External 250 GB USB drive
UUID=2a2a2b88-c229-4e26-829b-de4294fcfd8a /media/ext3backup ext3 user 1 2

and it does mount the drive into ext3backup, but only with a lot of output on the black screen on entry (and does not start properly) and something about not being able to resolve UUID... etc but then after a couple of Ctrl-Ds it boots up and ext3backup is mounted. 

Any idea what this final problem is?

With thanks! Martin

---

### Post by aridus on 2007-12-01
oops
One more question.
Max file size in ext3 is determined by the number of blocks (according to the entry on ext3 in wikipedia). I want to have the max file size as large as reasonably possible. With a 1KB block size for example the max file size is 16 GB, which could easily be exceeded using sbackup but with 2KB block size max file size is 256GB which is fine. 
Is block size the same as sectors?
And if so I think I can set this with fdisk, correct?
Thanks! M

---

### Post by aridus on 2007-12-01
OK, a log of the problem was produced and here it is:

Log of fsck -C -R -A -a 
Sat Dec  1 17:20:05 2007

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 86 files, 3712/44068 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda5: 128 files, 69052/264550 clusters
fsck.ext3: Unable to resolve 'UUID=2a2a2b88-c229-4e26-829b-de4294fcfd8a'

fsck died with exit status 8

Sat Dec  1 17:20:05 2007
----------------

---

### Post by bingoUV on 2007-12-01
The error is coming from fsck. When the last entry in fstab is 2, linux fscks the partition before mounting. I don't know why the UUID is not found at that time, but change the fstab entry to 
```

# External 250 GB USB drive
UUID=2a2a2b88-c229-4e26-829b-de4294fcfd8a /media/ext3backup ext3 user 1 0

```This will get rid of the error at the expense of no filesystem check before mounting.

***************************************************************

I don't know how you created your ext3 filesystem, but generally you do not need to worry about max file size unless your hard disk is bigger than 2TB. This is because while creating the filesystem, mkfs.ext3 takes the device size into consideration to decide the block size. If your disk is 250 GB, I think it would have created the file system with 4k block size. It keeps maximum file size greater than device size.

If you(unlikely) create the filesystem by some tool which intentionally keeps a small block size, you might run into file size problems. Check block size by 
```

sudo dumpe2fs /dev/sdb | grep "Block size"

```***************************************************************

---

### Post by aridus on 2007-12-01
Many thanks!
OK block size is 4096, that is fine.
However somewhere along the way I have lost the mounting and am now back with the drive being mounted but as 'disk' and not with my chosen name of 'ext3backup' even though that is still in fstab as discussed earlier.
If you want to give up on me that's fine!

---

### Post by bingoUV on 2007-12-02
If something is already mounted at the mountpoint 'ext3backup', your disk will now get mounted at another location. Try unmounting 'ext3backup', maybe it will help
```

sudo umount /media/ext3backup
sudo mount /media/ext3backup

```

---

### Post by aridus on 2007-12-02
thanks again! I am at the tearing my hair out stage now! Trying to mount gives me this:

mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Perhaps I should go through the whole process of formatting, setting up a partition etc? Curiously Nautilus indicates that about 12 GB is used although there is nothing in the volume (hidden or otherwise).

---

### Post by aridus on 2007-12-02
Some more information, the output of 
martin@martin-laptop:~$ dmesg | tail 
after I have tried sudo mount /dev/sdc /media/ext3backup

[   34.692000] [fglrx] max single LFB  = 37105664
[   34.692000] [fglrx] total      Inv  = 0
[   34.692000] [fglrx] free       Inv  = 0
[   34.692000] [fglrx] max single Inv  = 0
[   34.692000] [fglrx] total      TIM  = 0
[   46.844000] kjournald starting.  Commit interval 5 seconds
[   46.852000] EXT3 FS on sdc1, internal journal
[   46.852000] EXT3-fs: mounted filesystem with ordered data mode.
[  750.312000] EXT3-fs error (device sdc): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  750.312000] EXT3-fs: group descriptors corrupted!

---

### Post by bingoUV on 2007-12-02
Are you sure the disk you want is /dev/sdc ? Can you give the output of 
```

sudo fdisk -lu

```

---

### Post by aridus on 2007-12-02
Here you go

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   de  Dell Utility
/dev/sda2   *      176715    48403844    24113565    7  HPFS/NTFS
/dev/sda3       112985145   117210239     2112547+   5  Extended
/dev/sda4        48403845   112985144    32290650   83  Linux
/dev/sda5       115089660   117210239     1060290    b  W95 FAT32
/dev/sda6       112985271   115089659     1052194+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca0a1480

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f149

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   83  Linux

---

### Post by aridus on 2007-12-02
Hmm Looking at what I just posted. Does the problem seems to be that I have a partition sdc1? Could I get rid of this? Does its existence explain why there is 11.8 GB used but nothing in the drive? 

M

---

### Post by bingoUV on 2007-12-02
Instead of trying sudo mount /dev/sdc /media/ext3backup, try sudo mount /dev/sdc1 /media/ext3backup. You have created a partition(sdc1), instead of formatting the whole hard disk(sdc). After mounting in this manner, do
```

df -h

```

This should give you a better picture of how much space is used in each partition. You could also see this in gparted 
```

sudo gparted &

```

This will tell you if you have unallocated space after sdc1

---

### Post by aridus on 2007-12-02
Many thanks yet again!
Nothing like a spot of gardening to sort out problems, and now I have my 250 GB external USB drive formatted as ext3, mounted automatically to ext3backup, and with sbackup writing its archives there. 
The final problem was that I needed to use the UUID of the partition (sdb1, which is actually the whole drive) rather than of the drive (sdb). All is well and checking is also enabled at mounting also and that works fine!
Along the way I have learnt a number of things that I never thought I would learn... it has been an education!

Best, Martin

---

### Post by aridus on 2007-12-02
Hmmm I spoke too soon. Everything is working fine except that file checking, if enabled (=2) at the end of the fstab line does not work (it causes the same problem as before with fsck) and therefore I have it set to 0. Pity about this but otherwise all is well.

---

