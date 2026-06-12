---
title: "won't switch from metacity prob- even after enabling compositing"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by skaspud on 2007-07-19
i have beryl installed and everything, the lil icon up top and all, but when i try switching from the metacity window manager to beryl, the screen flickers a bit and nothing changes, and it still says it's using metacity window manager.


i got this in terminal...
************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : failed

No composite extension
beryl: No composite extension
............................................................................

i even tried this in my xorg.conf
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

.................................................................................
but it still didn't work...
will somone please help me, this is like the whole reason i got ubuntu...

---

### Post by Armman on 2007-07-19
Did you properly install your graphics driver and have it setup correctly?

---

### Post by skaspud on 2007-07-19
yes, it works perfectly.
i used envy (in case it helps)
i ran a command to check ( i forgot, som1 just told me...)
and i got perfect readouts.
... for the graphics card

---

