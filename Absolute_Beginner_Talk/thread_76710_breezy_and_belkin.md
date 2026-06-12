---
title: "breezy and belkin"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by mcdamage on 2005-10-15
Hi new to linux and have installed breezy on to my laptop which is sweet but although in device manager i can see my belkin pcmcia card there,s no lights on the card and ive no idea what im to do, i hand simply mepis installed but could not get get ndswrapper to in stall the windows driver correctly. i was told that ubuntu was more friendly.

---

### Post by bluefrog on 2005-10-15
I assume your pcmcia card is a network card.
Just in case, open the networking tool (system/administration menu). Is an interface for your pcmcia card listed here by chance? If yes configure it, activate it and you're done.

Otherwise here's a guide for ndiswrapper

using synaptic package manager (system/administration menu), install ndiswrapper-utils  (no need for network connection, it's in the cdrom).

Eject ubuntu cdrom and load your card's driver cd

open a terminal (applications/accessories menu)

sudo mkdir /lib/windrivers
sudo cp /media/cdrom/<path to your inf and sys files> /lib/windrivers
sudo ndiswrapper -i /lib/windrivers/*.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

_Explanation by example for my Belkin usb F5D7050 wifi card:_

sudo mkdir /lib/windrivers   [COLOR="Magenta"]## give whatever name to the folder where you're going to put the windows drivers in, use /home if you like.[/COLOR]

[COLOR="Magenta"]## copy the inf files and sys files[/COLOR]
sudo cp /media/cdrom/Driver/*.inf /lib/windrivers
sudo cp /media/cdrom/Driver/*.sys /lib/windrivers

[COLOR="Magenta"]##install the driver[/COLOR]
sudo ndiswrapper -i /lib/windrivers/*.inf

[COLOR="Magenta"]##to have the driver loaded at boot[/COLOR]
sudo ndiswrapper -m

[COLOR="Magenta"]##to load the driver now, for u to configure your card afterwards[/COLOR]
sudo modprobe ndiswrapper

open the networking tool (system/administration menu). Hopefully your connection will be listed here as it was for me after those simple manipulations.
Configure it and activate it.

---

