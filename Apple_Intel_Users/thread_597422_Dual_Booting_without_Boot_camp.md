---
title: "Dual Booting without Boot camp"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by winn_man on 2007-10-30
After a long search of a way trying to find of installing Ubuntu on my MacBook to run using BootCamp like Windoze would, I stumbled across the Apple Intel Users FAQ this morning. Happy that I had finally found some way of doing this, I set out to trying the method. Unfortunately I can't use this method anymore due to BootCamp only being able to be used only with Leopard now.
I'm not interested in upgrading to Leopard, so my question is... Is there a way to install Ubuntu on my Mac? I'm looking for a non-destructive way that wont destroy any of my data already present on my HDD.

---

### Post by cyberdork33 on 2007-10-30
> **winn_man said:**
> After a long search of a way trying to find of installing Ubuntu on my MacBook to run using BootCamp like Windoze would, I stumbled across the Apple Intel Users FAQ this morning. Happy that I had finally found some way of doing this, I set out to trying the method. Unfortunately I can't use this method anymore due to BootCamp only being able to be used only with Leopard now.
I'm not interested in upgrading to Leopard, so my question is... Is there a way to install Ubuntu on my Mac? I'm looking for a non-destructive way that wont destroy any of my data already present on my HDD.
[Gparted]("http://gparted.sourceforge.net/livecd.php")... OR [Parted Magic]("http://partedmagic.com/").

---

### Post by doublemeat on 2007-11-01
Just follow the instructions in one of the many guides available, some here on these forums, specifically for ubuntu and mac.  Try googling something like "mac dual-boot ubuntu".

I have done what you are trying to do, and where you are now is fairly easy.  There is a terminal command in Mac OS X that non-destrcutively resizes partitions.  It might be "disktools" or something--the same name as the GUI application.  Most of said tutorials walks you through it.  I don't think you need BootCamp for any part of dual-booting with Linux.

Linux' gparted cannot resize Mac's file system, but does do a fine job of non-destructively resizing inux partitions.

Word to the wise, save yourself alot of headache, and heed the recommendations to use rEFIt, and do not use GRUB as a stage 1 loader (but you do need it as a stage 2 and only stage 2 loader).  Most of the tutorials discuss this.  Good luck.

---

### Post by cyberdork33 on 2007-11-01
> **doublemeat said:**
> I have done what you are trying to do, and where you are now is fairly easy.  There is a terminal command in Mac OS X that non-destrcutively resizes partitions.  It might be "disktools" or something--the same name as the GUI application.  Most of said tutorials walks you through it.  I don't think you need BootCamp for any part of dual-booting with Linux.

it is 'diskutil resizeVolume'

> Linux' gparted cannot resize Mac's file system, but does do a fine job of non-destructively resizing inux partitions.

Yes it can. and parted magic can create hfs+ as well.

---

### Post by winn_man on 2007-11-01
I've found a way of using the expired beta of boot camp and that is to just change the clock. I set my clock back a year and was able to get the boot camp assistant to do everything!!!!

---

### Post by cyberdork33 on 2007-11-01
> **winn_man said:**
> I've found a way of using the expired beta of boot camp and that is to just change the clock. I set my clock back a year and was able to get the boot camp assistant to do everything!!!!
HAHA, what an overlook! Good find!

---

### Post by doublemeat on 2007-11-02
> **winn_man said:**
> I've found a way of using the expired beta of boot camp and that is to just change the clock. I set my clock back a year and was able to get the boot camp assistant to do everything!!!!

Good job.  I used to do that as well with VMware Fusion--just reset the clock.  But I got tired of that and so installed Linux and VMware Server instead ;-)  And hey, as long as you wish to play by "the rules", might as well make the rules remotely easy to play by, i.e., GPL.

edit: Actually that's not entirely true.  I'm not so cheap that I wouldn't buy Fusion.  It's actually a pretty snazzy product and was a great way to run Linux with much less hassle than on bare metal.  But the reality is that I came to the cruel (and forehead-slapping) realization that by buying a macbook, I was not reducing my "vendor lock-in woes" (from Vista), but doubling it.  Hence the switch to Linux.  In hindsight, I would have bought a more generic notebook with twice the ram for cheaper, and saved some headaches.  

And now that Leopard is out, my decision is doubly confirmed--I'll be $&%dammed if I'm going to pay $130 to upgrade my OS for a small handful of new features, when I just bought the notebook a couple of months ago!  At least with Windows XP, they gave you a practically new OS with more new features than OS X upgrade, with each service pack (which of course the company has committed - indirectly - to stop doing).  Plus, I just upgraded to Gutsy, which cost $0.

---

