---
title: "need help with fstab"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-11-16
i changed the mount point for my external hard drive. i need to know how to set it back to normal so i can mount it. any help would be great. thanks

this is what my fstab looks like. the hda is fine and i can access all windows files, but my external (sda1) is messed up somewhere?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/ntfsmount     ntfs-3g silent,umask=,locale=en_US.utf8 0 0 defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /dev/sda1	fat32	defaults	0	0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2006-11-16
> **huviduc said:**
> i changed the mount point for my external hard drive. i need to know how to set it back to normal so i can mount it. any help would be great. thanks

this is what my fstab looks like. the hda is fine and i can access all windows files, but my external (sda1) is messed up somewhere?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/ntfsmount     ntfs-3g silent,umask=,locale=en_US.utf8 0 0 defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /dev/sda1	fat32	defaults	0	0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Post the output of ```
sudo fdisk -l
``` With the external drive connected.

And what is your desired mount point?

---

### Post by bodhi.zazen on 2006-11-16
Try: ```
sudo mkdir /media/sda1
```

Change: > /dev/sda1 /dev/sda1 fat32 defaults 0 0

To: > /dev/sda1 /media/sda1 auto users,auto,umask=000 0 0

Then try to mount: ```
mount /media/sda1
```

---

### Post by huviduc on 2006-11-16
i dont care where its mounted, i jsut want it to work with both ubuntu and xp

this is the output
huviduc@huviduc-laptop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8485    68155731    7  HPFS/NTFS
/dev/hda2            8486        9598     8940172+  83  Linux
/dev/hda3            9599        9729     1052257+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    b  W95 FAT32


thanks

---

### Post by bodhi.zazen on 2006-11-16
My second post should work for you....

---

### Post by huviduc on 2006-11-16
> **bodhi.zazen said:**
> Try: ```
sudo mkdir /media/sda1
```

Change: 

To: 

Then try to mount: ```
mount /media/sda1
```

that worked. thank you VERY much, i have been trying to fix that for hours

---

### Post by bodhi.zazen on 2006-11-16
8)

See also [How to fstab](http://ubuntuforums.org/showthread.php?p=1653968#post1653968)

---

