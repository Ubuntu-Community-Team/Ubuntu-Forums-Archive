---
title: "Kubuntu Live CD wont boot"
date: 2006-11-18
forum: Apple PPC Users
---

### Post by galvatron1983 on 2006-11-18
Hi guys, 

Ive gone AWOL since joining almost a year ago, been hiding away in Mandriva for a few months. Good distro, software installs are more complex then good ol Ubuntu tho...

Anyways, Ive just downloaded Kubuntu 6.10 Live CD and when I put the disc in the cd drive of my Powerbook G4, and boot from it, it goes through the booting process until eventually just taking me to a terminal command line. Is there any way I can get this to boot into the Kubuntu desktop??

---

### Post by aysiu on 2006-11-18
Can we assume you've verified the integrity of the ISO before burning it?

If so, have you tried typing *startx* or *sudo /etc/init.d/kdm restart* at the command line?

---

### Post by stmiller on 2006-11-18
When the CD boots, press 'TAB' at the boot menu. And pick a 'live' kernel image. One for the G4. If one doesn't work, try the other live image available. I can't remember the options at the top of my head.

---

