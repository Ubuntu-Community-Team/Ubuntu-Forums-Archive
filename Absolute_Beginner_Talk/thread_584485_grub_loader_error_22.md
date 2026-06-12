---
title: "grub loader error 22"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by tiger07 on 2007-10-21
Hey I have question and quite literally am scared for my computer, but I installed linux on a partition earlier and then decided to delete the partition.  Now when i boot the computer up it sends me to a error screen.  I believe that the grub loader has jacked my computer up.  I have vista and no boot disc, it came preinstalled.  Help please!

---

### Post by thelocust on 2007-10-21
GRUB rewrites your MBR which tell the computer where to boot the os from so since you deleted your linux partition that it is still trying to boot from your pretty well screwed. I don't know how to fix this for just have vista it's real easy if you want linux back. I am sure there is a way I just don't know about it.

---

### Post by thelocust on 2007-10-21
Do you just want to run vista or dual boot or go all linux?

---

### Post by tiger07 on 2007-10-21
well obviously i want to run vista, but the problem is getting back into vista in the first place.  Do you think that if i ran an xp boot disc at startup and ran a fixboot or boot mbr command, do you think it would fix it?

---

### Post by tiger07 on 2007-10-21
can i safely partition my hard drive using the ubuntu installation without losing all of my data in vista?

---

### Post by sandysandy on 2007-10-21
> **tiger07 said:**
> Hey I have question and quite literally am scared for my computer, but I installed linux on a partition earlier and then decided to delete the partition.  Now when i boot the computer up it sends me to a error screen.  I believe that the grub loader has jacked my computer up.  I have vista and no boot disc, it came preinstalled.  Help please!

Hi
U can try to restore MBR by using the Win disc. If u do not have the disc (as preinstalled) u can go to vista homepage and follow instructions to restore MBR.

Before trying to install linux again, as and when u restore MBR, it may be a good idea to have backup of your MBR on a removable media (floppy, CD etc) to help booting. 

There is also an utility called Super Grub which i learnt on this forum only that helps u to boot. This requires a bootable CD to be made of Super Grub.

regards

---

### Post by tiger07 on 2007-10-21
i try it out, thanks!

---

