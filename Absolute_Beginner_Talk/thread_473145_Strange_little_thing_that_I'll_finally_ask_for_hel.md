---
title: "Strange little thing that I'll finally ask for help with"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-06-13
After I boot my laptop and log into Gnome everything works fine.  But if I click on "Applications" and go into "Accessories" or whatever the application icons are not there and the system seems to hang for a few seconds before icons appear and I can select an app.  Seems really odd, like it's looking up all the application icons every time the machine is booted.

Not a grave emergency, but if somebody happens to know how to stop/fix this I'd be appreciative.

---

### Post by Inxsible on 2007-06-13
do you have beryl installed ? Maybe its beryl loading up which refreshes the desktop and screen because it takes over as the window manager

---

### Post by Shazaam on 2007-06-13
How much memory do you have in the laptop?

---

### Post by Atomic Dog on 2007-06-14
Sorry for the delay.  Work got crazy.

No Beryl
No Compiz (desktop effects are off)
2 GB  ram, core2Duo,  Ubuntu is not taxing the system at all.

It's just an annoyance.  Did it from the first time it booted.  It only does it the first time I go into the menu after a startup.

---

### Post by sailor2001 on 2007-06-14
[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)   this will speed you up

---

### Post by Atomic Dog on 2007-06-14
Good article, but this is a fresh install from a few weeks ago and I have hardly installed anything on top of the base install.  I'll just deal with it I guess.

---

### Post by mcduck on 2007-06-15
> **Atomic Dog said:**
> After I boot my laptop and log into Gnome everything works fine.  But if I click on "Applications" and go into "Accessories" or whatever the application icons are not there and the system seems to hang for a few seconds before icons appear and I can select an app.  Seems really odd, like it's looking up all the application icons every time the machine is booted.

Not a grave emergency, but if somebody happens to know how to stop/fix this I'd be appreciative.

That's exactly what it's doing. The images need to be loaded from disk into memory before they can be shown to you. Of course this could be done while loading the desktop instead of loading them when you open the menu first time..

---

