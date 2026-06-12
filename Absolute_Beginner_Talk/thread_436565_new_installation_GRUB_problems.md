---
title: "new installation GRUB problems"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by FirebornX on 2007-05-07
I've never tried Linux of any flavor before but I heard you could install it on an external drive so I thought that would be a perfect way to start off with it.
I have plenty of experience with windows, so I partitioned my external USB HDD with a 25GB slice and formatted it with ext3, partitioned a 2GB slice for swap. Installed Ubuntu on the 25GB partition.
That all came off without a hitch, but then I tried rebooting. GRUB threw an error, I believe it was error 21 and it didn't get past that point.
I've tried reinstalling Ubuntu but nothing changed.
I tried fixmbr from the windows recovery console, but now when it boots it just says GRUB... no other text.

I need two things, priority 1 is getting windows to boot, I have some work that I just can't do in Linux.
priority 2 is getting both systems playing nice with each other.

Thanks in advance!

---

### Post by nightskywind83 on 2007-05-08
From the recovery console, you may also need to run fixboot, although in all honesty fixmbr should overwrite GRUB with the Windows bootloader.

It might be advisable to use an internal hard drive.  But googling lead me to this page, it may help you:

[http://five.pairlist.net/pipermail/linux-laptop/2004-November/001488.html](http://five.pairlist.net/pipermail/linux-laptop/2004-November/001488.html)

Let us know how things work out.

---

### Post by FirebornX on 2007-05-08
fixboot completely trashed my windows install...
everything is corrupted on my C: partition...
going to have to revert to my backup, and I think I'm going to put off linux for now... I don't have enough space on my internal drive for it, and I can't risk all my data.
Luckily my other partitions are still in tact. So reinstall windows, restore settings and all is well.

too bad to, I liked linux. Thanks for your help though, at least I know I can't install it on an external drive heh.

---

### Post by jiminycricket on 2007-05-08
DOes your BIOS support booting from an external drive?  I've read that Linux _can_ be installed to an external drive.  What MBR was GRUB installed to, the external or internal drive?

Sorry about your trashed partition.

---

### Post by FirebornX on 2007-05-08
Yes my BIOS supports booting from a "USB HDD"

GRUB was installed to the internal drive, I think... it did replace the windows loader after all.

from the installation wizard it looked like GRUB was installed to (hd0), but I'm not sure which HD that is.

BTW I'm used to reinstalling windows, everything is back up and running thanks to a good back up from last week.

I think I'm willing to give it another go. I'll just need to be better prepared this time.

Can someone help me wade through this new world of Linux and get it up and running on my external drive?

---

