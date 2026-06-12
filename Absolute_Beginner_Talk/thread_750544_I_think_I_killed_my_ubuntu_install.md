---
title: "I think I killed my ubuntu install"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-04-09
I wanted to dual boot windows xp with my all ready installed Ubuntu, and screwed it up. I had Ubuntu installed on primary drive (SATA) and wanted XP just for games (yes I know about wine). I put in the CD and got to the part where I had to select a partition. I forgot I put all the space left onto my home partition. So I put in the Ubuntu live CD after rebooting so I could put some of the free space on my home partition into just empty space so I could use it to make a windows Partition. So I loaded up the Partition editor and when it was done scanning the drives, it showed my hard drive and said unallocated on the top of the drive! I thought that that couldn't be. I didn't tell the windows CD to delete or format ANYTHING. So I restarted my PC and booted from the Hard DRive and got a message saying, "Error Loading Operating System". It makes me really sad that if it was deleted that I lost all that data. :cry:
Help please!!! (I tried using the alternate CD's recover thing and reinstall Grub but that gave me a fatal error
Oh and if it was deleted, would you suggest installing Ubuntu first or XP.

---

### Post by motoperpetuo on 2008-04-09
are you able to mount the local volume on your computer with a live CD and confirm that your data is still there? (puppy linux is my personal favorite for doing this.) if the data is there, if you haven't tried it already, try the supergrub CD. i believe this is the correct link:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

you'll have to play around with the options a little, but i've been able to recover from many a boot up problem (in both windows and linux) with this CD.

if your data is gone, i don't think there's much you can do. this doesn't help you now, but always back up important stuff if you're planning on doing something major to your computer like trying to set up a dual boot system.

as far as which OS to install first next time around, definitely windows. the ubuntu install will guide you through easily setting up a dual boot system.

---

### Post by ELF_O8 on 2008-04-09
I would recommend setting the partitions up in Ubuntu first but installing XP first.
It is easiest to let Ubuntu recognize Windows and install it into the GRUB than
to install Ubuntu and then Windows and THEN set up the GRUB.

---

### Post by Shazaam on 2008-04-09
First off, boot into the Ubuntu livecd and run this code in terminal....
```
sudo fdisk -l
```
(small L)
This code will give you a list of your partitions. Somehow find a way to post the output here (write it down?).
If you do decide to start over install Windows first. Then in the unallocated space create an extended partition. Inside that extended partition install Ubuntu.

---

