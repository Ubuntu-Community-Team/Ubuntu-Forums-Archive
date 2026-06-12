---
title: "Joli OS boot issue (not Joli specific)"
date: 2012-09-24
forum: Any Other OS
---

### Post by metarune on 2012-09-24
Hi,

Installing Joli OS on an Asus 900 with two hdds: 4GB (sda) + 16GB (sdb).

Install worked fine on sda, not enough room to operate properly so installed on sdb - worked fine but after restarting post Asus-specific updates, boots to flashing cursor only if sdb is top in boot order or 'Geom Error' if trying sda.

Edited flags for sdb partition to make bootable, re-installed Joli, still the same issue. Tried every conceivable boot order, no change. So I figure either issues with boot sector or grub-related issues. Even to a noob like me it's clear the OS is there but it's not being found for some reason.

Noobiness = unsure of where to proceed from here. Is grub in the wrong place, is there an issue with the boot sector, how do I diagnose and if so how to fix?

I can boot into Joli via USB to probe things but I'm working in the dark, any tips or pointers much appreciated.

Thank you!

---

