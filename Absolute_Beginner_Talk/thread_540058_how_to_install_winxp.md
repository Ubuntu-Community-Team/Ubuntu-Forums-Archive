---
title: "how to install winxp?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by -=TH*SO=- on 2007-09-01
after the install of ubuntu?
I have just 1 hard drive 250 GB! :KS

---

### Post by -=TH*SO=- on 2007-09-01
somtngone?

---

### Post by wolfen69 on 2007-09-01
install xp first, then ubuntu.

---

### Post by -=TH*SO=- on 2007-09-01
thank you :)

---

### Post by gshyland on 2007-09-01
Yes, install XP then Ubuntu. You need 3 or 4 partitions, here's my suggestion:

0: WinXP
1: swap (small, 2-4 gigs)
2: Ubuntu
3 (optional): smallish FAT32 volume that both XP and Ubuntu can write (to share files between OS's)

I put the swap partition in front of Ubuntu to hopefully improve performance (shorter seeks, not having to seek all the way to the end of the disk to reach the swap partition.)

...I just started using Linux this week and I'm already giving advice, haha. My install went very smooth...until I tried to repartition. I hope this saves you the trouble of repartitioning after install.

---

### Post by anaconda on 2007-09-01
Yeah.. it can be done. It is easiest if you have some unpartitioned space, or a partition that you are ready to sacrifice to XP.

Just remember that when you install XP it will overwrite your ubuntu bootmanager (GRUB), but that can be restored with the liveCD after installinx XP. 

It should be easy to find instructions about restoring GRUB after installing XP.

and "wolfen69" is right it is easiest if you install XP first.

---

### Post by seshomaru samma on 2007-09-01
1. run gparted from the live cd
2. create a new FAT32 partition
3. boot from XP and install XP
4. restore Grub ([howto]("http://ubuntuforums.org/showthread.php?t=224351"))

---

