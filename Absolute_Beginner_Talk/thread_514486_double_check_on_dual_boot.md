---
title: "double check on dual boot"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ryanfx on 2007-07-31
Hey guys - just double checking that this is the correct way to do things as I dont have my windows disk on me, so if I mess this up I will be out of a windows install for about 2 months lol


I have a 160 GB HD with one huge NTFS partition.

All I need to do is boot into ubuntu, click install, select the first option about resizing the partition and use the free space and drag it to wherever I desire?  I'm assuming that this is a non-destructive partition resize and that it will automatically make the other partitions needed and handle grub?  Thanks for the help!

-Ryan

---

### Post by p_quarles on 2007-07-31
It's *supposed *to be non-destructive, but that doesn't always mean it is. For best results, you should defragment the hard drive twice before attempting to resize the partition. You should also make sure all of your files are backed up to a safe place. [EDIT: Just to clarify -- Gparted is a great partition manager, and very safe; there's just no such thing as a completely safe partition resizing operation]

Other than that, you've got it right. 

One thing, though: if you're running Windows Vista, it's much better to use its built-in partition partition manager to free up space for Ubuntu. Gparted doesn't seem to work very well with Vista.

---

### Post by xc3RnbFO8P on 2007-07-31
How much space are you going to use for Ubuntu?
Do you have windows installed?
If so, have defrag it?

---

### Post by ryanfx on 2007-07-31
How much space should I allow for ubuntu?  It's going to be a pretty bare bones system with only minimal applications installed.

Also, if I want a minimal install, I'm assuming I want that slider towards the higher % side?

I'll go run my defrag now!

---

### Post by p_quarles on 2007-07-31
I've seen 10 gigs quoted as the minimum recommended space for Ubuntu. The OS and basic apps don't take up a whole lot of space, so unless you plan on saving a lot of large files on this partition, 10 gigs should be adequate.

---

### Post by xc3RnbFO8P on 2007-07-31
It is up to you, min 20 gb. If you want try some programs.
Slide to the right.

---

### Post by MQMike on 2007-07-31
You dual boot should go OK the way you have it – Windows on the first partition, Ubuntu after it.

Just in case, 2 references:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)


And if you are dual booting with Vista, here’s another good one:

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

