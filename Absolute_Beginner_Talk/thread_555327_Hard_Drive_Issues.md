---
title: "Hard Drive Issues"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-09-20
I can't get my second hard drive to be recognized by Ubuntu.  It is showing in the BIOS as an automatically detected 120gb hard drive, but can't find it anywhere in ubuntu.  Help, please?

---

### Post by alienexplorers on 2007-09-20
Please post the output of :
> sudo fdisk -l (l = a small L)

---

### Post by soaklord on 2007-09-20
There is nothing on this disk that I need to recover so I am good with a format, preferably to FAT32 as I want this to have network access.  Here's the info, so ubuntu finds it in cli.

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Bothered on 2007-09-20
It doesn't look like it's formatted. You can use gparted to format it. gparted isn't installed by default, but you can install it with:

```
sudo apt-get install gparted
```

---

### Post by Pumalite on 2007-09-20
Click on the whole drive and make one big partition formatted to your liking. Ubuntu does not recognize 'unallocated' space.

---

### Post by soaklord on 2007-09-20
That's just it, there isn't any drive in the GUI to click on.  Gparted only shows my file system, etc. on my primary drive, the secondary drive doesn't show at all.  Is there a cli way to format, as the cli obviously sees it.

---

### Post by Bothered on 2007-09-20
Towards the top right of gparted there should be a box that says "/dev/sda". Click that and select "/dev/sdb" and then you can format your second drive.

---

### Post by soaklord on 2007-09-20
Ahh, will try as soon as I get home.  Thanks.

---

### Post by maniac_X on 2007-09-20
pic for your reference :)

[IMG]http://img229.imageshack.us/img229/2863/untitled1ho6.png[/IMG]

---

### Post by soaklord on 2007-09-20
Thanks for the help so far!!!  The drive is still not showing in my places menu, how do I mount the drive?

---

### Post by alienexplorers on 2007-09-20
Try this for mounting instructions
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Pumalite on 2007-09-20
sudo mkdir /media/harddrive
sudo mount -t ext3 /dev/xxx /media/harddrive
(replace xxx for real device and ext3 for real format)

---

### Post by soaklord on 2007-09-20
Thanks for the help!  I finally have it mounted and working.  YaY forum friends!!!  =)

---

### Post by Pumalite on 2007-09-20
Happy Ubuntuing!

---

### Post by soaklord on 2007-09-21
I thought this was solved, but I typed too soon.  The drive is visible, I was able to copy files to it in the GUI, but I can't rename, change any properties, etc.  I know that all hard drives are less than their listed capacity, but isn't it a bit much to lose 9GB?  The drive only shows in the GUI as an 111GB drive.  Suggestions?

Here's the fdisk:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32

---

### Post by Pumalite on 2007-09-21
120 GB ARE 111 GB if you do the maths.(1024=1 GB)
For permissions:

sudo chmod 777 /dev/xxx
(you substitute the xxx for what's appropriate to you)

---

### Post by soaklord on 2007-09-21
Still can't rename, etc.  Here's the message:

Sorry, couldn't rename "111.8 GB Volume: disk" to "kaosdrive111".

---

### Post by Bothered on 2007-09-22
I recommend you add a line to you /etc/fstab. Could you post the result of:

```
cat /etc/fstab
```

and also:

```
ls -l /dev/disk/by-uuid
```

and then we can advise you on how to do this.

---

### Post by soaklord on 2007-09-22
Here they are, and thanks again for the help.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc0a377c-7be8-42d4-856a-a0895ea7284c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1d4191ca-c9f2-441a-9541-842416d00666 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


total 0
lrwxrwxrwx 1 root root 10 2007-09-22 07:09 1d4191ca-c9f2-441a-9541-842416d00666 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-09-22 07:09 46F2-FD84 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-09-22 07:09 fc0a377c-7be8-42d4-856a-a0895ea7284c -> ../../sda1

---

### Post by soaklord on 2007-09-22
*soaklord trips, bumps thread accidently*:^o

---

### Post by Pumalite on 2007-09-22
Post:
blkid

---

### Post by soaklord on 2007-09-22
/dev/sda1: UUID="fc0a377c-7be8-42d4-856a-a0895ea7284c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1d4191ca-c9f2-441a-9541-842416d00666" TYPE="swap"

---

### Post by Pumalite on 2007-09-22
Now compare the UUID's to your fstab and change them if necessary.
(after backing up /etc/fstab)

---

