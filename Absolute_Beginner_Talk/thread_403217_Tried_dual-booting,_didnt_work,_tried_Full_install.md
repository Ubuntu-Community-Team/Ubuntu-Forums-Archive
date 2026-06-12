---
title: "Tried dual-booting, didnt work, tried Full install, didnt work, i have a few more Qs"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-04-06
I want to dual-boot still and I found this guide, [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2), How does that look?  Are those all the instructions I need?

Once I install, how would I install my monitor drivers?  I found out that the drivers I use for windows xp are on a partition made by the OS thats about 4gig and has all the drivers and stuff I need, but how can I get them onto ubuntu?  or at least find the specific drivers i need on the web and then get them over?

---

### Post by sirhalos on 2007-04-06
Basically the way Ubuntu Linux works is generally you do not install drivers unless you have something that uses a special proprietary driver such as a Nvidia video card or ATI. Run the Ubuntu Live CD and make sure everything is functional the whole Ubuntu system will be running off of the CD. Test your audio, internet, video settings that way. If everything works once you install Ubuntu everything will be the same. Linux is actually better than Windows out of the box because it typically always works or doesn't work out of the box some times you may need to do something but typically you never need to do anything at all. Same is true with downloading software you do not go to websites to download software there will be a program in Ubuntu to find and install software. And to answer your last question they will be an option during the install to resize your Windows drive or if you have a partition already available for Ubuntu there is an option to do a custom install to that partition. You will find the Ubuntu install is very straight forward and much easier than installing Windows.

---

### Post by garwaymatt on 2007-04-06
When installing a dual boot system, ubuntu takes care of most of it, the only complicated bit is to partition the hard drive. The key to this is to back up, and make sure the backups work!(speaking from experience). 

Edgy has a graphical system of resizing partitions. The key thing is that you need an ext3 partition for ubuntu files and data, and a swap partition(similar to virtual memory in windows) make sure that you do not resize the partitions smaller than the data on the drive, otherwise you will lose the data. The ubuntu partition does not need to be very large, anything above 3-5 gb is ok. This needs to be created as an ext3 partition, set as the root mount point. You also need to create a swap partition, which should be a similar size to the amount of ram you have.

The drivers on the windows partition are generally not needed by ubuntu, as it has its own set of drivers. Out of the box, most things should 'just work' but don't hold me to that one!

---

### Post by nintennuendo on 2007-04-06
I tried doing the Live CD before, and installing.  IT still seemed to redraw very slowly.  like.. VERY slow.

---

