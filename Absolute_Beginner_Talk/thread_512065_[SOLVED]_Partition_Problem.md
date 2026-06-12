---
title: "[SOLVED] Partition Problem"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by DonBucknall on 2007-07-28
Hello,

I searched the forum but could find a solution for this problem.

I wanted to swap my xp(on 500GB) to my ubuntu(on 80GB) so I swapped xp round and wanted a fresh install of ubuntu.
I insert the live cd and press install, when I come to the partition part I choose manually.
I've got 500GB free so I want to use the full drive, I create partition 256MB for swap --> no problem, 30GB for '/' (root) --> ok, then I try to do remaining 470Gb for /home and when I press ok it will show up as a +/- 40Gb drive and still say 430GB is free.

What am I doing wrong?

Thanks,

Don

---

### Post by specker on 2007-07-28
When it comes to partitioning like you are trying to do, I personally have always had better luck using the alternate install cd.

---

### Post by DonBucknall on 2007-07-28
Thanks for quick reply, but isn't there a solution for it?
At the moment I'm visiting my uncle in the UK and he is in the middle of nowhere with really slow internet. I just waited 5 hours to download it.
I would use the alternate cd if I was at home but can't at the moment.
Is it possible to use knoppix and use cfdisk to pre-make the partitions and will ubuntu pick them up automatically?

Thanks,

Don

---

### Post by pistcivet on 2007-07-28
> **DonBucknall said:**
> Thanks for quick reply, but isn't there a solution for it?
At the moment I'm visiting my uncle in the UK and he is in the middle of nowhere with really slow internet. I just waited 5 hours to download it.
I would use the alternate cd if I was at home but can't at the moment.
Is it possible to use knoppix and use cfdisk to pre-make the partitions and will ubuntu pick them up automatically?

Thanks,

Don

I think that's an excellent idea.
I always use a live cd to partition (usually the Gparted live cd)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by laidback on 2007-07-28
Why not let Ubuntu install itself with the smaller partitions then when you get back home use Gparted live CD, or Ubuntu Live cd which has Gparted on it, to reorganise your hdd.

---

### Post by Duck2006 on 2007-07-28
You can try it with a Gparted CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by DonBucknall on 2007-07-29
Thanks for all replies and help. But booting in knoppix and pre-setting the partitions worked.
Ubuntu is now fully installed.

Thanks,

Don

---

