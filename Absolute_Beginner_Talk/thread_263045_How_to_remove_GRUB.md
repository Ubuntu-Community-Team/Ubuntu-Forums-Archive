---
title: "How to remove GRUB?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-09-22
Ok basically what I'm wanting to do is remove grub so I can load just into windows, since I found my 40 Gigabyte harddrive (using 20 gig at the moment and it just isnt cutting it ;)), so I rebooted my computer to enter into windows (Having not used it for a couple of days now), and WindowsXP wont load in either safe or normal mode!
All i want to do is install Ubuntu to the 40 gig, but i cant take out the 20gig because it says that it has error17 with grub!

Basically:
Harddrive 1: 250 gig (Windows)
Harddrive 2(currently using, don't want to use anymore): 20gig
Harddrive 3(want to switch to):40 gig

Any advice? :-&

---

### Post by divague on 2006-09-22
boot from your winXP cd and when it loads select the R option i think is recovery console or something like that, put fixmbr, that will remove grub

---

### Post by Josh1 on 2006-09-22
> **divague said:**
> boot from your winXP cd and when it loads select the R option i think is recovery console or something like that, put fixmbr, that will remove grub

Ok, I will try that now, i was just looking for my WindowsXP Disk.
Thanks,
Josh

---

### Post by bulldog on 2006-09-22
If you put an hdd extra in your computer or your partitions ara changed GRUB doesn't understand.

Alter your GRUB to be sure that your windows boot partition is the right one.

Removing GRUB can be simply done with your windows install cd.

Boot your windows cd into recovery console and type fixboot which should recover your windows boot and remove GRUB.

If this is a no go,try fixmbr instead,it's a little trickier,but it never harmed me.

---

