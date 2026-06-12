---
title: "Making progress!"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by scorpiusmaximus on 2007-10-28
I posted last week in frustration but I now seem to be making some progress. 
I downloaded a fresh iso of Ubuntuv. 7.10 and reinstalled. Ran over to ATI and got the latest driver and followed the very simple Proprietary Linux Driver installer. Smooth, for a change.
I have two monitors on one ATI X1550 card. I am having trouble configuring. The monitors are of two sorts; one is a 15" flat screen, MAG-LXH-WG541, and the other is a 16" Gateway EV-700, not that it really makes a difference.
They are both on (mirrored) and my resolution is finally OK on both. I am trying to make changes via aticonfig so that the secondary is to the right of the primary. 
This is what happens;
me@me-desktop:~$ aticonfig --initial=dual-head --screen-layout=right
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
This is the best I have gotten after struggling with video for weeks. Any help would be greatly appreciated and please be specific. I am a newby.
PS Nothing happens when I click on the ATI Catalyst Control Center in Applications menu.

---

### Post by damotor on 2007-11-02
Why don't you just switch the monitor cables connected to your pc?

---

