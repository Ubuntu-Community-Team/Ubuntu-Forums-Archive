---
title: "Dual boot problem"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jacaline132 on 2007-04-10
I just installed Ubuntu Edgy as a dual boot on my laptop that has a 60 gb hard drive. I installed it so that both operating systems had equal space.  Now when I boot Ubuntu the screen goes black and numbers come on it and it says "not automatically fixing this"  Other than the numbers there is also hda1 and hda2 which should be the windows partition.  This makes me think that the numbers are files that belong to windows and that Ubuntu can't read, but as I'm new to this I may be wrong.  After a minute or two Ubuntu finishes booting and asks for username.  On the desktop there are the two windows hard drives and when I click on properties they both come to about 20 gb which is how full my windows partition is.  Both operating are also running very slow.

What went wrong and how can I make it so that both operating systems are separate and don't share anything?

---

### Post by dstew on 2007-04-11
From Ubuntu, open a terminal (in Accessories) and enter

sudo fdisk -l

This will list your partitions as your Linux system sees them. Maybe this will give us a clue.

---

### Post by jacaline132 on 2007-04-11
Thank you for your help,

It said:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         509     4088511   12  Compaq diagnostics
/dev/hda2   *         510        3871    27005265    c  W95 FAT32 (LBA)
/dev/hda3            3872        7169    26491185   83  Linux
/dev/hda4            7170        7296     1020127+  82  Linux swap / Solaris

---

### Post by dstew on 2007-04-11
That looks OK. I think you may be getting error messages when the kernel boot process tries to mount the partition hda1, and possibly hda2 also. Please post the output of **cat /etc/fstab**. This will show us the instructions for mounting partitions.

---

### Post by jacaline132 on 2007-04-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=bb2b27f1-d259-40c4-af08-3a58a02ed646 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0E4E-05CE  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=320D-180E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=ec6495f7-d1d2-4137-a799-d78527af715a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by dstew on 2007-04-12
Comment out this line by putting a # at the front of it:

**#**UUID=0E4E-05CE /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1

To edit the file, enter **sudo gedit /etc/fstab** at the command line. Put in the **#**, save the file, then reboot. Be careful not to change anything else in the file. If you want to, make a backup of the file before you edit by entering **sudo cp /etc/fstab /etc/fstab_old**

This instruction causes Linux to try to mount your Compaq Diagnostics partition. It has a proprietary file format that Linux does not recognize. It tries to mount it as a vfat file system, and this gives you the error message I believe.

---

### Post by jacaline132 on 2007-04-13
The error message for hda1 went away but there is still a similar message for hda2 can I do something similar for that?

Thank-you for your help.

---

### Post by gus sett on 2007-04-13
Yes. you can comment out the hda2 entry counterpart similar to
what dstew recommended for hda1.  
The W95 tag elsewhere identifies it as a Windows partition.

:?: You did backup your important data as a precaution before 
trying this, right

---

