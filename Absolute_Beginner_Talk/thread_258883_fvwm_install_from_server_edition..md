---
title: "fvwm install from server edition."
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2006-09-16
like the title says, im hoping to install fvwm from the server edition of ubuntu (the graphical install cd wasnt working with this optiplex g1).

after some fiddling with sources.list, i was able to install fvwm, but since i get fatal x errors on the display manager startup, im guessing theres something wrong with my X server. i think since i clean installed, ive "installed" gdm, fvwm, xserver-xorg (and all their dependencies).

what am i missing?

thanks!

willi

---

### Post by ThomasAdam on 2006-10-13
> **xolot1 said:**
> like the title says, im hoping to install fvwm from the server edition of ubuntu (the graphical install cd wasnt working with this optiplex g1).

after some fiddling with sources.list, i was able to install fvwm, but since i get fatal x errors on the display manager startup, im guessing theres something wrong with my X server. i think since i clean installed, ive "installed" gdm, fvwm, xserver-xorg (and all their dependencies).

what am i missing?

The exact error messages you get, for a start, is what *we're* missing.

I suspect X11 isn't running when the call to FVWM is made, hence the errors, but without anything concrete, that's just speculation.

-- Thomas Adam

---

### Post by shunthemask on 2006-10-14
try this:
```
sudo aptitude install x-window-system-core
```
worked for me when i compiled fluxbox over a server install.

---

