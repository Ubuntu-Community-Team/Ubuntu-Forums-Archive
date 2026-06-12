---
title: "Allocating more space to Ubuntu primary installation"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2007-11-30
Hi,

I've recently installed a dual-boot configuration for Ubuntu 7.10 and Windows XP. Both OS's are installed on the C drive.

I now wish to allocate more space to my Ubuntu primary installation (on C drive) from a secondary HDD.

My configuration is as follows:

C Drive 
- ntfs format
- 65.7GB total 
-- 27.8GB used for Windows XP files
-- 9GB used for Ubuntu 7.10

D Drive
- ext3 format
- 149GB total/free

1. Is it possible to add the D drive space to Ubuntu Home (so Home can store all my documents/videos/music files)? 

2. What format would you recommend I use for the D drive - ext2, ext3, FAT32? I'm not sure what these format types entail.

3. Is there another configuration you would recommend? 

Thanks for your help!

---

### Post by Stormspireiv on 2007-11-30
I was in almost your exact situation a month ago. What I would do is keep your secondary drive in ext3 format and move your home folder to that drive, then set your fstab to mount the new location of your home folder to /home.

I used this tutorial to help [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) but beware: you will probably need to know a bit about terminal commands and mounting file systems to make this work for you. If I remember right, I had to modify a few of his steps (don't remember which ones) to get it to work for me.  Another further warning: if you don't do everything correctly before you Ctrl+Alt+Backspace or reboot, you will be stuck at the console.

If you don't feel like moving your home folder (although, if you have the technical knowledge, it is a good idea), you could always create a folder in your home directory and mount the secondary hard drive there.  The downside to this is you would have to put everything "big" in that folder.

---

