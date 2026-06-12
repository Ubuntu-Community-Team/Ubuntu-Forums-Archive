---
title: "installation/partitioning"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by cmrober on 2007-05-05
Ok, I've made the install CD and started the install process but got scared when I got to the partitioning part...What option do I use to keep my Windows intact? How do I go through a manual precess if necessary?
Thanks

---

### Post by kfrance on 2007-05-06
I always do it manually because I like to have control where everything goes.  When you manually fix the partitions you just need a partition to put the root partition which is called "/".  This is where the heart of the operating system is installed.  You then have to indicate a partition for swap.  Swap is where things are placed temporarily on the hard drive.  Things will get swapped from RAM to swap and vice versa.  A good rule of thumb for the size of the swap partition is twice the size of the amount of RAM you have.  In the partition manager you will be able to see what partitions are already there and have the chance to make new partitions.   If you have windows then you can also assign it a label.  I think by default it is /media/windows.  I usually changed it to /windows but you can put it anywhere. I know that the interface has changed with feisty fawn but I haven't used it yet so I can give you to many specifics.

---

### Post by Rotaj on 2007-05-06
Before you start installation, I highly recommend backing up your data and defragmenting your drive from windows a couple of times. 
A couple of guidlines. 
Check how much space us used by windows. 
1Gb = 1024 mb
Your swap partition should be at least twice th size of your ram. 
If your drive is in the 60Gb range, Allow 13 Gb for both Windows & Ubuntu, & 2 Gb for swap. This leaves 32Gb that can partitioned and then formatted as a FAT32 drive. This is the largest Windows willl allow.

[http://ubuntuforums.org/showthread.php?t=432268&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=432268&highlight=dual+boot")

---

### Post by bobbybobington on 2007-05-06
The default partitioning is your best bet. However you should make sure that any stuff you don't want to lose is backed up, since things don't work perfectly all the time.

---

