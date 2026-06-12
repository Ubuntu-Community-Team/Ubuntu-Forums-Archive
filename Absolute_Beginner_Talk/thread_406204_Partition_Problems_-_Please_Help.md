---
title: "Partition Problems - Please Help"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by The Duke of Ted on 2007-04-10
Sorry, I posted this in the wrong place before... :lol: 

Anyway... I'm a ubuntu convert - I recently downloaded version 6.10 and want to create a separate partition to dual-boot ubuntu with Windows XP, but I keep running into problems - for some reason, it seems my PC is incapable of resizing my Data partition...

My hard drive is partitioned into three sections - the first one is a backup partition, the second is my Windows XP / programs partition, and the last is for data.

Partition One: FAT - 7.81 GiB
Partition Two: NTFS - 30.00 GiB - boot
Partition Three: NTFS - 111.24 GiB

The Third Partition is the one I want to resize.  I have tried to do so using Paragon Partition Manager in XP, and it restarts the computer, but doesn't do anything.
Doing so when going through the installation procedure in ubuntu, and it results in the following error:
> The following operation could not be applied to the disk

*Resize /dev/sda3 from 111.24 GiB to 69.19 GiB*

See the details for more information

I'm completely stuck on what to do, and I desperately want this to work, as I'm already amazed at the quality of ubuntu - please come up with a solution for me :)

---

### Post by Patrick K on 2007-04-10
Did you defrag the partition first. If there is any data in the area you want to resize, you won't be able to do it. After defragging take a look with GParted, it's on the livecd. If any data is in the area you want to use, it should show up in the graphic for that partition. 

Sometimes Windows puts unmovable files on the disk. If any of these are in the target area, they would keep you from resizing. I don't know how you would move them.

---

### Post by markusfarkus on 2007-04-10
It would be nice to have some of those other details for some more information :-)

You might try using gparted boot disk just to make the changes. 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you have everything backed up elsewhere (which would be recommended anyway) you could just delete the whole partition and recreate the partitions you need manually.

---

### Post by DoubleQuadword on 2007-04-10
> **Patrick K said:**
> After defragging take a look with GParted, it's on the livecd.

Another option could be using it from within the Ubuntu installer.

Regards.

---

### Post by gh0st on 2007-04-10
> **markusfarkus said:**
> It would be nice to have some of those other details for some more information :-)

You might try using gparted boot disk just to make the changes. 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you have everything backed up elsewhere (which would be recommended anyway) you could just delete the whole partition and recreate the partitions you need manually.

Yeah I'd also recommend the GParted Live CD option to you. I have used it many times and it's just great, I know you can use the Ubuntu installer to resize partitions but I just found it easier the other way.

GParted rocks, it really does. Good luck to you :)

---

### Post by The Duke of Ted on 2007-04-10
I'm currently using the ubuntu live CD, and gparted runs from it, but that doesn't seem to do the job either, resulting in the above error message.  I've defragmented the partition, and there are no system unmovable files in the area... any other solutions?  I'm dying to get this working :lol:

---

### Post by Patrick K on 2007-04-10
If you can do it, backing up, deleting, recreating the partitions needed, then restoring might be the best bet. A bit more work but should get you up and running.

---

### Post by dstew on 2007-04-10
What are the error details? Usually, this kind of failure is due to some bad sectors on the disk. The bad sectors do not interfere with its usability, but GParted will not resize a partition that is not free of errors.

I suspect this is the problem. To fix it, boot into Windows, and do **chkdsk /f** on that partition from the command line. Then try again to resize with GParted.

EDIT: You can also do chkdsk /f from the Windows Recovery Console, which you get when you boot the recovery disk.

---

