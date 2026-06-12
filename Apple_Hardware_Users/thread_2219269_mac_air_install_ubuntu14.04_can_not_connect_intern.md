---
title: "mac air install ubuntu14.04 can not connect internet"
date: 2014-04-23
forum: Apple Hardware Users
---

### Post by fkysly on 2014-04-23
network controller is BCM43600 802.11ac[14e4:43a0]

---

### Post by este.el.paz on 2014-04-23
You can install the wifi driver using the "driver manager" or something like that, from within Settings Manager should be . . .

e.e.p.

---

### Post by spencer8 on 2014-04-24
Hey,

Having same issue. So, I installed refind, added partition, etc. install Ubuntu 14.04, and all drivers worked properly. 

The next day I was trying to add support for trackpad swipe (added x11 conf to /etc/x11/), and ran a command from the tutorial. Rebooting, I got some weird error and the GUI was broken. I rebooted again, logged in with my user account on safe mode (terminal), removed the X11 conf, and rebooted. GUI worked again.

However, my internet adapters (both ethernet/wireless) were not working --- spent a few hours searching about the problem. Apparently the drivers were "unclaimed". 

Tried another few tutorials/fixes but didn't work.

Reinstalled Ubuntu, and the drivers STILL don't work.

I tried enabling the broadcom adapter from the "Additional Drivers", but it said that it was not working.

Any ideas?

---

### Post by este.el.paz on 2014-04-25
> **spencer8 said:**
> Hey,

Having same issue. So, I installed refind, added partition, etc. install Ubuntu 14.04, and all drivers worked properly. 

The next day I was trying to add support for trackpad swipe (added x11 conf to /etc/x11/), and ran a command from the tutorial. Rebooting, I got some weird error and the GUI was broken. I rebooted again, logged in with my user account on safe mode (terminal), removed the X11 conf, and rebooted. GUI worked again.
Reinstalled Ubuntu, and the drivers STILL don't work.
I tried enabling the broadcom adapter from the "Additional Drivers", but it said that it was not working.

Any ideas?

@spencer8:

Short answer, no ideas . . . .  Longer answer, in theory it shouldn't make sense that if you had the system working and then let's say messed it up, got it back . . . and then did fresh re-install . . . you ***should*** be able to add the wifi device back . . . .  Further complication on the answer . . . I've found that the various 'buntu flavors and LM don't seem to handle the complexities of the apple trackpad very well . . . some people seem to be able to tweak "synaptics" to adjust for finger pressure, but that is beyond my capacity . . . .  Did you do a total nuke and re-pave, or did you do something that would leave some parts of first file system installed??

Hopefully someone else will be able to discern your issue . . . I don't have an Air, so don't know if there are some notes in the wiki about it??

e.e.p.

---

