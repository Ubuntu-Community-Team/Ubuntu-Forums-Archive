---
title: "KDE Problems...again"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-03
I couldn't find my other tread so I'm going to have to start a new one
after some system updates on a fresh install of kubuntu, when I restart it will go to just a terminal and sit there,here's what's on the screen

Starting K Display Manager: kdm.
Starting Common Unix Printing systm: cupsd
Startng powernowd...
Starting avahi mDNS/DNS-SD Daemon avahi-daemon
Starting DHCP D-Bus daemon dhcdbd
Starting bluetooth services
starting anc(h)ronistic Cron Anacron
Starting defferred execution schedler atd
Strting periodic cmmand scheduler rond
Checking attery state...
Running local boot scripts (/etc.rc.local
_

they all say OK at the end and then the command just sits blinking on the bottom with nothing happening

What i thought was wierd was right before the upgrade the computer asked me if I wanted to upgrade my OS.  Problem is that I already have gutsy, but I said yes anyway.

---

### Post by OffAxis on 2007-12-03
> the command just sits blinking on the bottom with nothing happening
Is it at a command prompt or is it just frozen?

---

### Post by OffAxis on 2007-12-03
Can you restart the X-server with
```
startx
```

or 
CTRL+ALT+Backspace?

---

