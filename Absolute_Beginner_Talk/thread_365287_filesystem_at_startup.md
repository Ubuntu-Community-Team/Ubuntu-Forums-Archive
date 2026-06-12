---
title: "filesystem at startup"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Klimax on 2007-02-19
I have recently installed Ubuntu 6.06, on a dual boot windows/ubuntu system, and at startup I keep having a weird error about the filesystem. It still starts up just fine, but it pauses for quite a while on this error and it's quite annoying. Also, I'm not sure if this has any other effects on my computer.

I'd like to post all the details here, but I have no idea where I can find the log of the booting process.

Could somebody tell me where I can find this log so I can post the error here?

---

### Post by taurus on 2007-02-19
```
sudo cat /var/log/messages
-or-
dmesg | more
(and hit space bar for the next 24 lines)
```

---

### Post by Klimax on 2007-02-19
> **taurus said:**
> ```
sudo cat /var/log/messages
-or-
dmesg | more
(and hit space bar for the next 24 lines)
```

Hmm, I can't seem to find it in there, maybe we're talking about different logs.

The error occurs when Ubuntu is still loading, and follows every step with "OK" at the end of the line. At the step "checking filesystems" (if I remember correctly) it jumps over to a terminal interface instead of the simple loading screen with a detailed error message.

Where could I find this?

---

### Post by taurus on 2007-02-19
Do you remember what partition the error occurs?

---

### Post by Klimax on 2007-02-19
I lookd for it but I can't find it telling me what partition it is. However, I can only see it telling me that its a problem with a fat32 partition, but both my windows and linux partition use that filesystem.

---

### Post by taurus on 2007-02-19
Are you telling me that you installed Ubuntu on a fat32/vfat filesystem?  Post the result of these two outputs here.

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Klimax on 2007-02-19
> **taurus said:**
> Are you telling me that you installed Ubuntu on a fat32/vfat filesystem?  Post the result of these two outputs here.

```
sudo fdisk -l
cat /etc/fstab
```

I think I made a mistake there XD these are the results:

```
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    c  W95 FAT32 (LBA)
/dev/hda2            3188        4863    13462470    5  Extended
/dev/hda5            3188        3252      522081   82  Linux swap / Solaris
/dev/hda6            3253        4863    12940326   83  Linux

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS
richard@richard-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows-c      vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hdb1       /windows-h      ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-02-19
Replace the last digit from **1** to **0** for both /dev/hda1 & /dev/hdb1 in /etc/fstab.

```
gksudo gedit /etc/fstab
```
That should fix the problem.

---

### Post by Klimax on 2007-02-19
> **taurus said:**
> Replace the last digit from **1** to **0** for both /dev/hda1 & /dev/hdb1 in /etc/fstab.

```
gksudo gedit /etc/fstab
```
That should fix the problem.

Thanks alot! :) I can't believe how fast I got this problem fixed XD

---

