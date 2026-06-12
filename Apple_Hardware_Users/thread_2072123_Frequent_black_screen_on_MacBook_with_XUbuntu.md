---
title: "Frequent black screen on MacBook with XUbuntu"
date: 2012-10-17
forum: Apple Hardware Users
---

### Post by etienoo on 2012-10-17
Hi,

My MacBook frequently blocks on a black screen when I'm using it.
Then, I have no other choice to switch it off using the power button (which is not so good for the hardware!).

I couldn't find any command to restart the X server for XUbuntu, so I couldn't try this.
Note that, if the computer "blocks" while I'm listening to music, the music is still going on, and some keyboard commands still work (such as keyboard brightness control, etc.), which let me think this may be a graphic driver / config problem.
(But CTR+Q and similar don't work.)

Furthermore, the problem occurs in particular when many things happen on the screen (e.g., a shell program is looping in a terminal, and printing a lot of information very fast).

The system has been working fine for several months, and the problem is recent, and more and more frequent; it's almost impossible to use the computer more than 15mn, which becomes pretty annoying.

**Hardware**
MacBook Pro 6.2 Mac OS X 10.6.7
2.66GHz Intel Core I7
4GB 1066MHz DDR3 SDRM - 2x2GB

**OS**
XUbuntu 12.04 64 bits
(with Mac OS, just in case…)


Would you have any hints?

Thanks!

---

### Post by etienoo on 2012-10-21
OK, I "solved" the problem by reinstalling the system (actually replacing XUbuntu 12.04 with KUbuntu 12.10).
And everything is fine.

---

### Post by moschops on 2012-11-02
Same problem here with a MacBook Pro 6,2 - the big difference is I'm on Ubuntu 12.10.

I've tried all the supplied drivers - regular Nouveau X org driver, nVidia binary tested, nVidia binary with updates and nVidia binary experimental.

The symptoms are that usually when mousing over the launcher I'll just get a black screen.  There seems to be no way to regain control other than power cycle and there are no crash logs.  

I most often get a crash right after login if I use the launcher - but if I can get apps open by another means or wait a while then the system seems more resilient - today I was able to get it to not crash through a full work day.  On returning home after resuming from suspend it crashed within a few minutes.  After a power cycle it crashed again in less than a minute when I tried to use the launcher.

It's a real shame because otherwise Ubuntu is running quite nicely on this machine (much better than via Parallels which is what I was doing before).

---

