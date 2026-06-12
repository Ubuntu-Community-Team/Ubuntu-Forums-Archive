---
title: "Installing Dual-Boot with VIA VT8237 RAID 0"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by crazy757 on 2007-05-10
I want to make sure I know how to do this before I begin installing Ubuntu.  I want to know if I can install Ubuntu to dual boot with Windows XP on an already made RAID 0.  My RAID controller is a VIA VT8237 and is on an ASUS motherboard SK8V.  If I need to reinstall Windows, I will, but would rather just have it already work.

---

### Post by richteel on 2007-06-14
I have been trying to find a solution for a different problem with the VIA VT8237.  I did not intend to do a dual boot but it looks like that is what I have.  (I have not booted into Windows XP yet as I am afraid I may loose my Ubuntu install.)

I have two 250GB hard drives on a RAID-0 array (mirror array).  I installed Ubuntu 7.04 64bit and during the installation I was a bit concerned as when it asked me where to install I had the option of the two hard drives.  (I would have expected that they would show up as one.)

I selected the first drive and went on with the install.  Once Ubuntu installed, the first thing I wanted to do is verify that the install was on the mirror or just one drive.  I looked in vain for "Disks Manager" but found that someone thought it was a good idea to remove it from the release.  Hello very very stupid!! (Just in case anyone cares.)

I found pysdm and installed it but it is a very poor replacement.  I can not view partition size so what good is it?  Well it is good enough to let me see that it installed only on the first drive.  Windows XP is intact on the second drive.  That explains why it shows up as one of my OS choices when I boot up.

It appears that Ubuntu disabled the mirroring on the controller.  I rebooted and hit tab to get into the VT8237 bios and found that the array is intact so Ubuntu did not remove it.  So what is going on here??

I found one post which vaguely  made mention to the fact that VIA RAID is done in software.  OK I can understand that it. It should be software on the controller that is how all controllers work. What I am starting to wonder is if the individual meant in the OS not in the controller.  If that is the case then the VIA controller is not a very good one and that would explain why this happened.

As a result I am fearful of running Windows XP as it may wipe out the Ubuntu install.

I don't know if any of this helps but seeing how there have been no responses to your post I figured it may not hurt.  Hopefully someone will know what I am talking about here and explain to me why and how this happened. :confused:

---

