---
title: "[SOLVED] video issue"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-03
I have the ati drivers installed, used envy for my integrated x1300, games such as boson, chromuim and others blink as in the screen repetitively turns on and off.  It's driving me bonkers.

Tips\help

---

### Post by spiderbatdad on 2008-02-04
are you running compiz at the same time as playing games? If so, that is the problem, most likely.

---

### Post by TechDragon on 2008-02-04
okay how do you temporarily disable compiz then?

Thanks

---

### Post by spiderbatdad on 2008-02-04
not easily, as far as I know. Gnome-compiz-manager may work for you...otherwise I think you would have to reconfigure xserver every time to truly disable it.  Maybe just "killall ccsm."  Then "ccsm --replace" to restart.

---

### Post by TechDragon on 2008-02-05
found an easier way.  

System->appearance->visual effects->none

Apply.

This resolved the issue.

---

