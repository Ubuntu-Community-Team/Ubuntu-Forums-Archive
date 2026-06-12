---
title: "monitoring winxp from ubuntu"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by r3mu on 2006-11-30
hi!

I was wondering if it is possible to monitor and remote control winxp using ubuntu..i mean, u can see what's the winxp user is doing and u can control their pc by shutting it down, reboot.etc..it's like remote controlling the target's pc..in LAN environment..

any idea..:confused:

---

### Post by qamelian on 2006-11-30
> **r3mu said:**
> hi!

I was wondering if it is possible to monitor and remote control winxp using ubuntu..i mean, u can see what's the winxp user is doing and u can control their pc by shutting it down, reboot.etc..it's like remote controlling the target's pc..in LAN environment..

any idea..:confused:

You can do this with any of the VNC (Virtual Network Computing) applications. Do a search in Synaptic and you should find a few options.

---

### Post by r3mu on 2006-11-30
thanx..
but, do i need to install something on the remote computer?..i found a few vnc in synaptic but i'm not sure whether it's compatible with XP or not..can u suggest the best one?

---

### Post by psyke83 on 2006-12-06
Hi,

tsclient or krdc, and rdesktop (the backend) will allow you to connect via Remote Desktop Connection (Terminal Services) on XP, once you configure the XP machine to accent Remote Desktop connections (right click My Computer, it's in one of the tabs there). You should have tsclient installed with ubuntu, and krdc with kubuntu, but rdesktop needs to be installed via synaptic/apt.

Good luck.

---

