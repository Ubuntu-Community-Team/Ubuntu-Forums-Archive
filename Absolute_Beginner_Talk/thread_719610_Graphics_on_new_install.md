---
title: "Graphics on new install"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by gbnogkfs on 2008-03-09
let's say I'm a Real Rookie here... and don't even know if this is the right place to ask...

Men: IT IS REALLY HARD TO INSTALL THIS UBUNTU THING....

... ok, rants aside, I just installed Ubuntu 7.10 and I have problem with monitor setting and/or graphic display:

the problem is I am not even sure what the problem is, but:

1) during boot, I cannot see the startup screen (the one with the Ubuntu logo and the loading bar), as my monitor refuses to display saying "please set input to 1280x1024 60MHz"...

...it is a minor quirk, but how do I manage to get it work? (NOTE: during the installation or live CD sessions, there is not such a problem!)

2) even after loading the graphic is... hum... disturbing: characters are sometimes hard to read, icons appear too bright (no: changing the monitor hardware rendering doesn't work), the borders of text boxes are sometimes invisible, and even images appear in bad colors: just too bright.

also: i cannot activate desktop visual effects: it may be that i have a too old card, but don't sincerely think so.

is this a problem with monitor or graphic card install? note: i don't know how to let the system know which card or monitor I have, for they are not among the options in the graphics settings

note number 2: movies seems to play reasonably well, but possibly somewhat altered as well.

I have a ATI Radeon X200 card and a HP vs17 flat monitor: they're not the top, but I wouldn't throw them away...

---

### Post by Belak on 2008-03-09
Try this:
Go to system->Administration->Restricted Drivers Manager
It may ask for your password.
Check and see if your card shows up there. If it does, check the box to enable it and it should automatically download what it needs.

EDIT:
You may have to restart for the changes to work. In linux, though, this is usually only required if you're doing a major upgrade (kernal upgrade), or installing certain drivers. You very rarely have to restart, but this is a case where you should.

---

### Post by drewcoon on 2008-03-09
Do you have the drivers for your graphics card set up? Because my computer's graphics look pretty bad too, if I have the driver disabled.

I have an ATI Radeon xpress 200 card and the proprietary driver from the site ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)) works great for me, even with desktop effects.

Hope this helps :)

---

### Post by gbnogkfs on 2008-03-09
> **Belak said:**
> Try this:
Go to system->Administration->Restricted Drivers Manager
It may ask for your password.
Check and see if your card shows up there.


it doesn't

---

### Post by gbnogkfs on 2008-03-09
> **drewcoon said:**
> Do you have the drivers for your graphics card set up? Because my computer's graphics look pretty bad too, if I have the driver disabled.

I have an ATI Radeon xpress 200 card and the proprietary driver from the site ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)) works great for me, even with desktop effects.

Hope this helps :)

I don't have a clue on how to install those drivers: I tried to follow the instructions on that site, but very rarely do instructions on linux work as written...:(

---

### Post by Malta paul on 2008-03-09
As said in previous posts often the default drive my give poor results, I would suggest that you download 'Envy' from: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and use this great program to install the latest driver for your video card. Then goto System>Administration>Restricted Driver Manager, and tick the box for Enable.
Have fun :)

---

### Post by gbnogkfs on 2008-03-09
AT LAST!!!!!!!!

I have been working with envy for hours, and eventually I had to reinstall linux from scratch (totally blanck screen at login), and THEN Envy did work properly and the drivers do work.

now i remain with the other (minor) problem of the startup screen (the one with the Ubuntu logo & loading bar) which I can't see:

my monitor says to "set input to 1280x1024 60MHz" which I frankly don't know how to do.

I will start another thread...

---

