---
title: "Ubuntu won't load after login"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by CitroenC4 on 2007-02-09
Hi 

I am having trouble with Ubuntu loading. I have installed it on a couple of computers with the Live CD and had no problems. I tried to boot the LiveCd on this computer and it would load up to the screen with the X and then the spining loading symbol but would then just sit at a brown screen and not load. I thought I would try to use the ALT install CD and the installation went fine, it loads up to the login screen, enter the login details and then after that is just goes to a brown screen. I have checked it is not the date problem, I tried both the on board video card and an old voodoo card yet it still the same thing so I don't think its a video issue. Any ideas? BTW the computer in question is a PIII with 512mb ram and is a dual boot with Windows XP.

---

### Post by riven0 on 2007-02-09
This happened to me once before, but it was my own fault. Try doing this. When you get to the login screen, go to Sessions >> Failsafe Terminal. Then login if you have to and type this:

> sudo apt-get install --reinstall linux-image-2.6.17-10-generic linux-headers-2.6.17-10-generic

Then try restarting.

---

### Post by CitroenC4 on 2007-02-12
OK I tried that, but I went CTRL-ALT-F1 and then did that and the linux image reinstalled command, restarted but I am still have the same problem. Anyone got any ideas as to where to look next?

---

