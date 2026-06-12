---
title: "Are these install instructions (Ubuntu on Mac) still valid?"
date: 2010-06-05
forum: Apple Hardware Users
---

### Post by germanix on 2010-06-05
I found these instructions for installing Ubuntu on a (Intel) Mac in the Ubuntu Pocket Guide. These instructions were based on Ubuntu 8.10. I have a 2009 24" iMac and would like to install Ubuntu 10.04 as a dual boot configuration. I would appreciate if someone can check these instructions as shown below and tell me if they are still valid or has something changed in the meantime.

Getting Ubuntu onto an Apple Mac (Intel based)
You can use Ubuntu’s install CD to install Ubuntu on Macs that use Intel CPUs. This will let you dual-boot Mac OS X and Ubuntu. However, you will first need to use OS X’s Boot Camp feature to create space.
Instructions are below. These steps assume Windows is not installed on the Mac alongside OS X—complications are introduced if this is the case; see [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook).
1.	Start Boot Camp Assistant and follow the wizard as if to create a Windows installation. Boot Camp Assistant can be found by
Installing Ubuntu : 17
opening Finder and clicking Applications, then selecting the Utilities folder. The Windows partition size you choose will equate to the Ubuntu partition size, so ensure more than 5GB is freed-up. When Boot Camp Assistant finishes shrinking the OS X partition, hit the QUIT & INSTALL LATER button.
2.	You must now delete the NTFS (Windows) partition created by Boot Camp Assistant. To do this, open Disk Utility (as previously, it can be found in the Utilities folder). In the program window that appears, select the topmost entry in the list of disks on the left representing your hard disk, and click the PARTITION button on the right. Select the BOOTCAMP entry in the graphical preview of partitions, and click the minus button beneath. Then click REMOVE. When done, close Disk Utility.
3.	Download and install the rEFIt software. This provides a boot menu that lets you choose between Mac OS X and Ubuntu. rEFIt can be downloaded from [http://refit.sourceforge.net—](http://refit.sourceforge.net—) choose the Mac disk image download. Note that there is no immediate sign that rEFIt is installed; it doesn’t feature a configuration program within Applications, for example.
4.	Insert the Ubuntu install CD and reboot your computer. Upon hearing the boot chime, hold down the C key. Eventually, you’ll see the Ubuntu install disc boot menu. Follow the instructions on page 9 describing how to install Ubuntu. However, when the partitioning stage begins, don’t resize. Instead, select Guided- Use the Largest Continuous Free Space.
(select Guided- Use the Largest Continuous Free Space? I cannot recall having seen this option when I installed Ubuntu on my laptop. Is it still there?)
NOTE There is a bug with Ubuntu 8.10 whereby selecting the Guided&#8208;Use the Largest Continuous Free Space option shows Ubuntu occupying the entire disk in the “After” graphical preview. This is incorrect and can be ignored. (is this still true?)
5.	Follow through the installation stages, as if installing on a standard PC. When you reboot, select the Linux penguin on the rEFIt boot menu to boot Ubuntu, or the Apple icon to boot OS X (use the cursor keys to highlight either, and hit Enter to select).

Is the above still the standard procedure?

---

### Post by linuxopjemac on 2010-06-05
I am not sure, but this is what some guy found useful:
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=125](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=125)

---

