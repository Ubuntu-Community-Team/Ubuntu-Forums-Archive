---
title: "waking system from sleep"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Jeffa on 2007-04-16
Hello all, 

I'm running Ubuntu 6.10 on an Asus P5W DH (More specs [here]("http://ubuntuforums.org/showthread.php?t=390401"))

Everything was working fine, but yesterday i hit the "standby" button on my keyboard, and they system went into sleep mode. Now it won't wake. I've tried rebooting, but the sytem hangs on the boot screen. I can hit "delete" to try and enter the bios, but the system hangs on the next screen. I've tried popping in the live CD hoping to boot from it, but it won't boot. I can't get to anything, the bios, a login screen nothing.

anyone have any ideas as to what may have happened, and more importantly how I can fix it?

Many thanks.

---

### Post by Jeffa on 2007-04-16
Well, problem solved. I thought it might be a memory module (despite the fact that i ran a memory test and it came up clean, and the systems has been running stable for a couple of weeks now) But anyway, i pulled one of the memory sticks out, and the system booted normally. So I swapped sticks, putting the other one in and pulling the first out, and the system booted normally. Then, for shits and giggles, I put them both back in and the system booted normally. 

I don't know why that worked, but it did.

---

### Post by RapMan on 2007-04-16
I can confirm exactly the same problem after hibernating, the system hangs on the boot screen, before grub menu, so it makes no sense to insert live boot cd. 
For me helped to switch-off power supply and switch it on again (so not only power off and on on the case, but direct on the power supply. So if you don't have switch on the power supply, you have to unplug the cable and plug it again).
My BIOS version is 1901.
Any solution for EE 6.10? How it is with FF 7.04? There are lot of other problems, so maybe it makes no sense to ask...

---

### Post by Jeffa on 2007-04-17
Switching the power supply off then back on is probably what really fixed my system. When i was swapping the RAM, i turned the power supply off and unplugged it.

---

