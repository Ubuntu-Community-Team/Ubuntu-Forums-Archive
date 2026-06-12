---
title: "Thinking of trying out Edgy, need help w/ partitions"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by jeffrey.mezic on 2006-11-12
Goal: 
I'd like to try out Edgy (KUbuntu since I haven't tried KDE yet), but I've heard a lot of people are reporting that upgrading from the command line (gksu "update-manager -c") isn't so hot. So, I figured I'd make a separate partition for Edgy.

Current Setup:
I have a partition for windows, ubuntu, and a swap. (See the attached screen shot.)

Plan:
[LIST=1]
[*]I'm going to first set up a partition for kubuntu using gparted, by taking 5 or so gigs from the ubuntu partition. Quick question: it seems like I need to unmount the partition containing ubuntu before resizing(shrinking) it, is that correct? Can I do that even while I'm in ubuntu?
[*]Second, I'm going to download and create a CD for kubuntu 6.10 using Gnomebaked.
[*]Third, I'm going to install it and use the same swap partition for kubuntu as I do for ubuntu (this will work too, right?).
[/LIST]

Will this all work? Any ideas of doing it a different way? I suppose I could try to do a dist-upgrade, but if possible I'd perfer not to lose my current ubuntu setup.

Thanks!

---

### Post by bodhi.zazen on 2006-11-12
Looks good excpet step 1. You can not do this if you ar eruing from HD. Just e-boot from the live cd and you should be good t go.

---

### Post by jeffrey.mezic on 2006-11-12
Awesome. Thanks for the quick reply :)

---

