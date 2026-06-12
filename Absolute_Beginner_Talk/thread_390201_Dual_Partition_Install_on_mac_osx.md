---
title: "Dual Partition Install on mac osx"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by sexlax8769 on 2007-03-21
Hey guys,
  I'm currently running Mac OSx 10.4.9 on an iBook G4.  I partitioned the drive so i now have two drives each with around 27 gigs apiece.  I am running the osx on the first partition....  How do i install Ubuntu on the second partition?

Thanks for any info!

---

### Post by undertherift on 2007-03-22
Do you have an install CD for ubuntu?  Go ahead and drop that in.  Boot to ubuntu, and double click 'Install' that will appear on the desktop.

When you get to the option about what partition to use - make sure you click the right drive, and then select the right partition.  Generally, what i've done is formatted one partition HFS+ (or whatever) and then left the rest of the space free, and let ubuntu configure the free space itself.

Good luck.


EDIT:  You can generally follow any simple HOWTO dual boot ubuntu and WinXP - the boot loader will treat it the same way.  If it doesn't, post back - we'll have to set up a grub (bootloader) entry for OSX.  The trip boot xp/ubuntu/osx worked fine for me, so i'll do my best to help. (10.4.6, i think, i dont remember, i dont use it).

---

