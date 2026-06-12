---
title: "problem about mplayer and alsa"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by javeer on 2007-10-07
:( SOS

I compile and install mplayer successfully following this guide:[http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)
but i can't find alsa sound driver in its preferences 

however when i check the system with command : 
 cat /proc/asound/version
I got :
 "  Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC). ", seems i already installed alsa.

see my attachment.

somebody can help me? sometimes i must use alsa in mplayer!
thanks!

---

### Post by javeer on 2007-10-07
anyone knows? thanks!

---

### Post by shirilover on 2007-10-07
You may wish to install libasound2-dev and libsdl1.2-dev before compiling mplayer to get more audio driver choices.

---

### Post by javeer on 2007-10-08
thanks very much!

---

