---
title: "Using live CD how do you mount local linux disk"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by XstatyK on 2007-04-05
Here is the current situation:
I have Ubuntu 6.10 installed on a local disk
I have booted the system using the Live CD (6.10)
 My question is
How do you mount the local disk while in the live CD session?

My task:
To backup my files to an external usb drive (which is ext2 - linux native), since I've managed to mess it up.  I was planning on upgrading soon, so I was just trying a bunch of things.  I'm not really concerned with wiping it out and reinstalling but I  would like to backup the files from the local disk to the external usb drive before I do it.  I should have done this before .. lesson learned. :) 

Thanks

---

### Post by cantormath on 2007-04-05
assuming it is a linux drive we are mounting......

first you need to find out what partition the drive with linux is on, /dev/hda1 most likely.....
if you want to look with the live cd you can open the disk manager and see what partitions are on the drive.......

```

:~$ hal-device-manager

```
click on the partition tab, its gonna be one of those.......probably /dev/hda1.
then
```

:~$ cd /tmp

:~$ mkdir hd

:~$ sudo mount /dev/hda1 hd

cd into the hd folder and it should be your local file system.
:~$ cd hd


```

you could name the fold hd anything you want, also, you could put the folder in /media/ and it will show up in your mounted devices in your places tab.

---

### Post by XstatyK on 2007-04-05
Yes it is a linux drive.  What is the command to list the hard drives that are existing?  It says:
ubuntu@ubuntu:/tmp$ sudo mount /dev/hda2 hd
mount: special device /dev/hda2 does not exist
ubuntu@ubuntu:/tmp$ sudo mount /dev/hda1 hd
mount: special device /dev/hda1 does not exist
ubuntu@ubuntu:/tmp$ sudo mount /dev/hdb1 hd
mount: special device /dev/hdb1 does not exist
(i tried a couple of different ones)

---

### Post by XstatyK on 2007-04-05
Ok thanks for the heads up in the right direction.  
The command to list partitions is sudo fdisk -l
then I was able to see which partition I wanted to mount.  Then i just did as you suggested only changing the drive partition name.  Here is what it looks like

ubuntu@ubuntu:/tmp$ sudo fdisk -l

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
240 heads, 63 sectors/track, 7943 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7943    60049048+   c  W95 FAT32 (LBA)

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       36106   290021413+  83  Linux
/dev/hdd2           36107       36483     3028252+   5  Extended
/dev/hdd5           36107       36483     3028221   82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12188    97900078+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5168    39070048+   7  HPFS/NTFS
ubuntu@ubuntu:/tmp$ sudo mount /dev/hdd1 hd
ubuntu@ubuntu:/tmp$ cd hd
ubuntu@ubuntu:/tmp/hd$ ls
bin    dev   include     initrd.img.old  man    opt   sbin   sys  var
boot   etc   initrd      lib             media  proc  share  tmp  vmlinuz
cdrom  home  initrd.img  lost+found      mnt    root

Anyway just wanted to say thanks!:KS

---

