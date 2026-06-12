---
title: "I made a mess of my partitions..."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-10-14
Ok, in my infinite wisdom, I decided that the easiest way to backup and restore my system would be to make a partition of equal size to my main partition and just copy and paste my main partition to it as a back up. I later found out that this didn't work at all, and now I'm in a pickle. 
My hard drive is cut up like this
Sda1 -> Windows, gparted says it's flagged as boot.
Sda2 -> Previous copy partition, now main partition
Sda3 -> Previous main partition
Sda4 -> Extended, swap/ etc.

I tried to 'fix' things, and it didn't work very well (at all). 
What I tried to do is have my computer use Sda3's grub and boot only into Sda3, without ever looking at Sda2.  
Now my computer uses Sda3's grub and boots into Sda2. I used this for awhile and just ignored the problem, now I want it fixed, but I want it to boot into Sda2's grub, and from there load Sda2. I copied Sda3's grub into Sda2, so the only thing I need now is to have my computer start by loading Sda2's grub. Any advice?

---

### Post by logos34 on 2007-10-14
Reinstall Grub pointing to sda2:

> [B]sudo grub
find /boot/grub/stage1[/B]
(it should output 'hd0,1' and 'hd0,2'.  Enter the former--aka sda2--on next line.)
[B]root (hd0,1)
setup (hd0)
quit[/B]

---

