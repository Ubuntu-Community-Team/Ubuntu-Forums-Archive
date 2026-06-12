---
title: "NDISWrapper problems in new Feisty install."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-04-20
I installed Feisty today, a clean install, not an upgrade. I set up NDISWrapper as I usually did with Dapper and Edgy (for my D-Link DWL-G132 USB Dongle) and I've run into some troubles.

Here's what I did to install:

```
ndiswrapper -i NetA5AGU.inf
ndiswrapper -d 2003:3A05 NetA5AGU.inf
ndiswrapper -m
modprobe ndiswrapper
```

And this worked. I have internet access. Until I reboot. In which case, unless I unplug the wireless device and reconnect it upon GDM, it does not work at all. I get some ugly errors after the splash screen, and Ubuntu won't recognize the card until I do the reboot/unplug trick.

Not a HUGE problem, but pretty irritating. 

Any ideas?

---

### Post by sunexplodes on 2007-04-20
Anybody?

---

### Post by tl3000 on 2007-04-20
For my application for a Netgear WG511v1 with netwg511.inf, after the steps you've described I also needed to:

```
sudo gedit /etc/modules

```
Add the following line to the end of the file and save:

```
ndiswrapper

```

Re-start, and this worked for me with Edgy.  However, Fiesty is not working anymore now...

---

### Post by sunexplodes on 2007-04-21
Yeah, I did that also, forgot about that. Thanks though.

---

### Post by sunexplodes on 2007-08-09
For anyone searching, here's a brief rundown of exactly how easy this thing is to install in feisty, once you know what you're doing:

Get newest version of NetA5AGU.inf driver from D-Link website. 

sudo aptitude install ndiswrapper-common ndiswrapper-utils
cd /wherever/neta5agu/is
sudo ndiswrapper -i NetA5AGU.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

The only caveat is that you need to unplug the usb adapter when you reboot, as it seems to only work if you've plugged it in after the GDM.

---

