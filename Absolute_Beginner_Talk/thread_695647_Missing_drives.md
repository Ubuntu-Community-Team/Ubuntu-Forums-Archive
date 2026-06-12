---
title: "Missing drives?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-13
Previously on my desktop it showed my various disk drives & their partitions, as well as a drive for my flash drive. After installing some various software packages, its no longer visible either in "Computer" on places or located on my desktop. Um, where did they go? And how do I get them back?

---

### Post by jan quark on 2008-02-13
let's see if your partitions are still there

please run these commands in terminal and post the output here
thank you


```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by jan quark on 2008-02-13
forgot something


you can also run
this command

```
gksudo gconf-editor
```

navigate to 
apps > nautilus > desktop 
and check the boxes for these devices you want to be displayed on desktop

---

### Post by spacefreak86 on 2008-02-13
Mount:

bdizzle86@MINE:~$ mount
/dev/sdb4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,user=bdizzle86)
/dev/sdc1 on /media/PublicZone type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)


bdizzle86@MINE:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef21ef21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4604    36981598+   7  HPFS/NTFS
/dev/sda2            4605        9729    41166562+   f  W95 Ext'd (LBA)
/dev/sda5            4605        9729    41166531    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22c742f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13336   107121388+   7  HPFS/NTFS
/dev/sdb2           26666       38913    98382060    f  W95 Ext'd (LBA)
/dev/sdb3           13337       13398      498015   82  Linux swap / Solaris
/dev/sdb4           13399       26665   106567177+  83  Linux
/dev/sdb5           26666       38913    98382028+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 462 MB, 462946304 bytes
16 heads, 32 sectors/track, 1766 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x142a43af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1766      452080    6  FAT16

bdizzle86@MINE:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=5207e63c-168c-4806-82fa-927b36fa67cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4C4416CB4416B822 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=1C18AC6218AC3CA0 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=CCB82D39B82D2404 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=A2D031B9D031950F /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=ecc4323d-1024-47e5-8ba0-2b9176cb9e9a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by spacefreak86 on 2008-02-13
And somehow in a wierd case of "what did I do right?" after restarting the computer and uninstalling one or two programs related to the desktop management, the drives are back again. Yay!

Now I just have to figure out how to get LaTeX, GSView, Ghostscript, and the actual TeX system on here. Right now I'm having to use Windows TeXniCenter and MikTeX on Windows for compiling, though I did find a cool program by the name of TeXMaker. Now I just have to figure out where to get the TeX libraries from to actually be able to use it.

---

