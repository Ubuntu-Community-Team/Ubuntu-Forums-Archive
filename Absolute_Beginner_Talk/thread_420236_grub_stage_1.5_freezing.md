---
title: "grub stage 1.5 freezing"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2007-04-23
im extremely sorry if this has nbeen answered anywhere, there are a lot of threads i found similar but not about the exact same problem,

i reinstalled ubuntu 6.06 server version onto my server, after messing it lal up by playing, but it jsut wont beet now, it freezes at grub stage 1.5 and does nothing, there are no usb devices, in fact all thats connected is the Sata hdd, ps2 keyboard, network cable and the monitor

ive tried everything i could think of but it just refuses to go past that point :( its really annoying, it doesnt give any errors or anything, it just stops dead.

does anyone have any suggestions, please :(

---

### Post by mahy on 2007-04-23
boot the live cd and run the command

grub-install [device]

where [device] is the the name of your master disk drive (the first in boot order).

---

### Post by kgls13349 on 2007-04-23
ah im really sorry, ive figured out the problem, my hdd is a sata, the bios on my board was set for the sata to run as raid, despite only having a single drive, i set it to "ide" mode and its now working fine, i will have to remember that for the future :)

Thanks for the reply its appreciated :)

---

