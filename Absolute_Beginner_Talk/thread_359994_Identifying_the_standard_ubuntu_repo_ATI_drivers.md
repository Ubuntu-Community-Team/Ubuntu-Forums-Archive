---
title: "Identifying the standard ubuntu repo ATI drivers?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-12
Some time ago I installed Ubuntu dapper on a friends Acer laptop, they have an ATI graphics card, I cannot remember whether I used the standard drivers from the ubuntu repository or whether I installed 3rd party drivers (from example from ATI site).

How do I identify the ati drivers from the ubuntu repo? (I want to carry out the kernel update without going through the mess of having to reinstall drivers).

Thank you.

---

### Post by crispy_420 on 2007-02-12
The "free" drivers will be listed as radeon. ATI (3rd party) will be listed as fglrx. Check your xorg.conf. Usually a default install will go radeon and not fglrx.

Check /etc/X11/xorg.conf:

> gedit /etc/X11/xorg.conf

Is that what you are talking about?

---

### Post by igknighted on 2007-02-12
try 'fglrxinfo', it will tell you if the fglrx drivers are in use.  If the command fails the fglrx drivers are not installed.  If the command reports "mesa" then they are installed but not working properly.  If you get something about your ATI card and ATI technologies (blah blah blah) then fglrx is installed and working properly.

---

### Post by PartisanEntity on 2007-02-13
Thanks to the both of you, I will check their laptop soon.

---

