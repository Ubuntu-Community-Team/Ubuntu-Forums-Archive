---
title: "[SOLVED] backup hassles"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by GabeForPrez on 2007-07-27
Hello Ubuntu World!

[INDENT]
i was interested, and installed Ubuntu onto a partition in my 160gb drive.
it was doing well, and i was getting quite comfortable with it.
then i began to realize that i would want more than the 10 gigs i designated for it.
i was hoping to just grow the partition, so that i could have 50 gigs for Ubuntu now.

i load up the boot cd,  launch GParted, but found that the start point of the partition cannot be moved, and i had made the partition at the far right.

i looked around, and found that i could just make a complete backup of the system, as instructed in [this guide by Heliode]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup.tgz").

next, i made another partition that was the size i wanted, and i installed a fresh Ubuntu.
i wanted to extract my backup over the new Ubuntu.

after i did, though it would not boot properly. i would think its because of a change in the partition name [from hda1 to hda3][/INDENT]

[B]so, what i need to know is how to extract the backup.tgz so that it does work correctly.

particularly, how can i format the Ubuntu partition, and then extract the backup, and then what is left to do so that it works correctly [in reference to the GRUB menu.lst's pointing to a partition that doesn't exist.][/B]

Thanks in advance.

---

### Post by ddrichardson on 2007-07-28
What happens if you follow the restore part of the above tutorial then re-install Grub?

---

### Post by rillip on 2007-07-28
Here is what I would do.

Partition the way you want.  Install.  Back up the /boot/gurb/menu.lst that's placed by default.  From the live cd, extract it the tar.  Change the /boot/grub/menu.lst to reflect the new drive.  Reboot.  If you still get errors, post the errors here.

---

### Post by GabeForPrez on 2007-07-30
alright, i'm back.

> **rillip said:**
> Here is what I would do.

Partition the way you want.  Install.  Back up the /boot/gurb/menu.lst that's placed by default.  From the live cd, extract it the tar.  Change the /boot/grub/menu.lst to reflect the new drive.  Reboot.  If you still get errors, post the errors here.

i'm reinstalling currently.

alright, it seems to have gone over smoothly. one minor note: i can't connect to the internet through my wireless card. its usually automatically detected, by my previous Ubuntus and the live cd. for the most part, this is resolved, and will be marked accordingly when i get that up and running.

but presently, maybe i missed something in not recreating the directories listed in the guide.
d'oh.
help is greatly appreciated.

---

