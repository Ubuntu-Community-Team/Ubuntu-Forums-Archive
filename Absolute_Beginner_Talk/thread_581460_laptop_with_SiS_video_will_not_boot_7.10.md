---
title: "laptop with SiS video will not boot 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by patjr on 2007-10-19
I have a laptop with SiS chips in it and video, so it says when digging around. I had/have 7.04 installed on a dual boot and it works well or did until I messed it up. I am trying to put 7.10 on the laptop but I can't get it to boot. I stops at an error 

[ 121.308000] powernow-k8: failing targ, change pending bit set

there are about 7 more of these different numbers before this one comes on. There is also a note about a "pending bit very stuck" 

any tip appreciated.

Thank You,
Pat Jr.

---

### Post by ddrichardson on 2007-10-20
It's a known [bug,]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96592") but reported upstream as it's a kernel bug. I'd suggest staying with 7.04 and reporting that the bug is back in whichever kernel version 7.10 is using.

---

### Post by patjr on 2007-10-20
Thank You for your reply.

Well since I hosed my system I thought I would give something different a try. I dl a copy of Vector. Very cool but easy NOT. It does "feel" quicker then 7.04 was but then without some kind of test you really can't say. Installing as a little trickier, ubuntu and Vector should try and install fedora some time, much more though with more options.

I was wrong about my video in my laptop, it's via not SiS but it didn't make any difference. I tried Live CD for fedora 7 - chocked, fedora 8 T3 - chocked, Sabyon - would boot the disk, ubuntu 7.10 - chocked, when I tried Vector is didn't want to boot either but some how I got the driver to switch to vesa and it came up. Installing it was challenging and I still have an extra 100MB partition that was suppose to have been my /boot but some how didn't get that way. I had to dig around and install grub while running off the CD to get the hd install to boot. It end up being one of those long trips where you end up some place and can't remember exactly how you got there.

Guess I'll run Vector until the kinks, if ever, get worked out of the current issues with new distros and my sneaking suspicions of the latest Xorg.

best of luck to all, this just shown why Linux is so great, YOU HAVE A CHOICE
Pat Jr.

---

