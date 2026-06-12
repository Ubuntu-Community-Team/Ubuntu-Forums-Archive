---
title: "can't access large partition"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by vansterhant on 2007-12-29
So I've just installed ubuntu Gutsy 7.10 and I've tried numerous approaches to this problem.

 I have several ntfs partitions that I'm able to access on my primary HDD but my secondary HDD contains all of my data and is largely inaccesible. the first partition on the second HDD is accessible but the second partition is not.

I have tried unmounting and remounting the partition and disabling nautilus's preview functions. The strange thing about it is that it can read the hard drive information(eg. capacity but does not allow me to view the files within, prompting me with a "the folder contents could not be displayed" dialog box. I have checked the mounting/permissions options against those of the other drives and they are identical.

it has been a known problem for some people on windows based operating systems so I will post the irregular characteristics of the drive contents. the second partition of the second hard drive disk is roughly 360GB large. it contains dvd images and ridiculously huge files in the root of it such as half gig mp3 files and DVD images upwards of 4GB which are easily accessible in XP and Vista for me.

While I'm very happy with this distribution(no services has crashed so far which is a nice change from windows) and the driver support has improved quite a lot I just can't see myself using ubuntu for much longer if I can't access my media files through it.

---

### Post by Gone fishing on 2007-12-29
This is odd I wonder it there is a problem with errors on the drive have you tried booting into XP and chkdsk?

On my system I use a large ext3 partition to store stuff and access it through Windows and Ubuntu (there is a good ext3 driver for Windows)

---

### Post by vansterhant on 2007-12-29
yup the drive is fine. this is why it seems so odd to me. there doesn't seem to be a reason for why one particular partition shouldn't be accessible.

---

### Post by Moop on 2007-12-29
Sometimes Ubuntu complains about sata drives not being shut down correctly in windows. 

If it's a sata hdd and not your main windows hdd try booting into windows and using the safely add/remove hardware thing to shutdown that hdd.

---

### Post by hyper_ch on 2007-12-29
please paste the output of:

```

sudo fdisk -l

```

and

```

cat /etc/fstab

```

---

### Post by vansterhant on 2007-12-29
it's possibly a hardware conflict going on as well. in /media/ it seems to have mounted it under two names, "Storage", the drive name I assigned it and /sdb2 refering to physical location. It is able to read the hard drive capacity from the properties window. but something strange happens. The desktop shortcut to /media/storage/ will show the properties window as will navigating to /media/ and opening the properties window for sdb2. However, trying to open the properties window for storage from the /media/ folder instead of the desktop results in a misreporting of properties data, the relevant ones being:

contents: nothing
volume: /
free space: 15.1GB(where 97GB is actually free and it does not specify the size of the drive)

Does ubuntu have another folder called storage in the /media/ folder? this could be the cause.


anyway, here's the output from the terminal:

root@BOB:~# sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d6a8d6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20480000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2550        6375    30720000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            6376        8806    19527007+  83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c980763

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1403    11264000    7  HPFS/NTFS
/dev/sdb2            1403       48642   379445248    7  HPFS/NTFS
root@BOB:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2473d3e7-1897-44d3-8f55-1aac82fbd963 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3814A9C414A9860A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=A0EA42B1EA42840E /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=10706AE0706ACC52 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=4A1019931019875B /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
root@BOB:~#

---

### Post by hyper_ch on 2007-12-29
I think the problem is this:


Device Boot Start End Blocks Id System
/dev/sda1 1 2550 20480000 7 HPFS/NTFS
**Partition 1 does not end on cylinder boundary.**
/dev/sda2 * 2550 6375 30720000 7 HPFS/NTFS
**Partition 2 does not end on cylinder boundary.**
/dev/sda3 6376 8806 19527007+ 83 Linux

It seems to me the partition table isn't completly correct and that this results in being unable to mount the drive.

---

### Post by vansterhant on 2007-12-29
that's the first hard disk drive and those partitions mount properly. it's the sdb2 that I'm having trouble with.

---

### Post by Furat on 2007-12-29
try to mount the partition  manually 
```
mount /dev/sdb2 /mnt 
```
then try to access the /mnt in terminal

---

### Post by vansterhant on 2007-12-30
yes I can access it now in /mnt. Now I just need to figure out why it won't mount in /media/sdb2.

---

