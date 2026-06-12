---
title: "[SOLVED] Second harddrive not showing after wireless card installation."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by 10player on 2008-01-12
Well, as the title says, my second harddrive isn't showing anymore. It was working perfectly before I setup a rt61/rt2561 wireless card. I've checked if maybe I disconnected a cable when I put the wireless card in but everything was fine. I did a fdisk -l which shows this:

```
sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4701    37760751   83  Linux
/dev/hda2            4702        4865     1317330    5  Extended
/dev/hda5            4702        4865     1317298+  82  Linux swap / Solaris

```

If, there is anything else I should post to help clarify anything please let me know. I'd like to get it working again.

---

### Post by mkoyle on 2008-01-12
Does the drive show up in your bios?  This doesn't really sound like something that should happen after installing a PCI card.  If you really think it is the card, you might try shifting it from one slot to another but I feel fairly certain this is not the problem.

If the drive is not in your bios, there is something very basic wrong - disconnected power, disconnected cables, jumper settings...  If none of those are the problem (really, remove them and put them all back on; I hate when something like this is the problem), look at the following idea:

If both drives are on the same cable, pull out a live CD and swap the drives (change from master to slave and vice-versa).  If the same drive doesn't show up you probably had a freak harddrive failure.  If the other one disappears, then I'm a monkey's uncle unless there is something wrong with a connection or a cable.

Good luck!  You are clearly capable of fixing this.  Post back questions or notes about the end result.

--Matthew

---

### Post by 10player on 2008-01-12
Thanks for the help mkoyle. I checked the bios, then shutdown and unpugged and replugged the hdds. Now it works. Haha, should been the first thing I did before I posted. Sorry for the bother and thanks again mkoyle.

---

### Post by mkoyle on 2008-01-12
Very welcome.  I've doubted the cables would be the problem before and they almost always get me :) glad it's fixed.

--Matthew

---

