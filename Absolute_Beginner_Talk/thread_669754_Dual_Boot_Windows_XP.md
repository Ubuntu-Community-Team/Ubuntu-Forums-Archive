---
title: "Dual Boot Windows XP"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-16
I'm sure this is asked a million times over, but I can't search very easily at the moment, as I've killed all of my bandwidth.  I've got 100gb of free space on my hdd, and i want to stick windows xp on there.
Couple of questions though
A) what is a good size to make my windows partition if i want to put some games on there
B)Is it easier to dualboot windows xp on a ubuntu box than to stick linux on a windows box?
C) Is there a guide someone can link so i don't end up killing my entire drive like the last time i tried to dual boot
D) Any other precaution i should take before installing?

---

### Post by buntunub on 2008-01-16
> **jordank said:**
> I'm sure this is asked a million times ove


You are correct with your assumption. Check UbuntuWiki section or Community Docs. Those have not failed me even one time with any question about Ubuntu I ever had.

---

### Post by Cypher on 2008-01-16
If you've already got Linux installed and have the free space for XP installation, know that you can safely install XP to the free space, but once XP installs itself it will blow GRUB away and put it's bootloader in place.

This isn't a big issue, as getting GRUB back is documented pretty nicely. However, you'll have to manually add XP to the GRUB menu to boot into it.

On the other hand, if you install XP first and then install Linux, it will not only install GRUB but also make the option to boot into XP very easily.

So all depends on what you have right now..

---

### Post by melopsittacus on 2008-01-16
Hi Cypher, I suggest you should back up any data you have before performing the installation (but I think that is quite obvious). And be careful if your XP is not bundled together with SP2: in this case it might not handle too big hard drives correctly (that is, those larger than 130GB), and see your hard drive as a single 130GB unpartitioned one.

---

### Post by zipperback on 2008-01-16
> **jordank said:**
> I'm sure this is asked a million times over, but I can't search very easily at the moment, as I've killed all of my bandwidth.  I've got 100gb of free space on my hdd, and i want to stick windows xp on there.
Couple of questions though
A) what is a good size to make my windows partition if i want to put some games on there
B)Is it easier to dualboot windows xp on a ubuntu box than to stick linux on a windows box?
C) Is there a guide someone can link so i don't end up killing my entire drive like the last time i tried to dual boot
D) Any other precaution i should take before installing?


Here you go.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

