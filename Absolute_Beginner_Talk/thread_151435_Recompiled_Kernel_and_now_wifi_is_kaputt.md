---
title: "Recompiled Kernel and now wifi is kaputt"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by YuHoo on 2006-03-27
I did a stupid thing. Before fully understanding how my laptop interacts with linux, I recompiled the kernel in hopes of getting hibernation (Standby2 tutorial). Now I can not even get my ieee802.11 to install. I have the ipw2200 wifi built into my Dell XPS 140, the latest firmware 3.0 downloaded (but needs ieee installed first), the ipw2200-1.1.1 driver, and the latest ieee802.11 from sourceforge. I have also tried the previous versions of the firmware (2.4) with the stable release ipw2200-1.1.0 driver. These had the exact same error. I have no proprietary drivers for ATI or nVidia video cards. My wifi is also detected in the gnome device manager in name only, but nothing is installed. I followed the vauge and annoying install methods provided online through intel and more complete ones from this community's wiki that worked last time. Neither have yielded any results. Every time I go to make the ieee file it gives me the error:

grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//include/linux/autoconf.h: No such file or directory

make[1]: Entering directory '/lib/modules/2.6.12-10-386/build
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/2.6.12-10-386/build'

I'm stumped and thinking that I have screwed things up to where I should try a reinstall. I've also tried manually cutting and pasting files, but I think that led to further degredation of the system. I've done build-essential, dist-upgrade, upgrade, and nothing changes. I've also researched how 'make' works and could not find anything that broke it down into a simple tutorial explaining how to use it. 

So my two requests are:
1) Help with the wifi problem
Whether you know how to fix it or not, 
2) Any good tutorial walking through the 'make' process to help me troubleshoot further on my own and future problems with compiling

---

### Post by YuHoo on 2006-03-28
Never mind, I solved the problem with a reinstall and downloading the autoconf utilities

---

