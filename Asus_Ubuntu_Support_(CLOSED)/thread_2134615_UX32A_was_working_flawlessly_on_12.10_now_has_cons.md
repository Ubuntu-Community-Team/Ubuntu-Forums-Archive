---
title: "UX32A was working flawlessly on 12.10 now has constant error messages."
date: 2013-04-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by infernozx on 2013-04-11
I've got an Asus Ultrabook, the UX32A, and when I originally got this ultrabook we worked around many of the issues that it had on 12.04, it was all fixed, and the 12.10 release worked flawlessly out of the box.

Last week I ran a system update as usual, and it asked for a reboot. Once it came back from the reboot, I continually get "GFX Error" popups and if I go into the system settings, and "about" section, it says the Graphics card and Drivers are "unknown."

I've made no changes to the laptop since installing 12.10.

On boot it throws the error, and then it throws them every 1, then 5, then 15, then maybe every 6 hours after that. I'm fairly certain it was one of the recent updates that has done it.

I've pushed the bug out through the built in bug reporting feature, but I'm not sure where I need to go to follow that up. Can someone point me towards that? Or get me going on how to provide more information to get this fixed up. I'd hade to see whatever update has just gone through get pushed into 13.04, and ruin the experience for other Zenbook owners.

---

### Post by aeolibus on 2013-04-15
FYI : 

There is a confirmed graphics related bug in the latest Kernel 3.5.0.27.

On my Asus K 93 SV it even causes the bootprocess to hang. 

For the time being you can select the previous kernel in Grub : 3.5.0.26 



[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1167114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1167114)

---

