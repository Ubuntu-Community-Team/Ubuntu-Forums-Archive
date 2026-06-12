---
title: "diskaccess"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jonl on 2007-07-18
Hi

I wonder if it's possible to mount a ntfs disk under ubuntu feisty fawn server edition, so that everyone in my network can access it? And if you would please tell me how?

thanks JonL

---

### Post by bodhi.zazen on 2007-07-18
Yes : 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]


Next you will need to decide how you want to share. NFS or Samba.

---

