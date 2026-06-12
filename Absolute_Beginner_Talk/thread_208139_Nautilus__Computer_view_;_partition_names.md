---
title: "Nautilus : Computer view ; partition names"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-07-03
In the "Computer" view of Nautilus, all of the ntfs partitions are labeled with the names they were given in Windows. And Fat32 partitions are labeled as "<size> Volume: <mount point>". Can it be changed so they are labeled with the names that are specified by the mounting points in /etc/fstab?

NTFS exa: 
```
/dev/hda1       /media/Win[C]   ntfs    noauto,nls=utf8,umask=007,gid=46 0       1
```
Under "Computer", that drive will show up as "Windows", instead of "Win[C]"

Fat exa:
```
/dev/hdb7       /media/Fat[K]   vfat    defaults,utf8,umask=007,gid=46 0       1
```
... labeled as "30.2 GB Volume: Fat[K]"

---

