---
title: "boot problems installing ubuntu studio"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by mike sumner on 2007-06-08
Hi Folks, this is my first post here.  I am trying to install ubuntu studio but it failed with lots of error msgs, so I installed 7.04 so I could upgrade, and although it seemed to install ok and the cdrom popped out when it finished, it did not install grub. I already have grub on another partition which I could use, but I cant seem to find any info that just gives me the entry I need to add to the menu.lst for ubuntu 7.04. which is on sda9.
Cheers, Mike

---

### Post by ronocdh on 2007-06-08
> **mike sumner said:**
> Hi Folks, this is my first post here.  I am trying to install ubuntu studio but it failed with lots of error msgs, so I installed 7.04 so I could upgrade, and although it seemed to install ok and the cdrom popped out when it finished, it did not install grub. I already have grub on another partition which I could use, but I cant seem to find any info that just gives me the entry I need to add to the menu.lst for ubuntu 7.04. which is on sda9.
Cheers, Mike
I also think that installing Feisty Fawn and then upgrading to Studio is a nice way to go. Can you go into more detail about your partition scheme? It seems a bit complicated, seeing as you cited a /dev/sda9. I personally recommend that you wipe what you can and just install Feisty freshly, confirm it's operating well, then upgrade to Studio using the package calls listed [here]("http://ubuntuforums.org/showthread.php?t=442506").

---

### Post by mike sumner on 2007-06-08
hi ronocdh, thanks for the reply, I have 3 other linux partitions, xp and a data partition, so I didn't really want to wipe it. Decided to try reinstalling feisty which worked this time, so i just finished updating to studio and it's excellent! Had to modify the menu.lst so I could boot the other linux's though.
Cheers, Mike.

---

