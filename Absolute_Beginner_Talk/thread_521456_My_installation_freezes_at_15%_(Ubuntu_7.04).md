---
title: "My installation freezes at 15% (Ubuntu 7.04)"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by yuzyin on 2007-08-09
Ubuntu 7.04 Freezes after repartioning the drive. At 15% mouse becomes slover then freezes. What should I do? Live desktop looks working. I have tried to repartition myself and use whole disk. Problem still continues. 

I have AMD semron 2200+ 
256 ram, and everything is onboard. A basic computer

---

### Post by Dr Small on 2007-08-09
To me, it sounds like it ram. I forget how much Ubuntu is required to run/install, I think it is much less than what you have, but I have 1024 MBs of RAM and it was a slow install for me.

Dr Small

---

### Post by oilchangeguy on 2007-08-09
> **yuzyin said:**
> Ubuntu 7.04 Freezes after repartioning the drive. At 15% mouse becomes slover then freezes. What should I do? Live desktop looks working. I have tried to repartition myself and use whole disk. Problem still continues. 

I have AMD semron 2200+ 
256 ram, and everything is onboard. A basic computer

if you've only got 256mb of ram, and onboard video, you're losing some ram to video. you must have at least 256mb's to devote to the computer, or the install won't work.

---

### Post by Nervouswreck on 2007-08-09
It sounds like RAM but probably isn't. 256 is a little low, but should do the job even devoting part to video, which it might not be depending on what kind of card you have (which is what BTW?).
You'll probably want more RAM once you start editing photos and stuff so it's wrthwhile to upgrade to 512 anyway, and it might help with the partitioning

---

### Post by oilchangeguy on 2007-08-09
> **Nervouswreck said:**
> It sounds like RAM but probably isn't unless you have a rediculously low amount. It would help if we knew your drive speed, RAM and clock speed. Those are what come to my mind first b/c im kinda hardware oriented.

not really needed. the issue is, the users low amount of ram, combined with onboard video. the user needs to upgrade the ram, or use another version, like xubuntu.

---

### Post by dptxp on 2007-08-09
Download GParted, make live CD, boot with it, and make a 1 GB (512 MB to 2 GB) SWAP partition preferably at end of your HDD. You shall not be able to change it during installation as the Live CD shall use it.

That is exactly what I did with 256 MB RAM Sempron 2500+ , remember that 64 MB out of 256 goes to video, you got just 192 MB left.

It runs fine after that.

---

### Post by macuto on 2007-08-09
In my situation was a ram issue. It got stuck at 40%. I made a memtest86 boot disk checked the memory and found a faulty module.

---

### Post by normalfish on 2007-08-12
I had this problem and have 256MB RAM and I found a useful workaround. I'd tried a number of times to install Feisty and each time it got stuck until I did this:

I'm dualbooting XP and Feisty. I booted into XP, used a partition manager to create a swap partition then installed feisty with no problem at all. If you're dualbooting I would strongly suggest you do this before installing Linux.

---

### Post by Nervouswreck on 2007-08-13
> not really needed. the issue is, the users low amount of ram, combined with onboard video

You'd be surprised. In a home-built machine you could have an old or improperly cared for HD that is so slow its write speed can cause problems.

---

