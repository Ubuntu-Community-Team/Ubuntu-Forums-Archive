---
title: "[SOLVED] network manager problems"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by japephillips on 2008-02-22
fourth attempt at ubuntu in 4 weeks - failing again
gone back to 7.04 as more stable and no excessive overheating that i had with 7.10, network manager keeps changing the configuration I set. I want no network, this is stand alone laptop
I want internet connection and have it at present using conexant softmodem and 3rd party drivers for dialup
however, network manager is not stable, keeps altering back to self select 'wired enabled' and 'wireless enabled' whatever i change.
also it disregards my modem settings of muted spkr and even goes to pulse dial sometimes!
it still intermittently decides to dial out after bootup
after suspension (it will not hibernate) it loses the mouse (usb) until it is taken out and reconnected, then it will change the network again to disconnetced (it cannot find the card it syas but then so what? i don't want it to)
if i turn off 'use modem as internet connection', then even if i connect it will not allow evo/fox to connect

can someone run me through the network setup slowly and carefuly please
i need just default softmodem connection by dialup when i want it, not when it decides!

is there an alternative network manager i can download,  how cani turn this one off once and for all and load just a ppp connector, hopefully one with an icon showing if connected?

---

### Post by spiderbatdad on 2008-02-22
yes. look into gnome-ppp in synaptic package manager as an alternative to ppp-config. Disable ppp and eth.

---

### Post by japephillips on 2008-02-23
thanks, as you may recognise this is my fourth attempt at ubuntu. i will be back after trying this within 24 hrs, hopefully to report it working!

---

### Post by japephillips on 2008-02-23
I don't know how to disable ppp and eth
so i uninstalled network manager and a few dependencies it found (from synaptic pm)
then installed gnome-ppp
and - here i am
hopefully it will hold up
THANKS

---

### Post by japephillips on 2008-02-24
its worked ok for a couple of days with this setup
so lets call it SOLVED!

---

