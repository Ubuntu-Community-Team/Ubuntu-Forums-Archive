---
title: "[SOLVED] second hard drive missing!"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by hj82 on 2008-02-20
I've just installed a new 250GB Maxtor SATA drive on a Dell Dimension 8400, and installed Ubuntu Gutsy on it, and kept XP on the original 160GB Maxtor SATA drive that came with the computer.

XP doesn't see the new drive with Ubuntu on it, and Ubuntu doesn't see the original drive with XP on it.  Both are see in the BIOS,  I ran fsdisk -l and got this:


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       18994   152497012+   7  HPFS/NTFS
/dev/sda3           18996       19452     3670852+  db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f05f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386   83  Linux
/dev/sdb2            1460       30401   232476615    5  Extended
/dev/sdb5            1460       30158   230524686   83  Linux
/dev/sdb6           30159       30401     1951866   82  Linux swap / Solaris
 
And this is what cat /etc/fstab returned:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2ffc3768-6020-4431-9682-b280c7c9520b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=629c6661-6a5f-494c-9c5d-ae61c5fa26bd /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D4-0A1B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=E4C89315C892E558 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=e2b2ff80-bc7b-4ded-9953-10b040352cf4 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec 0       0


It seems to see an extra cdrom drive - I only have two, scd0 and scd1.

Any suggestions??

---

### Post by Presto123 on 2008-02-20
XP will not see the Ubuntu drive unless you install a program on XP to read the file system. I don't remember where I saw it or what program it was, though.

Try using the command in Terminal:

```
sudo mount /dev/sda2
``` 

If it errors, post the output in code tags (located on top of reply screen as a # sign).

---

### Post by hj82 on 2008-02-21
Hello

Thanks for the reply.

I tried sudo mount /dev/sda2, but it failed and returned:
```
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()

```

I'll have a look for that XP program....

---

### Post by stoodleysnow on 2008-02-21
You may need to reinstall GRUB and re-jig the partition tables... :-k

---

### Post by hj82 on 2008-02-21
Problem fixed!

I installed Ext2IFS in XP, so that it can access the Linux side... that worked fine, and seems to have fixed the problem on both sides because Linux can see the XP drive now too.

Thanks for the suggestion, Presto123.

---

### Post by Presto123 on 2008-02-21
Very nice fix. Looks like you got a fix for others with that issue. ;)

---

