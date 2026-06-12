---
title: "Booting"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by amphet on 2007-02-24
I'm running Ubuntu 6.10 Edgy, one of my problems is that when I start ubuntu almost every time right after the ubuntu boot up screen, kubuntu boot up screen would show up shutting down my system, this happens like 3 or 4 times before my system boots up correctly. any ideas?

Also I noticed if I press alt+f1, I see that the problem occurs when it's loading kdm, I tried to start it manually 'sudo /etc/init.d/kdm restart' but it would only shutdown my computer.

---

### Post by igknighted on 2007-02-24
Try removing KDE (and KDM) and seeing if the problem goes away.  If it does, try reinstalling KDE, but picking gdm as the display manager when it asks (or if you did that before, use kdm).

---

### Post by amphet on 2007-02-24
I have both, kdm and gdm, same thing happens

---

