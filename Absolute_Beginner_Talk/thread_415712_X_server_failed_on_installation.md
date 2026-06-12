---
title: "X server failed on installation"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bluewagon on 2007-04-20
while trying to install any Ubuntu( ive tried 7.04 and 6.10) i get the error that the X server has faile.. it tells me
Fatal Server error: No screens found
under sudo nano /etc/X11/xorg.conf it has this

selection "screen"
[INDENT]Identifier "Default Screen"[/INDENT]
[INDENT]Device  "Intel Corp. 82845G / GE Chipset Integrated Graphics Device"[/INDENT]
[INDENT]Monitor "776"[/INDENT]
[INDENT]Default Depth 24[/INDENT]

i currently have that onboard graphics card disabled and have a NVDIA GeForce FX 5500
so how can i fix this? enabling my intel graphics?

and another thing, when trying to do
sudo dpkg-reconfigure -phigh -xserver-xorg
i get this error:
[INDENT]Xserver-xorg postint warning: overwriting possibly-customised configuration file; back up in /etc/X11/xorg.conf.(then numbers)[/INDENT]

---

### Post by bluewagon on 2007-04-20
also:
Pentium Celeron processor 2.6ghz
1 gig of ram
one 125 gig seagate hard drive(master with windows)
one 250 gig seagate hard drive (slave with nothing on it, new-just partitioned - putting ubuntu on it)
LCD Monitor1280x1024

---

### Post by bluewagon on 2007-04-20
i enabled my intel grpahics and tried and it no go, does anyone have any idea on how to fix this?

---

