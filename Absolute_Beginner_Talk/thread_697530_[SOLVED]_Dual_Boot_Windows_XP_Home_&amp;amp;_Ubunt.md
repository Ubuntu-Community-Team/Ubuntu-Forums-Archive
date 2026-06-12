---
title: "[SOLVED] Dual Boot Windows XP Home &amp;amp; Ubuntu Linux"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Rytron on 2008-02-15
Hi,
I have got ubuntu on a cd.
I have got an old pc with a 60 GB hard drive with Windows Xp Home on it.
I decided I wanted to have this pc as a dual boot pc with Ubuntu & Xp Home.
I booted from the cd, partitined the Xp Home into 20GB and allotted 35GB for Ubuntu.
I then installed Ubuntu.
It looked like everything was going well.
The install took about 1 hour and 10 minutes.
After the install was finished, I clicked restart now.
The pc rebooted and I got the GRUB menu.
Ubuntu was first on the list, I clicked return.
The ubuntu symbol came up on the screen and the progress bar was below it, the progress bar started and only moved a tiny amount.
The pc did nothing for a few minutes.

Then I got this screen - please find it attached.

Please does anyone know what the problem is and how do I remedy this situation?

If it is relevent here are the specs of the pc I used:
256MB RAM
60GB Hard Drive

---

### Post by bumanie on 2008-02-15
I would guess that the computer crashed. 256 mb ram is not really enough to use with ubuntu. You should try xubuntu instead. I think gutsy and feisty need 384 mb ram to function. I'm surprised your computer managed to install from the live cd. Xubuntu is a lighter version of ubuntu with a different desktop environment that is not as heavy on resources, or else put a bit more ram in the computer.

---

### Post by neurostu on 2008-02-15
hm....

maybe these can help:
[https://answers.launchpad.net/ubuntu/+question/173](https://answers.launchpad.net/ubuntu/+question/173)
[http://ubuntuforums.org/showthread.php?t=94250](http://ubuntuforums.org/showthread.php?t=94250)

It seems to me from reading those two posts that it probably an issue with your hard drive.  What did you use to partition the HDD? Did you use something like partition magic or did you let the Ubuntu install CD do it?   If didn't use the install CD, I would reinstall Ubuntu (make sure you have the latest copy) and make sure you select the correct partition, Format it to EXT3 and set its mount point as " / "

Also you might want to check to see if grub is pointing to the correct location it could be checking for something like SDB2 instead of SDA2 which is probably where your ubuntu partition is....

sorry I can't be of more help but I would definately check google!

Good luck!

---

### Post by phr0ze on 2008-02-15
You install disk could have been corrupted too. The disks have a self check, run that once to see if the disk is ok. Then, even if it is OK, I'd try the install just one more time.

---

### Post by bumanie on 2008-02-15
If you are installing gutsy gibbon, ubuntu 7.10, the current release, you need a minimum of 384 mb ram (apparently releases prior to this could manage with 256 mb.
> The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

Whether you can successfully install may depend on whether you have a shared video card or not and then you would have to be installing a release prior to the current release.

---

