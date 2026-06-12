---
title: "Can't boot Vista"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by tormodfoss on 2007-04-18
I have just installed Ubuntu and thought that I could boot Vista from Grub. The Grub menu however does not show Vista and when I try to boot Vista from the cd I don't get anywhere. Any solutions?

---

### Post by LaRoza on 2007-04-18
How did you install Ubuntu? 

Did you:

1. Defrag Vista First.
2. Use Vista to create a partition for Ubuntu.
3. Install Ubuntu to that partition.

If you did not do these steps you will have a problem.

---

### Post by tormodfoss on 2007-04-18
I didn't defrag Vista, but I created a new partition for Ubuntu which I installed it in. Are there any ways I can get Vista to work again without doing fundamental changes?

---

### Post by seetho on 2007-04-18
> **tormodfoss said:**
> The Grub menu however does not show Vista and when I try to boot Vista from the cd I don't get anywhere.

This is a good thing! ;)  I had my first look at Vista earlier today when a friend asked me to look into some networking problem he was having in the office... and I must say that I'm glad  I switched to Ubuntu.

---

### Post by seetho on 2007-04-18
> **tormodfoss said:**
> I created a new partition for Ubuntu which I installed it in.

How did you create this partition?

---

### Post by freebird54 on 2007-04-18
I hope we don't have a problem here.  It is safer to resize partitions from the Vista side when using Vista as the Win part of a dual boot.  Please tell us how you set this up??

---

### Post by tormodfoss on 2007-04-18
I reduced the main HD used by Vista to let Ubuntu find the space to use when I installed it. I didn't understand the technicals at the Ubuntu installations to good so was happy when the installation started.

---

### Post by LaRoza on 2007-04-18
Did you resize the partition with Vista?

Does Ubuntu work fine?

---

### Post by seetho on 2007-04-18
If you resized the Vista partition during the Ubuntu installation then you may have trashed it.

---

### Post by tormodfoss on 2007-04-18
I did all the partitoning in Vista. And Ubuntu works excellent. Are there any ways I can do the whole set up of the partitions and formating of the HD again as there's no information on the HD I need?

---

### Post by LaRoza on 2007-04-18
Losing Vista, in itself, is probably a good thing. 

Do you have a compelling reason to use Vista?

If you want to reclaim your hard drive, you could reinstall Ubuntu over the entire drive.

If you need Vista too, you will most likely have to reinstall it and then reinstall Ubuntu.

You cannot alter the windows partition with Ubuntu, you could with previous versions of windows.

---

### Post by tonycheese on 2007-04-18
hi, i haven't actually dual-booted ubuntu yet, as i'm waiting for the next build, but i've been looking at dual-booting and apparently vista makes it difficult, so you have to manually go and change grub to let you find vista. here's a really good guide i found:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
you want to look about halfway down the page, it tells you exactly what to type in.
hope that works... i haven't actually used it yet =D

---

### Post by rickggreen on 2007-04-18
Just to throw in my 2 cents.....

If you have a fast machine, reformat everything to Ubuntu. and then run Vista in a virtual machine.

If you are newb, I realize that what I am telling you is going to require a lot of learning, but in the end you will be much better off. The satisfaction I get from showing my friends my machine, running Beryl btw with multiple windows, multiple monitors (CRT and TV) just blows them out of the water and has converted most of them from Vista/XP to Ubuntu BTW (the one that hasn't switched yet has trouble brewing a pot of coffee.........)

I was building this machine for Vista, waiting for it's release I decide to try Linux, I have spent a number of all nighters playing and tweaking in the last 2 months, but I am not sorry, and you won't be either.

For a really good dual booting tutorial  

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I am telling you this, because I have just gone through the process, there is almost too much info on the web and in the forums. Read everything first, make sure that the info your are getting matches your distro especially video drivers, (If you have a NVIDIA, read the LINUX readme before you do anything, and be prepared to reimstall if you screw up).

I am NOT trying to frighten you, because like I have said before, in the end you'll have on heck of a system even if it is not bleeding edge hardware. 

Ask questions

---

### Post by speedsterdm on 2007-04-18
> **tonycheese said:**
> hi, i haven't actually dual-booted ubuntu yet, as i'm waiting for the next build, but i've been looking at dual-booting and apparently vista makes it difficult, so you have to manually go and change grub to let you find vista. here's a really good guide i found:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
you want to look about halfway down the page, it tells you exactly what to type in.
hope that works... i haven't actually used it yet =D

Was just about to post this but Tony beat me to it. This should work although I have not done it yet, it has been used with much success by others. I am planning on doing the same when I get my laptop in about 2 weeks so tell us how it goes.

---

