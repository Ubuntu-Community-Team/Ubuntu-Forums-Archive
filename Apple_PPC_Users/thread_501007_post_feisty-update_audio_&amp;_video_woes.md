---
title: "post feisty-update audio &amp; video woes"
date: 2007-07-14
forum: Apple PPC Users
---

### Post by Lovewig on 2007-07-14
hi,
i upgraded via apt about a week ago, and have yet to get any software to play video files.
i've read a lot of related posts reguarding this issue, even tried the fix where you comment out the wacom lines in the xorg.conf. i've done all the things at the PowerPCFAQ url, and was wondering if anyone can point me into a direction as how to fix this. :confused:

cat /proc/cpuinfo

processor       : 0
cpu             : 750FX
temperature     : 1-13 C (uncalibrated)
clock           : 400.000000MHz
revision        : 2.2 (pvr 7000 0202)
bogomips        : 28.30
timebase        : 24835245
machine         : PowerBook4,3
motherboard     : PowerBook4,3 MacRISC2 MacRISC Power Macintosh
detected as     : 257 (iBook 2 rev. 2)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld

uname -a

Linux lovewig 2.6.15-26-powerpc #1 Fri Sep 8 19:51:33 UTC 2006 ppc GNU/Linux


thanks!

---

### Post by stmiller on 2007-07-14
You'll have to give us some more detail. Video/audio from the browser? Have you installed all the good/bad/ugly gstreamer codecs? Search Add/Remove programs for good, bad, and ugly (separately) and install those gstreamer pacakges.

---

### Post by Lovewig on 2007-07-15
All i did was update to feisty. then neither vlc nor mplayer would play video. "Illegal instruction" errors. the only * new* thing installed were the the Medibuntu codecs recommended from [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) - which i thought might fix my problem, but didn't. VLC worked fine with edgy. the upgrade to feisty went smoothly, just realized i can't watch videos.

---

### Post by stmiller on 2007-07-15
By more detail, I mean of what exactly you are doing when video doesn't play. Are you trying to play from a browser? Or just a video from your hard disc? If it is a webpage can you give us a link so we can test?

Type VLC in a terminal, then open a video file. And give the output from the terminal here so we can see what is not working.

---

### Post by gnomeza on 2007-08-28
Sounds like this bug: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/104630](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/104630)

I have the same problem and have been using gxine in the meantime.

---

