---
title: "Switching wireless cards?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ajkirchner on 2007-11-24
Running Gutsy on Thinkpad T43 with ipw2200 wireless card

I have an Airlink 101 PCMCIA wireless card (Atheros based chipset) that I would like to try out instead of my ipw2200 card

I was wondering how I disable my ipw2200 card and use my Airlink card for wireless use

Thanks

---

### Post by Dr Small on 2007-11-24
Power the machine off, Unplug the AC Power Cord, remove the side panel.
Remove the old IPW2200 Wireless Card and plug in your New Airlink Wireless Card.

---

### Post by hardyn on 2007-11-24
BUT ASK YOURSELF!

do i have the right tools?
do i have the aptitude?

and BE REALLY CAREFUL WITH THE ANTENNA LEADS, THEY BREAK REALLY EASILY!

---

### Post by ajkirchner on 2007-11-24
Sorry I was unclear...the ipw2200 card is internal and my Airlink plugs into the Cardbus slot on the side of my laptop

I simply want to turn off the ipw2200 (I could disable it in windows) and have my Airlink card take over my wireless needs...

Thanks

---

### Post by ajkirchner on 2007-11-24
I don't want to replace the ipw2200 i just want to disable it and use an external card - is this possible in Ubuntu?

---

### Post by hardyn on 2007-11-25
remove the driver.

which is umod? or modprobe -u  or something to that effect (the inverse of modprobe), google it, i have only had to do it once.

cheers.

---

### Post by Majorix on 2007-11-25
You could blacklist the ipw2200 driver by doing this:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and adding "blacklist ipw2200" somewhere in that file on a line by itself.

There was a tee command that appended a string given to the end of the file but I don't remember its usage :KS

---

