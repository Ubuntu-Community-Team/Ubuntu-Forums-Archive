---
title: "can't partition hard drive"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by calldrin on 2007-10-01
I'm trying to install 7.04 on my hard drive and it comes back with a error.
The drive is 60Gb, NTSF, running XP, I've tried several CD's and this same error comes up.
I'm using the Guided - resize, even using the manual-resize has this same error;

"Resize operation Failure
an error occurred while writing the changes to the storage devices.
The resize operation is aborted."
:
I've looked at the help files and can't find any answers.

Also what size do I make the different partitions? and what is each partition name?

System is Acer running AMD 64x2 @ 4200, 2GB RAM

Thanks for helping a real NEW NEWBIE!!

Chuck
Chico, CA

---

### Post by Yoooder on 2007-10-01
Chuck, I'd recommend letting Ubuntu do the partition for you if you are a newbie.  It's much easier and should produce better results.

Before you proceed though, you do intend to wipe the NTFS partition from the drive, don't you?

---

### Post by jalanbuntu on 2007-10-01
Maybe gparted which comes with the live cd cant resize NTFS partition.
Also I think it is not safe to resize the NTFS or FAT32 partition if you dont defrag it first.
Try to use any third party partition manager from windows first, like Norton Partition Manager,
to make a partition for linux (reiserf, ext3, etc) and swap partition.

---

### Post by calldrin on 2007-10-01
I have tried both ways, auto and manual... both have the same error.
Not sure what  you mean about wiping the NTSF
I want to keep my XP on one half of the drive and Linux on the other.
chuck

---

### Post by calldrin on 2007-10-01
I did a defrag just before starting the install process!

chuck

---

### Post by jalanbuntu on 2007-10-01
I guess he dont try to wipe the NTFS partition, but to install dual boot Ubuntu and Windows. Because he said that he want to resize it :)

---

### Post by iposner on 2007-10-01
Download the Gparted bootable CD from sourceforge.net. Burn a disk and boot into it. Now select the NFTS partition and shrink it. Then select the empty space and create two partitions from it, one for Linux and the other for the Linux Swap. Make the Linux Swap roughly twice the size of physical RAM. Format the Linux partition as either EXT3 or ReiserFS (my favourite). Specify the format of the swap partition to be Linux Swap.

Apply the changes and shutdown.

Boot onto the Ubuntu install CD. When it comes to the disk configuration, go to the manual configuration and select the Linux partition to mount as "/". If you want to be able to read from the NTFS partition, set the mount point to something like "/windows". Continue with the install and it should all just work.

---

### Post by psusi on 2007-10-01
Run a chkdsk /f from windows, reboot, and let it fix the filesystem.

---

### Post by calldrin on 2007-10-01
Thanks for the help.. I got it to works using your directions.

Chuck

---

