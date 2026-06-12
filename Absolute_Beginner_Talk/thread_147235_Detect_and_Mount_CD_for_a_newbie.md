---
title: "Detect and Mount CD for a newbie"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by SamTheShaman on 2006-03-19
I am trying out linux for the first time. I have a 1.7Ghz 756 Ram on an ASRock GEpro-m2. A 120 Gig hard drive runs windows. I installed 10 gig hard drive and reformated Fat32 for Linux. I have a CD burner and a DVD burner.
HL-DT-ST CD-RW GCE-8525B abd NU DVDRW DDW-082.

When I tried to install Ubuntu the first couple of screens were alright but I came upon No common CD Rom drive was detected.. Load CD from floppy?

I did no. Not load floppy, and tried some choices available. But it just stalls, blue screen.

I tried Ubuntu Live and had the same problem.

Any ideas
:-k

---

### Post by celloandy on 2006-03-20
Perhaps you should try the other drive, since you have two?  Also, just for reference, Ubuntu won't work natively on Fat32, but rather uses ext3 by default (you may be able to use reiserfs, too, but I'm not sure).  The Ubuntu installer will take care of partitioning and formatting, though, so you don't need to worry about that step.

Andrew

---

### Post by Brunellus on 2006-03-20
[QUOTE=celloandy]Perhaps you should try the other drive, since you have two?  Also, just for reference, Ubuntu won't work natively on Fat32, but rather uses ext3 by default (you may be able to use reiserfs, too, but I'm not sure).  The Ubuntu installer will take care of partitioning and formatting, though, so you don't need to worry about that step.

Andrew[/QUOTE]
ubuntu runs on reiserfs.  I can confirm this;  I run reiser3.

---

### Post by SamTheShaman on 2006-03-20
[QUOTE=celloandy]Perhaps you should try the other drive, since you have two?  Also, just for reference, Ubuntu won't work natively on Fat32, but rather uses ext3 by default (you may be able to use reiserfs, too, but I'm not sure).  The Ubuntu installer will take care of partitioning and formatting, though, so you don't need to worry about that step.

Andrew[/QUOTE]

Yes I did try the other drive before posting. Same problem.
No common CD Rom drive detected.
:cry:

---

