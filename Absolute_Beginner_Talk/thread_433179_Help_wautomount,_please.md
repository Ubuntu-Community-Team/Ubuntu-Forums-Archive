---
title: "Help w/automount, please"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by gspaulding on 2007-05-04
I have 2 hd's. One w/xppro (sda) and the second w/vista & feisty (sdb).  I select the boot disk in the bios options so if want xp it just boots from that hd.  If i want vista or ubuntu, I select that hd and choose from the grub menu.  I want my sdb5 (fat32) partition to automount to use as a shared drive w/windows.  I've looked at many threads and can't make sense of just what I have to do.

OUTPUT FROM fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16128   129548128+   7  HPFS/NTFS
/dev/sdb2           16129       20251    33117997+   f  W95 Ext'd (LBA)
/dev/sdb3           20252       30401    81529875   83  Linux
/dev/sdb5           16129       19814    29607763+   b  W95 FAT32
/dev/sdb6           19815       20251     3510171   82  Linux swap / Solaris

CONTENTS OF FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fbb0c939-b1e3-4622-af1b-fdb518d061dd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=f32bc96c-658d-4433-afee-a34e8549ba01 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What do I need to add to fstab to automount sdb5 at startup?
Do I have to create a folder or something for a mount point?  I don't get that part.
Please explain the steps.  I thank you in advance for your help.
Gary

---

### Post by taurus on 2007-05-04
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
dev/sdb5   /media/sdb5   vfat   iocharset=utf8,umask=000   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb5
sudo mount -a
df -h
```

---

### Post by gspaulding on 2007-05-04
Thanks, taurus.  That did the trick.  I'll search around to figure out how and why that worked.  Now, if I could  get ubuntu to work with my canon mf4150 multifunction laser printer, I'd be in hog heaven.  I'm loving feisty, so far.

I really appreciate your prompt and thorough help.

---

