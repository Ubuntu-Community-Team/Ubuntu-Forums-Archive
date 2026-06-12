---
title: "ubuntu on duel boot with xppro very slow to start"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by eric-g on 2008-03-10
i've just installed 7.10 on my fujitsu n3520 laptop as a duel boot with xp pro. it runs very well, everything works!  just these 2 problems maybe somebody knows why?; 1st; starting up takes almost 2 minutes (or, "an eternity"); ubuntu is sometimes aware of sda1 (windows partition) and sometimes not (shows or does not show sda1 under "computer"). the single hard drive is partitioned like this; sda1, 50 gigs, windows ntfs; sda5, 2 gigs, swap; sda6, 28 gigs, /.  i did used the "advanced"  button on the last installation window to install grub to /dev/sda6.  any opinions?

---

### Post by sayakb on 2008-03-10
> **eric-g said:**
> i've just installed 7.10 on my fujitsu n3520 laptop as a duel boot with xp pro. it runs very well, everything works!  just these 2 problems maybe somebody knows why?; 1st; starting up takes almost 2 minutes (or, "an eternity"); ubuntu is sometimes aware of sda1 (windows partition) and sometimes not (shows or does not show sda1 under "computer"). the single hard drive is partitioned like this; sda1, 50 gigs, windows ntfs; sda5, 2 gigs, swap; sda6, 28 gigs, /.  i did used the "advanced"  button on the last installation window to install grub to /dev/sda6.  any opinions?

Disable unneeded startup entries from System->Preferences->Sessions.
Also, Compiz needs some time to load. Disable compiz to furthur speed up your startup by going to System->Preferences->Visual Effects and select None.
Also, do you properly shut down your computer after using XP. You might need to add a force mount option in case of an improper shut down, or otherwise in the fstab entries.

---

