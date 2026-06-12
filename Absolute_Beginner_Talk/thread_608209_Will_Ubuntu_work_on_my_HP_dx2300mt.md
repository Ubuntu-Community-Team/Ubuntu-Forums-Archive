---
title: "Will Ubuntu work on my HP dx2300mt?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Crimmy on 2007-11-09
I'm a 100% n00b to anything GNU/Linux so please forgive! 

I downloaded Ubuntu 7.10 and its running smoothly on a 5 year old compaq Evo D51C. It's a little sluggish with 3D but it works OK. I plan to change to a more beefy graphics card in the future. But I was curious to get it on some newer hardware and MAYBE get good enough to play with Beryl. (someday)

I have a spare HP Compaq dx2300MT that I'd like to try Gutsy on: system specs are:

**HP dx2300 RT841UT Intel Desktop Computer - Intel Pentium 4 641 3.2GHz, 512MB DDR2, 80GB SATA II HDD, SATA DVD-ROM/CD-RW, 10/100Mbps LAN, NO Floppy, **

It came with Windows Vista Business, but I **deleted** the partition in preparation of a Gutsy install. So basically it isn't partitioned anymore. Won't the 64-bit version of Ubuntu format and install on my SATA drive?  Or am I NOT able to install a stable copy of Ubuntu Gutsy on this machine at all?  

My Ubuntu CD didn't seem to boot the PC at all so I'm going to try to create another LiveCD from the .iso file *just in case I screwed up the first time*. In the meantime I have a couple questions. 

1. Can this dx2300mt support Ubuntu?

2. If I need to format this unpartitioned drive should I use Linux boot CD and format it with it?

Thanks!

---

### Post by SunnyRabbiera on 2007-11-09
usually HP's work well with linux.
but make sure you have a version of it that will work with your specs, and it seems you do have a 64 bit version...
this will not work.
download and use the intel x86 version instead.

---

### Post by kevinatkins on 2007-11-09
Hi,

I'd second SunnyRabbiera on this - use the normal 32 bit x86 version of Ubuntu. I'm running an AMD 64 bit processor and I tried the 64 bit Ubuntu, but there are too many compromises (not Ubuntu's fault, mainly stuff like Flash plugins, etc, that are only 32 bit, too much faffing about to make stuff work...)

If you've got an unpartitioned drive, the live installer will cope fine with this and create the necessary partitions during installation.

---

### Post by gn2 on 2007-11-09
Have you tried typing "only-ubiquity" as an additional boot parameter after pressing F6?

This runs the installer from the 7.10 live CD without running a live session.

Definitely get the 32-bit version if you like an easy life.

---

### Post by Crimmy on 2007-11-09
Thank you all for your attention and guidance. I'm off to try the install again!

---

### Post by Crimmy on 2007-11-09
Well SO FAR SO GOOD. When I used the LiveCD, it was creating really strange graphic problems with the display. I let it sit for a while, (I saw the ROM drive spinning) and voila! I was able to install Gutsy. 

I'll be trying to figure out the OS now. Thanks for the pointers.

---

