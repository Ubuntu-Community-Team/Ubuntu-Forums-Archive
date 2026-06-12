---
title: "need help badly, using win xp to post this (uninstalling ati drivers)"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by gamerzl on 2007-02-13
how is it possible to uninstall the ati drivers from the console, because i made an error in setting up the resolution on my laptop, and it will not let me log in to the gui, and i'm sitting int he console atm. 

i've tried changing the resolution with the following

aticonfig --resolution=0,1024x768

it gives me

Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etcX11/xorg.conf' failed. Bad file descriptor.

and i've spent all day today installing the latest kubuntu for the amdx64. 

i've gotten everything to work (i love that the wifi is default now, since i last used beezy)

---

### Post by sardion on 2007-02-13
From the console type:

sudo dpkg-reconfigure -plow xserver-xorg

That should let you rebuild your xorg.conf by asking you a series of questions (all thru text mode).

---

### Post by gamerzl on 2007-02-13
i went through and it gave me this...

xserver-xorg protinst warning:overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20070213222924

---

### Post by gamerzl on 2007-02-13
its working again, thank you

---

### Post by sardion on 2007-02-13
That's what we're here for.  Your welcome.

---

### Post by gamerzl on 2007-02-13
also what would be the best resolution for my screen, and how would i set it because the gui settings don't let me change anything even within administrator mode

i'm running an ati x1600, with a 15.4 inch widescreen lcd laptop display

---

