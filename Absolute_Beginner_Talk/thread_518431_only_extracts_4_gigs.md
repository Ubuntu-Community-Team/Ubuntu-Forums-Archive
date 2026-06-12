---
title: "only extracts 4 gigs"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by CrashintoDMB on 2007-08-05
when i extract files more than 4 gigs, it will only extract up to 4 gigs. then it gives me an error. the hard drive still have 400+ gigs on it, so its not an issue of space. anything im doing wrong?

---

### Post by arijarot on 2007-08-05
maybe you can try doing it through the command line.

---

### Post by CrashintoDMB on 2007-08-05
how?

---

### Post by arijarot on 2007-08-05
what's the file extension type?

---

### Post by CrashintoDMB on 2007-08-05
.rar...i installed something to extract this. but here's another problem. my brother was sending me the first two bourne movies from his computer upstairs through a shared file and when i tried to pull the two movies (iso files) from his shared folder onto my data hard drive, it only took 4 gigs of each movie.

---

### Post by asmoore82 on 2007-08-05
what are you extracting files from??

---

### Post by testube_babies on 2007-08-05
What type of filesystem is this on?  On FAT32, 4gb is the largest file size possible.

---

### Post by dfreer on 2007-08-05
Sounds like a 4 GB file size limit to me as well. Try making chunks of the file using multi-part .rar files, that should fix the problem.

---

### Post by CrashintoDMB on 2007-08-05
testube, i have no idea what you just asked. im running ubuntu studio if that helps? no idea what FAT32 stands for. Dfreer, is there a way i can get around the file size limit? or even up it? i only need like another half a gig. i dont really know how to make chunks of this. it extracts to an .iso file

---

### Post by arijarot on 2007-08-05
To extract a .rar file:

```
unrar x file.rar
```

see for more info [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by CrashintoDMB on 2007-08-05
that didn't work. is there some way i can up the file limit?

---

### Post by dfreer on 2007-08-05
> **CrashintoDMB said:**
> testube, i have no idea what you just asked. im running ubuntu studio if that helps? no idea what FAT32 stands for. Dfreer, is there a way i can get around the file size limit? or even up it? i only need like another half a gig. i dont really know how to make chunks of this. it extracts to an .iso file

You can find out what filesystems are on your computer with these commands:
```
sudo fdisk -l
cat /etc/fstab
```
Let us know where you are trying to save the file and we should be able to tell you whether it is due to using FAT32.

As for breaking the rar file up into chucks, not sure on the exact commands. you will most likely need to install rar/unrar, and then check the man page or google on splitting the files themselves. If you don't feel like installing rar, you should be able to break up the file using tar as well (tar is already installed in ubuntu).

Basically, what is involved here:
Taking the large file.iso, creating multiple small archives using rar/tar, sending to the other computer, and extracting the files. But you will probably still run into the 4 GB limit if you are using FAT32. You can try downloading to another partition that is hopefully not FAT32 (give us that info and we can tell you which is which).

---

### Post by CrashintoDMB on 2007-08-05
readout:


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           7        9118    73192140    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1306    10490413+  83  Linux
/dev/sdb2            1307       60801   477893587+   f  W95 Ext'd (LBA)
/dev/sdb5            1307       60801   477893556    b  W95 FAT32


I'm saving/extracting the file to my "data" hard drive, which is like 500 gigs.

---

### Post by dfreer on 2007-08-05
According to this, you are indeed using FAT32 on the 500 GB hard drive. This is most likely causing the 4 GB file limit. Try saving it elsewhere, on your 80 GB drive, and you shouldn't have any problems.
If you do end up needing it on the 500 GB, try figuring out a way to split it up. For example, if the +4 GB file is a movie .iso, try extracting the video into a VIDEO_TS schema or .avi file. Or, if you can do it, you could repartion the 500 GB into a file system that supports +4 GB files.

---

### Post by CrashintoDMB on 2007-08-05
thanks.

---

