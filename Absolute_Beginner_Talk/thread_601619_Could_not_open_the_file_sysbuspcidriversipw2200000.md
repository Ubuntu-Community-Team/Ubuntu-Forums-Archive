---
title: "Could not open the file /sys/bus/pci/drivers/ipw2200/0000:02:01.0/led....w hy?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by IWood on 2007-11-03
I used

> gksudo nautilus

to browse. I was  able to open and save changes to rc.local, but couldn't even open /sys/bus/pci/drivers/ipw2200/0000:02:01.0/led.

I'm trying to restore Fn+F2 on/off functionality to the LED on my Dell 700m, and from what I've gathered on some older threads, I need to get into this file and muck about with it...

thanx

IW

---

### Post by mrvertigo on 2007-11-03
ooh, opening nautilus as root or sudo is BAD JUJU try something like > gksudo gedit then open /sys/bus/pci/drivers/ipw2200/0000:02:01.0/led     by browsing directories its a long shot but give it a try

---

### Post by IWood on 2007-11-03
Heh. That's why I'm using this spare computer here...so I have complete freedom to do the Bad Juju and then explode.

Anyway: no dice on that suggestion. I mean, I'm **supposed** to be able to edit such files, right?

---

