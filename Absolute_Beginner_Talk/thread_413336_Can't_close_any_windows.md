---
title: "Can't close any windows"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-04-19
I had a few glitches with my upgrade.  A short power failure just as I got to the begin upgrade? screen.  When my power returned, I was told that I had a "custom set up."  from that point on the upgrade went fine.  I don't know if that has anything to do with my following problem or not.  I tried screen effects but I wasn't able to close my windows.  The controls in the upper right hand corner were completely gone.  I turned screen effects off but I still can't close my windows except from my task bar.

Any ideas?

---

### Post by ghowells on 2007-04-19
Sounds like Metacity (the GNOME Window Manager) was closed for the new WM to run (compiz or emerald, not sure which one the desktop effects feature uses) but for some reason the replacement window manager didn't launch, this could be due to any number of reasons (hardware incompatibility, broken software) if this package was installing while you had your power failure it may not be installed correctly.  Have a go at re-installing it (remove then install fresh) the package is called "desktop-effects".  You can do this either via synaptic or using apt-get.  Hope this helps! :)

---

### Post by djen9999 on 2007-04-19
That makes sense.  I was going to do a complete reinstall but I'll try this first.  Thanks.

---

### Post by djen9999 on 2007-04-19
Nope.  Same problem. Re-install from the beginning now unless someone else has an idea.

---

