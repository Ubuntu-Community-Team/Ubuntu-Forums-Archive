---
title: "Is it possible to fix my Ubuntu install with the Live CD?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-20
I was fooling around with my graphics drivers and uninstalled them (oops!)

Is there any way to fix Ubuntu with it?  Everytime it starts up it says Server X cannot start or something because of the graphics card I'd assume.

Do I have to do a fresh install?

---

### Post by AriciU on 2007-06-20
Try to do "dpkg-reconfigure xserver-xorg"

---

### Post by the.phantom on 2007-06-21
I am not a expert
but i kinda messed up mine 
i had to boot into rescue
and then enter as admin
the above command
now you might want to read this before you start that !!!

i found it and it sure helped me out !
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

(note if "ok" was not colored i would hit "esc" and the rest was done with "enter"
as some pages are just info and others are for the data

---

### Post by w4ett on 2007-06-21
Fron the command line type:

sudo dpkg-reconfigure xserver-xorg

this will bring up the semi-graphical interface to configure your xserver

up and down arrows move the cursor

spacebar marks selections

enter confirms selections.

This will allow you to select your GFX driver and screen resolutions and refresh rates.

---

