---
title: "trouble with hard drives"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by insub2 on 2005-12-12
before install i backed up my files on another hard drive.  how do i get to them?

---

### Post by My8os on 2005-12-12
You'll probably have to mount it.
Maybe if you give a few more details about this hard disk (is it in ntfs?sata?external?) someone could help you more.
For start try these tutorials, helped me a lot:
 - [How to mount](http://www.tuxfiles.org/linuxhelp/mounting.html)
 - [How to edit fstab](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by insub2 on 2005-12-12
it is an old internal drive taht connects via ide

---

### Post by JimmyBEng on 2005-12-12
ok what else can you tell us.
do you know the kinds of partitions that are on the drive?
do you know how all the drives are hooked up in your system (primary or slave)?
what does your file /etc/fstab contain now?
```
more /etc/fstab
```
what is the result of the following command?
```
sudo fdisk -l
```

---

### Post by insub2 on 2005-12-12
[QUOTE=JimmyBEng]ok what else can you tell us.
do you know the kinds of partitions that are on the drive?
do you know how all the drives are hooked up in your system (primary or slave)?
what does your file /etc/fstab contain now?
```
more /etc/fstab
```
what is the result of the following command?
```
sudo fdisk -l
```[/QUOTE]

partitions:
i formatted in windows the just one partition.

hook up:
the hd that ubuntu is on is a sata primary
the one i am trying to get my files off of is ide(?)  primary



~$more /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


~$ sudo fdisk -l:
> 
Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1247    10016496    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris




also i tried following the ubuntuguide resulting in all the files having little locks on their icons.

---

### Post by qiemem on 2005-12-12
Just out of curiousity, what kind of files are you trying to recover?

---

### Post by JimmyBEng on 2005-12-12
here's the deal. The partition you are trying to access(/dev/hda1) is NTFS so that means you can only mount it as read-only for linux ( that was what caused the locks). below are the spots from the ubuntuguide about mounting your drive. (it looks like you found these already).

to mount once:
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

to mount everytime you boot:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

even though the guide is written for hoary, these sections on mounting FAT and NTFS work the same in breezy.

---

### Post by insub2 on 2005-12-12
[QUOTE=qiemem]Just out of curiousity, what kind of files are you trying to recover?[/QUOTE]


personal files such as .html, .jpg, .doc, .gif, .mp3, and etc.

which reminds me, i edited html using notepad.  what should i use now?

thanks!!!

---

### Post by JimmyBEng on 2005-12-12
[QUOTE=insub2]i edited html using notepad.  what should i use now?[/QUOTE]

the gnome equivolent to notepad is gedit

---

