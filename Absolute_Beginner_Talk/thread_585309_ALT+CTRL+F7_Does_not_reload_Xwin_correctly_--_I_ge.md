---
title: "ALT+CTRL+F7 Does not reload Xwin correctly -- I get a black screen"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by gogetadbl on 2007-10-21
Hello,
When I press ALT+CTRL+F1 then back into ALT+CTRL+F7 and then repeat the process once more, I end up at a black screen. At this black screen, my cursor moves around like normal but no keys work.  I tried CTRL+ESC, the power button, ALT+CTRL+F1 through F10 but nothing does anything.  Also when my computer is sleep/display turns off after idle time, I get the same thing. What can I do to be able to boot back into xwindows properly?

Specs:
Laptop
Ubuntu Feisty Fawn with all updates
Intel Core Duo T2250
1GB RAM
Nvidia 7600 to go

---

### Post by FuturePilot on 2007-10-21
It's a bug with the Nvidia Driver. Make sure you don't have SyncToVblank enabled in Compiz if you are using Compiz.

---

### Post by gogetadbl on 2007-10-21
I haven't done anything with Compiz.  Is it on by default?  I don't see it anywhere on my system.  

Do I just wait for a new nVidia driver or is there a site where I can download the driver and try them all out?

---

### Post by arsenic23 on 2007-10-21
There has been no fix from Nvidia for this, so you won't find a driver that will fix the problem.

Compiz is on by default in Gusty, you can find its preferences under Preferences > Desktop Effects.

I beleive there is also a package you can install that is a better config for Compiz then the one provided, but I forget the name.

---

### Post by gogetadbl on 2007-10-21
> **arsenic23 said:**
> There has been no fix from Nvidia for this, so you won't find a driver that will fix the problem.

Compiz is on by default in Gusty, you can find its preferences under Preferences > Desktop Effects.

I beleive there is also a package you can install that is a better config for Compiz then the one provided, but I forget the name.

Oh I see.  Is there anywhere I can get more information about the problem, like the nVidia forums perhaps?  Seems like there might be some 3rd party drivers that had a fix since this effects anyone using the xwindows + nVidia combo.

---

