---
title: "Unable to install 14.04 LTS onto mac mini"
date: 2015-10-12
forum: Apple Hardware Users
---

### Post by salmacis on 2015-10-12
I have a 2009 Mac Mini which I am attempting to dual boot with 14.04 LTS.

I've installed 14.04 LTS onto a flash drive. I've installed rEFIt. Ideally, I'd like to install onto a partition on the boot disk, but I'll settle for installing onto an external USB drive. (I can resize the Mac OS X partition so if I can work out how to install onto the external disk, the same solution will probably work for the internal disk.)

On rebooting, I get the rEFIt menu, and I'm able to run Ubuntu directly from the flash drive, and everything looks fine (apart from the wifi, which I'll have to sort out seperately.)

When I try to actually install Ubuntu, I select the option to install alongside Mac OS X, choose the external disk, and press 'Install Now. From there, I just get the spinning cursor,a nd nothing else happens. 4 out of 7 circles at the bottom of the window are orange.

On the external disk, I erased the one partition. Is there anything else I need to do to that disk to allow the install? Is there a way of getting a diagnostic or logfile from the install process?

Update: I was a bit of a numpty - I thought the partition was deleted, but Disk Utility had created a FAT32 partition. I used gparted to remove it, and the installation went smoothly.

---

### Post by yancek on 2015-10-12
You would likely be better off using the manual method called "Something Else" on Ubuntu rather than install Alongside.  You will have more control and select the drive and partition on which to install.

---

### Post by howefield on 2015-10-12
Thread moved to the "*Apple Hardware Users*" forum.

---

