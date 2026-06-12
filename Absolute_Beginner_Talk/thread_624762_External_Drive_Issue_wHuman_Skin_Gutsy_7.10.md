---
title: "External Drive Issue w/Human Skin Gutsy 7.10"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Lorac1949 on 2007-11-27
Was using Crux skin and could see my FreeAgent external drive just fine.  Even opened and saved files to it.  [It's space is shared with XP Pro, too.]  However, in order to solve a program crash in OpenOffice v2.3, I switched to the Human skin.  OO is working fine now, but when I try to open the external drive, I get:

"The folder contents could not be displayed.  Sorry, couldn't display all the contents of 'FreeAgent Drive.'"

What do I need to do so that I can see and access the external drive again?

---

### Post by taurus on 2007-11-27
Is it mounted?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
mount
```

---

### Post by Lorac1949 on 2007-11-27
Here's the first one:

carol@carol-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11       23309   187149217+   7  HPFS/NTFS
/dev/sda3           23310       30009    53817750    f  W95 Ext'd (LBA)
/dev/sda4           30010       30401     3148740   db  CP/M / CTOS / ...
/dev/sda5           29684       30009     2618563+  dd  Unknown
/dev/sda6           23310       29388    48829504+  83  Linux
/dev/sda7           29389       29683     2369556   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

and here's the second:

carol@carol-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /media/sda4 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda5 on /media/sda5 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

Does "mounted" mean that the USB cable is plugged in?  Before I changed the skin, I could see the external drive.  I moved files on and off of it.

---

### Post by Lorac1949 on 2007-11-28
Downloaded and installed latest batch of updates and the external drive issue has been resolved.

---

