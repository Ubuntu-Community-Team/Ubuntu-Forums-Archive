---
title: "Start without keyboard"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by DenOK on 2007-04-27
Hi!
Sorry, if this has already been discussed, then just give me a link. :) 

Kubuntu Fiesty, on PC, with PS/2 keyboard, just installed.

I need to start my system w/o keyboard, so I made changes to BIOS to stop on all errors except the keyboard, setup passwordless and automatic login in KDE's Login Manager and finally put a symlink to Klavier (KDE's onscreen keyboard)  in /.kde/Autostart

But when starting my system after removing keyboard, I can get no further than seeing cross mouse pointer just for a sec (this time KDM is supposed to start) and then black screen, nothing more  :(

Is it really a problem to run without keyboard?

---

### Post by DenOK on 2007-04-27
And is it alright to plug/unplug PS/2  keyboards/mice while PC is turned on?

I think that it will do no harm to the hardware/ports, but I've never heard of PS/2 as supporting hot swap.

---

### Post by DenOK on 2007-04-27
Tryied to cooment InputDevice     "Generic Keyboard" in xorg.conf that didn't help. (

---

### Post by Cypher on 2007-04-27
I was going to suggest you modify the X config to remove the Input, but you've already done that.

Also, I don't know if PS2 is hot-pluggable like USB is. I don't believe it is..

---

### Post by freebird54 on 2007-04-27
I don't think that PS/2 is sophisticated enough to know whether it has been hot-plugged or not.  Certainly I have swapped keyboards on the fly before without a problem - and added one after stop on keyboard errors, and been able to hit F1 to continue.  I don't know how you tell gdm/kdm to stop looking though!

---

### Post by DenOK on 2007-04-27
Thanks!
But is it so hard to run Linux w/o keybrd?!

---

### Post by freebird54 on 2007-04-27
No idea - sorry.  Never tried.  It can't be TOO difficault or it wouldn't make much of a server!  Perhaps that might be the way to track down some info - look into apache settings or some such.

Sorry not to know more about this - but someone may be along....

---

### Post by compmodder26 on 2007-04-27
I'm running a headless/keyboardless/mouseless server at home.  However, I'm not running with a gui so I can't tell you how that would affect it.

---

