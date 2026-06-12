---
title: "WiFi After Suspend"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Dxh on 2007-11-27
I've noticed that in every new distro (Ubuntu 7.10, Fedora 7 & 8, openSUSE 10), after my laptop wakes up from suspension, it can no longer connect (wirelessly) to the internet. I've tried everything I can think of, but it won't allow me to even see what networks are in the area. I've tried restarting the network session, nm-tool shows nothing abnormal... I just can't figure it out. Does anyone have any ideas as to why? Is it a driver issue? (I'm using madwifi with an atheros 5005, I believe)

Any ideas would be appreciated.

---

### Post by raycosm on 2007-11-27
I get the exact same thing with an Atheros AR5007EG using ndiswrapper. Upon returning from a standby or hibernate, wireless never works, and nm-applet always says I'm connected, but doesn't respond when I try to connect to another wireless network. Never been able to figure it out, hopefully someone else knows a fix.

---

