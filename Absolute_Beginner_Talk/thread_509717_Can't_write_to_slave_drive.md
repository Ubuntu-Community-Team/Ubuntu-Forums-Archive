---
title: "Can't write to slave drive"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by babya on 2007-07-25
I just installed a spare internal hard drive, but it won't give me permission to write to it.  Says it's read-only.  

I logged into root to try to change permissions, but it wouldn't take.  Solution?

---

### Post by doomster on 2007-07-25
what format does the spare HD has? 
if its ntfs, you will have to install ntfs-3g and enable write support for ntfs drives from there

---

### Post by bodhi.zazen on 2007-07-25
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

