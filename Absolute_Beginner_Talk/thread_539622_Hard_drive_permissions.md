---
title: "Hard drive permissions"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Zoiked on 2007-08-31
I have one hard drive in my computer with about 4 different partitions on it. Here they are layed out. 

1: Windows NTFS
2: Ubuntu EXT3
3: Ubuntu Swap
4: Media NTFS // hard drive for all my media, I share this drive between ubuntu and windows. 

Ubuntu auto mounts all of my hard drives but gives them only read only access. I have tried messing with the fstab and I can't do anything to help. 

fstab: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0220f497-add2-472c-8e6e-1cea49d1e349 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=F4488F50488F1092 /media/Media    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1,rw,auto
# /dev/sda1
UUID=D63866B438669373 /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1,rw,auto
# /dev/sda4
UUID=4011d4a8-d79c-40a1-8b79-cc6a636df2d7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Thanks.

---

### Post by LaRoza on 2007-08-31
Ubuntu will read NTFS but will not write to it, without the NTFS driver.

---

### Post by raijinsetsu on 2007-08-31
To get read/write permissions, you have to use ntfs-3g, which is not part of Ubuntu. If you search for ntfs-3g on the forums, you will find a howto.

---

### Post by diatribe on 2007-08-31
you may have to chown the mountpoints to your username in order to get read/write access

---

### Post by Zoiked on 2007-08-31
Ohh, I thought ntfs-3g was already installed on Ubuntu. :D Thanks.

---

### Post by raijinsetsu on 2007-08-31
I belive ntfs-3g hasn't been judged "stable" enough for the regular repositories. I think it's in "universe", but not sure.

---

### Post by LaRoza on 2007-08-31
If you need to share files, using FAT32 is an easier choice if you are willing to live with its limitations.

---

