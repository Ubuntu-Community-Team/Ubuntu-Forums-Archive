---
title: "Hardy Heron and Tibook G$"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by ag0g0girl on 2008-05-06
I got a message in the Software Update manager that Hardy was ready, so I clicked the button for the install.

I had been stuck at busybox with Gusty, and have had to boot with modprobe ide-core.

I now get a boot screen, with the loader stripe moving left to right, then black screen, a message that says boot scripts loading.

After a while I get 

*starting anac(h)ronistic cron anacron
*starting deferred execurion scheduler atd
*starting periodic command scheduler crond
*Running local boot scripts (/etc/rc.local)

This comes on screen and the boot stops.

This isn't busybox, so I can't just type the same thing to get in.  Is there anything I can do before clean install?

---

### Post by cyberdork33 on 2008-05-06
> **ag0g0girl said:**
> I got a message in the Software Update manager that Hardy was ready, so I clicked the button for the install.

I had been stuck at busybox with Gusty, and have had to boot with modprobe ide-core.

I now get a boot screen, with the loader stripe moving left to right, then black screen, a message that says boot scripts loading.

After a while I get 

*starting anac(h)ronistic cron anacron
*starting deferred execurion scheduler atd
*starting periodic command scheduler crond
*Running local boot scripts (/etc/rc.local)

This comes on screen and the boot stops.

This isn't busybox, so I can't just type the same thing to get in.  Is there anything I can do before clean install?
Try hitting enter there. sometimes that will cause it to continue, but IDK how to permanently fix it. just boot from the live cd, backup files , and reinstall. Upgrades tend to go poorly anyway.

---

### Post by driven1 on 2008-05-06
I had to do a fresh install from the alt install iso, twice actually, befoer it all worked nicely.

---

