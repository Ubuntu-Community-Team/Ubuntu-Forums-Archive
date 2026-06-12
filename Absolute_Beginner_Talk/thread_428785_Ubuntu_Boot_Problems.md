---
title: "Ubuntu Boot Problems"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by dz0004455 on 2007-04-30
I have had Ubuntu 6.06 LTS installed for a while, and I decided that I would try out making a Linux from scratch system, but I already had four partitions(Windows, Windows Recovery, Ubuntu, Linux Swap).  So I deleted my Swap Space after resizing it to 4gb and created an extended partition to contain Swap space and the LFS system and now when I try to boot Ubuntu, The splash Screen shows up, but it sits on the "Mounting root filesystem" part and never advances.  If i can't figure out a solution, or someone can help me. I'm going to back up my valuable data from my Ubuntu live disk and reinstall Ubuntu.  I have already had to do that 3 or 4 times, and I spent about a week getting beryl set up, and I really don't want to go through all of that again.  Plaese help!!!

---

### Post by laidback on 2007-04-30
Sounds to me as though you need to read up on Grub:-

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There are 50+ pages here, not all will apply. I have a printed copy which I find much easier.

The section:-

How to boot Linux from Grub's CLI 

seems relevant. 

Happy Reading, it's worth the time even if it doesn't solve your problem.

---

### Post by dz0004455 on 2007-04-30
thanks alot,  I fixed the problem by reinstalling grub.

---

### Post by laidback on 2007-05-01
I'm so pleased. These problems appear impossible until you realise how to solve them. I've only just started looking into grub myself after a similar problem. Really handy program.

Kindest regards

Laidback

---

