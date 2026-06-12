---
title: "Changing Mount Permissions"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Azslande on 2007-08-09
When I installed Ubuntu, I also had windows installed. So a friend of mine mounted my windows C drive so I could view it in Linux and share files between Linux and Windows if I would have to duel boot. The problem is, I can't get into my windows mount from the linux side. It says I do not have the permissions to view the content. The folder is mounted in the following.
```
mnt/windows_c
```

and my fstab file says the following.

```
/dev/hda1	/mnt/windows_c	ntfs	defaults	0	0
```

Anyone have any idea how to change the permissions so that not just root has access. I tried chmod on the windows_c folder, which did not change its permissions.

I am using Feisty.

---

### Post by bodhi.zazen on 2007-08-09
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

---

