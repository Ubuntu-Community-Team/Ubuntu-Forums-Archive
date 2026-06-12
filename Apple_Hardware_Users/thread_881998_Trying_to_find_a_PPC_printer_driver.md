---
title: "Trying to find a PPC printer driver"
date: 2008-08-06
forum: Apple Hardware Users
---

### Post by spookthehamster on 2008-08-06
I've installed Xubuntu Feisty on an old G4 Powermac to try to get away from the slowness of OS X on the machine. Everything is going swimmingly but there's one dealbreaker; right now my printer doesn't work.

It's a Canon iP1800. I've found some drivers for it but they're i386. Does anyone know if I can get any PPC ones?

I'm new to Linux so I don't know where to look for this sort of help. I hope I didn't put this in the wrong place.

---

### Post by pxwpxw on 2008-08-07
Is cups (Common UNIX Printing System) working?
Drivers should be there, but you may have done all that.

[http://localhost:631/](http://localhost:631/)

---

### Post by stream303 on 2008-08-07
According to the openprinting.org site, it list the Pixma ip1800 as working perfectly, although you'll need to load the IJ printer driver.  This report comes from users, and the driver doesn't appear to be in the official foomatic release yet.

Perhaps it will make it into Ubuntu Intrepid, or you may have to add it manually.

In any case, pxwpxw was spot on about keeping an eye on cups.  Check out openprinting.org for further info.

I'm not big on solving printer issues, so perhaps someone can help if you need to go further..

---

### Post by spookthehamster on 2008-08-07
CUPS has no entry for the iP1800, and the driver available from the Canon website is i386 only.

---

### Post by cyberdork33 on 2008-08-07
> **spookthehamster said:**
> CUPS has no entry for the iP1800, and the driver available from the Canon website is i386 only.
I think they are trying to say that the driver on the Cannon website is not the one to use... search on openprinting.org.

---

### Post by spookthehamster on 2008-08-07
The Canon driver is the only driver on the Openprinting website, there's nothing about PPC there

---

### Post by stream303 on 2008-08-09
That printer model may be so new that the driver, especially for ppc, hasn't been included / compiled into any releases yet.  You may just need to hang tight for awhile, or find another printer temporarily.

---

