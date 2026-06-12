---
title: "Boot Manager - Help"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by swedeman on 2008-01-28
Have just Installed a third HD on my Dual booting Windows system.

Currently I have Vista Home Premium (X86) as my first Boot Choice.
And Windows XP as my second choice.

Have just Install UBUNTU 7.10 on this 3rd HD and on restart it boots up into Vista desktop.

Going to MY COMPUTER the 3rd HD is not shown.

Now what I believe I have to do is to Install a new Boot Manager system which is capable
of booting to UBUNTU on the 3rd HD

Any suggestions Please

PS have only had UBUNTU Installed for a few days on another system and I think its really great! MUCH BETTER THAN WINDOWS!!!!

---

### Post by dstew on 2008-01-28
> Currently I have Vista Home Premium (X86) as my first Boot Choice.
And Windows XP as my second choice.
Are you using the Vista boot manager program?

---

### Post by iris-n on 2008-01-28
I haven't quite understood your problem.

Is ubuntu loading fine?

Do you want to view the ubuntu HD from your Vista install?
That's not possible, windows can't read ext3.

If you want to share files between the systems, i guess the easiest way would be to create a NTFS partition in your ubuntu HD.

---

### Post by smurphy_it on 2008-01-28
As long as your computer can see the 3rd hard drive (to confirm it is working) you will be fine.  In XP (don't know Vista) right click my computer, choose manage, then click Disk Management.  Verify that your 3d hard drive is in the list.  If it is, then you are set.

Next just boot off of the CD, install ubuntu 7.10 to the 3rd hard drive, and install the Grub boot manager (part of the the install). that will give you the options for booting to Linux.

PS.  If you already have ubuntu installed, you will need to install the grub boot manager to get that going.  If that's the case, leave a message here for more instructions.

---

### Post by philinux on 2008-01-28
> **iris-n said:**
> 
Do you want to view the ubuntu HD from your Vista install?
That's not possible, windows can't read ext3.

If you want to share files between the systems, i guess the easiest way would be to create a NTFS partition in your ubuntu HD.


Native windows cant see ext file system but you can with this.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bumanie on 2008-01-28
During the install of ubuntu did you get the message that grub had recognised xp and vista on the other drives? Usually, grub recognises other OSes and then will ask you whether you widh to import any settings. Once installed gurb gives you the choice of which OS you wish to boot.
If you go into disc management on vista (seeing it boots), does your third drive show up as healthy  but an unknown file type? (or wording similar). This is a bit of a guess, but I suspect grub may not have installed properly.

---

