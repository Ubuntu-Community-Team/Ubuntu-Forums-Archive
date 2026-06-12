---
title: "Newbie in desperate need of help partitioning! Please help!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by mlucian72 on 2007-06-11
Hi,
 I am very new to UBUNTU, but I learn pretty fast...I try hard at least.
 I've installed UBUNTU 7.04 32 bit version, on an AMD64 machine and works great. I love it!!!
 The thing is I didn't really know how to partition my drive, so I let UBUNTU do it for me using the entire disk. I don't have windows anymore on my system, and I intend to keep it this way, so here is were I need help.
 I want to re-partition my drives. and re-install UBUNTU, but I don't know how to define the partitions.
 Here is what I have on the system now:
 1 SATA 400GB Hard set as master
 1 IDE 200GB hard set as slave.
 I want the computer to boot of the SATA drive, and I want to partition it like you would have "drive c:" ; "drive d:" ; "drive e:" in windows, so if I ever need to reinstall UBUNTU I don't have to format the entire drive and loose everything.
 On the SATA drive I want to make a 100GB partition for UBUNTU and all the aplications, and 2 more partitions of 150GB each, let say one for downloads and one for personal stuff (pictures,etc)
 Also I want to use the other drive and make one partition for the entire drive of 200GB, called backup or storage.
 I don't know how to do this and I will really appreciate if someone helps me with very explicit directions as far as defining the partitions type, "mount as" instructions and how I go about installing UBUNTU in the right partition on the SATA drive (100GB), and make it boot from it.
 Thank you so much for reading!
  I love UBUNTU!

---

### Post by bodhi.zazen on 2007-06-11
Linux Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Mounting : 

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


fstab : [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

