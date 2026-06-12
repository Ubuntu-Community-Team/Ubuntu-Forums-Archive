---
title: "mounting problem"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Obor on 2006-12-28
this is my disk:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/hda2            1403        2804    11261565   83  Linux
/dev/hda3            2805        7138    34812855    b  W95 FAT32
/dev/hda4            7139        7296     1269135   82  Linux swap / Solaris

```

hda1 is my windows partition and hda3 i call a data partition. They both get auto-mounted when i log in. 

My problem is that when I log out of a session, login as user 2 and then logout user 2 and login back as user 1 my data and windows partitions are not mounted anymore.  I can mount them by sudo mount -a but i would like to know what is causing this. what should i change in my fstab? Or is it something else?

This is my fstab (i'm using edgy):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f6a0dc49-864b-47df-80a8-81f640f3a6a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=4559-C033  /media/data     vfat  iocharset=utf8,umask=000  0    0
# /dev/hda1
UUID=3070C9A870C9755E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=2b8e4c7a-e658-4491-bbe5-2befbbb178c5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by tzulberti on 2006-12-28
I think that the problem, is in the fstab file. 

UUID=3070C9A870C9755E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       

I think thath gid has something to do with the user id or groups id (Check it in google). It could be that user one doesn't has that permission, but user 2 does has it...

---

### Post by Obor on 2006-12-30
I got rid of the gid=46 and its still the same :( 
Any other ideas?

---

