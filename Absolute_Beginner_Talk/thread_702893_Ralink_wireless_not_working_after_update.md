---
title: "Ralink wireless not working after update"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2008-02-20
I've got a problem I've been trying to solve myself, but no luck so far, so I'll ask here.

In the past few days, I've not been able to get my Ralink wireless card working.  It has a RT61/RT2500 chipset, whatever that means.  I've tried to follow various tutorials and even some threads here (so long as they didn't involve apt-get, since I have no Internet), but to no avail.

When I run "iwconfig", it finally shows my essid, but now no longer shows my key (previously, it was reversed).  I'm not really sure where to go from here.

If you need me to post additional info, just ask.

---

### Post by tyggna1 on 2008-02-20
```
iwlist <interface name> scanning
```

would be helpful.

---

### Post by tyggna1 on 2008-02-20
having dealt with ra wireless cards in redhat recently--it sounds like you might just have some screwy options with the firmware.  Linux keeps the firmware binaries in a directory (I don't know where it is in Ubuntu).  If you download the latest source from the edimax website and follow the instructions in the README, then you might have better luck.

---

