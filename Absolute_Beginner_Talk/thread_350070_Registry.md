---
title: "Registry"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-01-31
I recently installed wine, how can I clear the registry if any??
Thanks:D

---

### Post by PointSource on 2007-01-31
the *.reg file are in /home/{INSERT USER HERE}/.wine/

Probably ones called user.reg, system.reg and userdef.reg.

---

### Post by ayed on 2007-01-31
So if I delete them what happens??
THanks

---

### Post by PointSource on 2007-01-31
I suppose wine will regenerate them. Maybe just rename them so you have a backup if something fails.

---

### Post by ayed on 2007-01-31
So say I download a trial version of Ulead software and last for 15 days, after the 15 days if I delet the registry will it result in another 15 day extension and so on in the wine folder??:o

---

### Post by anaconda on 2007-01-31
it depends in how/where the program stores the 15 day info. if it is stored in the registry, then yes.

---

### Post by ayed on 2007-01-31
Hmmmm, interesting, so how can I check? I mean don't they usually store it in the registry?

---

### Post by ayed on 2007-01-31
no one answered

---

### Post by NESFreak on 2007-01-31
install some time trial. start it up and look for the X days left message. Wait one day and check for the X days - 1 message. Back up your register. Kill wine (close the wine server process). Remove the register. Start wine (and your program) again and look if your X days - 1 day left message. If it's back to X days instead of X-1 then you have succeeded.

NESFreak

---

