---
title: "How can I change my permissions on mounted drives?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by sarc on 2006-11-22
I want to allow read/write on all drives to users, including Windows XP, so I edited fstab.  My original file was:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8f3801a0-a3b1-4341-a6ca-8659796711f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1470-C70A  /media/D        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=C41A-9E7B  /media/E        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=349D-7DB0  /media/F        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=04A2-35FE  /media/Win98    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=05B4B59970DDA36F /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=b317dfcc-0283-4614-b467-a2802dd2e7ce none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Following advice to this forum I changed it to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8f3801a0-a3b1-4341-a6ca-8659796711f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1470-C70A  /media/D        vfat    rw,umask=000 0       1
# /dev/sda7
UUID=C41A-9E7B  /media/E        vfat    rw,umask=000 0       1
# /dev/sda8
UUID=349D-7DB0  /media/F        vfat    rw,umask=000 0       1
# /dev/sda2
UUID=04A2-35FE  /media/Win98    vfat    rw,umask=000 0       1
# /dev/sda1
UUID=05B4B59970DDA36F /media/WinXP    ntfs    defaults,umask=0222 0       1
# /dev/sda6
UUID=b317dfcc-0283-4614-b467-a2802dd2e7ce none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Still no change.. Permissions on the properties tab are still given as Read Only - Owner: root.  Any help appreciated.

---

### Post by taurus on 2006-11-22
First, change the last value from 1 back to 0 for all your vfat drives (and ntfs too)!  And if you want to be able to write to NTFS, then you need to install ntfs-3g!  There are a few threads here that show you how to install it.  As of right now, you can read and write to vfat but can only read from ntfs.  

```
UUID=1470-C70A /media/D vfat defaults,umask=000 0 0
```

---

### Post by sarc on 2006-11-23
??

I followed your suggestion but absolutely no change... am I changing the wrong fstab (is there more than one??)

My current fstab in /etc/

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8f3801a0-a3b1-4341-a6ca-8659796711f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1470-C70A  /media/D        vfat    defaults,umask=000 0       0
# /dev/sda7
UUID=C41A-9E7B  /media/E        vfat    defaults,umask=000 0       0
# /dev/sda8
UUID=349D-7DB0  /media/F        vfat    defaults,umask=000 0       0
# /dev/sda2
UUID=04A2-35FE  /media/Win98    vfat    defaults,umask=000 0       0
# /dev/sda1
UUID=05B4B59970DDA36F /media/WinXP    ntfs    defaults,umask=0222 0       0
# /dev/sda6
UUID=b317dfcc-0283-4614-b467-a2802dd2e7ce none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

:confused:

---

### Post by taurus on 2006-11-23
Did you reboot???

---

### Post by sarc on 2006-11-23
Yes several times.

Oh one thing comes in mind.  I changed the password on the user "Root" to be able to log in as root (now I know I should leave that user alone, but too late..).  Don't know if this has any consequence (does not seem to afect the system in any way).

---

### Post by taurus on 2006-11-23
Doesn't really matter if you give root a password.  Just be real careful when you log in as root.  If you need to run something, think twice before you hit the return key...

In the meantime, what are the output of these commands from a terminal (running as a regular user)?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sarc on 2006-11-23
Thanks for reply here it is:

super@RFNB:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1960    15735667    7  HPFS/NTFS
/dev/sda2            3872        4177     2457945    c  W95 FAT32 (LBA)
/dev/sda3            4178        9729    44596440    f  W95 Ext'd (LBA)
/dev/sda4            1961        3871    15350107+  83  Linux
/dev/sda5            4178        6089    15358108+   b  W95 FAT32
/dev/sda6            6090        6395     2457913+  82  Linux swap / Solaris
/dev/sda7            6396        8001    12900163+   b  W95 FAT32
/dev/sda8            8002        9729    13880128+   b  W95 FAT32

Partition table entries are not in disk order
super@RFNB:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8f3801a0-a3b1-4341-a6ca-8659796711f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1470-C70A  /media/D        vfat    defaults,umask=000 0       0
# /dev/sda7
UUID=C41A-9E7B  /media/E        vfat    defaults,umask=000 0       0
# /dev/sda8
UUID=349D-7DB0  /media/F        vfat    defaults,umask=000 0       0
# /dev/sda2
UUID=04A2-35FE  /media/Win98    vfat    defaults,umask=000 0       0
# /dev/sda1
UUID=05B4B59970DDA36F /media/WinXP    ntfs    defaults,umask=0222 0       0
# /dev/sda6
UUID=b317dfcc-0283-4614-b467-a2802dd2e7ce none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

