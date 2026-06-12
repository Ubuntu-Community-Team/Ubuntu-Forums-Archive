---
title: "No smp with generic kernel"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by SpinesN on 2006-12-12
Just did an install with edgy on my 3800+ x2 system and only one core comes up. What am I missing?

---

### Post by ElBuscador on 2006-12-13
Are you using an Nvidia graphics card and the Nvidia propriatary driver? If so, do a search on this forum for "SMP Nvidia". Basically, when you install the Nvidia driver and log back in, it switches to the 386 kernel, which does not support SMP, instead of the generic one. When you reboot into the generic kernel, X will not start. The solution that worked for me was to boot into the generic kernel and run the Envy script from the command line.

---

### Post by SpinesN on 2006-12-13
I am indeed. Many thanks :)

---

