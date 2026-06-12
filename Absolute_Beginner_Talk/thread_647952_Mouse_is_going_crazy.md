---
title: "Mouse is going crazy"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by jerome1232 on 2007-12-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Okay i am getting a strange problem, my mouse will randomly start flying across my screen and seems to rapidly right/left click, opening programs and etc... it's a wireless Logitech optical mouse ps/2, i use a mousepad and this is only started recently, my first thought was hardware and well it's wireless so i moved my base away from emi etc.. and i still get the problem. I then booted into a live cd and i don't have the problem there. could this even be a software problem? it seems to be a really random problem i can go 30 mins or so without an episode the all of sudden it's happening every couple of minutes. 

i'm using 7.10 x86_64 kernel 2.6.22-14-generic

from a dmesg output after a short spasm

[  226.259702] psmouse.c: bad data from KBC - timeout bad parity
[  228.304959] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[  260.835188] psmouse.c: bad data from KBC - timeout bad parity
[  265.708362] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[  397.655080] psmouse.c: bad data from KBC - timeout bad parity
[  398.912537] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[  447.626163] psmouse.c: bad data from KBC - timeout bad parity
[  451.480259] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization,
throwing 3 bytes away.

i'm going to buy a wired optical mouse here just to see if it allivates the problem i've noticed some pervious posts and a refrence to a bug reported but it was an older kernel and they were all running feisty, nothing in the posts was really helpfull

---

### Post by jerome1232 on 2007-12-23
Ok I went out and got the new mouse, it's a wired optical mouse with a usb port and a ps/2 adapter, i  plugged it into the ps/2 port and 4 minutes later spasm, i put it in the usb port and nothing for 30 minutes now

---

