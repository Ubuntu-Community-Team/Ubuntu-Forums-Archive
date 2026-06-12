---
title: "Mounting a phantom partition"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-04-15
I've got 2 HDs, the first of which is 40G and mainly filled with Ubuntu and openSUSE. The other HD is 80G, NTFS, filled with MP3s that I want to transfer over to my ext3 drive so I can delete etc. 

So I used the gparted livecd to resize the 80G NTFS partition to about half that, and formatted the rest as ext3. Now I'm having trouble finding that new partition and thus can't mount it, and can't move the mp3s to it. 

How do I locate this ghostly partition??

Thanks

---

### Post by bodhi.zazen on 2007-04-15
Easiest way is to put this command into a terminal :

```
sudo fdisk -l
```

Note that is a small "L" and not the number 1

That will list your partitions.

To have them mount at boot you will need to edit /etc/fstab.

See here:

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

---

