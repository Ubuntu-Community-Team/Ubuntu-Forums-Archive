---
title: "Slow Bootsplash Screen"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by slickidiotfan on 2007-04-21
The bootsplash (is this what it is?) moves up about half way and hangs for about 2-3 minutes on startup. Is this common or do I need to do something about it?

---

### Post by Crosbie on 2007-04-22
Type ```
dmesg
``` in a terminal.  That'll give you a list of boot events and timings, as a place to start diagnosing any problem.

I've had slowdowns before, with the boot process doing tedious unwanted thing like attempting to initialise bits of internal hardware I didn't want to use.

---

### Post by slickidiotfan on 2007-04-22
There is a lot in that. Should I post it all?

---

