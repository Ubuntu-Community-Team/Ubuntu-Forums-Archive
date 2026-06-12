---
title: "viewing windows partitions"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by norcalnewb on 2006-09-15
I am in the process of switching over to Ubuntu from Windows; which my wife is having a few issues with.  I had meant to make the machine a dual boot machine, but in the process, Windows got screwed up.  Now it reboots everytime I try to boot to Windows.  I think I have my wife convinced it is ok to switch exclusively to Ubuntu, but I need to get all the pictures, music, etc off my other harddrive (hda) which has Windows installed.  I can't get all of my partitions to mount.

When I run fdisk -l I get this output:
Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9732    78172258+  44  Unknown

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9355    75144006   83  Linux
/dev/hdb2            9356        9732     3028252+   5  Extended
/dev/hdb5            9356        9732     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS


I have 4 partitions on hda (actually I guess two, a primary, an extended with 3 logical partitions).  Does anybody have any advice?

Thanks,

Jim

---

### Post by bodhi.zazen on 2006-09-15
Err... [list=number][*]I only see 1 partition on hda: /dev/hda1. What happened with your windows partition?
[*]you were supposed to  backup first in the event "Windows got screwed up." #-o [/list]

At any rate try this (in a terminal)
```
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
```

If you are lucky you will find what you seek in /mnt/windows.

If you get error messages, post them here.... :-\"

---

### Post by norcalnewb on 2006-09-15
I do have a backup drive, which is the sda device.  I have most of the pictures backed-up there, but not the most recent.  There is also something odd with these files, as I cannot seem to open them, even though I can get to the ntfs folder they are stored in.

I am able to mount hda1, it is the other partitions I cannot mount at the moment.

---

### Post by agustin.g on 2006-09-15
You could try going into System -> Administration -> Disks. Normally the hard drive and all its partitions (and their format) should appear. Then you just set a mount point for the drive you wish to mount (for example /media/windows for hda1) and click on "enable" you should be able to access that partition until the computer is shut down. This normally should enable you to transfer documents without any particular difficulty, at least it has worked well for me, when i had to transfer documents from the Windows partition (in FAT32) to the Linux parition.

cheers

---

### Post by radiojef on 2006-09-19
I have tried to use the Admin > Disks controls and the commands and neither work for me. I can see the drives in the mnt folder but they have are the 'X' icon and when I click on them they say:

 "The Folders contents could not be displayed. You do not have permission to view these files"

I can view them in the command line as root of course, but that isnt really the way I would prefer to manipulate these files.

---

