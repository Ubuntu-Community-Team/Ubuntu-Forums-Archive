---
title: "File written to FAT32 invisible"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by ylu on 2006-04-09
I'm a beginner for Linux.
I have mounted my FAT32 partitions as follows:
/dev/hda1       /media/hda1     vfat    auto,user,utf8,umask=0        0       0
/dev/hda5       /media/hda5     vfat    auto,user,utf8,umask=0        0       0

When I wrote something on these partitions from Linux, it's all Ok.
But it became totally invisible from Windows.
I want to share files between 2 systems but it doesn't seem to work like this.

Someone can help me to point out why Windows can not show what is done  under Linux on the FAT32 partitions?

Lots of thanks.

---

### Post by christhemonkey on 2006-04-09
I have this in my fstab, and it allways has worked fine:
```
/dev/hda1        /media/hda1     vfat      auto,user,fmask=0111,dmask=0000         0     0
```

---

### Post by nanotube on 2006-04-09
[QUOTE=ylu]I'm a beginner for Linux.
I have mounted my FAT32 partitions as follows:
/dev/hda1       /media/hda1     vfat    auto,user,utf8,umask=0        0       0
/dev/hda5       /media/hda5     vfat    auto,user,utf8,umask=0        0       0

When I wrote something on these partitions from Linux, it's all Ok.
But it became totally invisible from Windows.
I want to share files between 2 systems but it doesn't seem to work like this.

Someone can help me to point out why Windows can not show what is done  under Linux on the FAT32 partitions?

Lots of thanks.[/QUOTE]

umask is supposed to be "umask=000" not just one 0. maybe that will help.

---

