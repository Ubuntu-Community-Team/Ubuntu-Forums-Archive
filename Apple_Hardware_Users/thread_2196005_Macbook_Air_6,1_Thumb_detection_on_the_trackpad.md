---
title: "Macbook Air 6,1 Thumb detection on the trackpad"
date: 2013-12-27
forum: Apple Hardware Users
---

### Post by Darrena on 2013-12-27
Right now the trackpad is very hard to use and I believe the issue is thumb detection.  I saw some solutions for older releases of Ubuntu that use the mtrack input driver and disable detection on the bottom 30% of the trackpad.  This looks like the solution I want but even installing this driver doesn't seem to change the behavior at all on 13.10.  Is there a different solution or some additional configuration changes I need to make with 13.10?

---

### Post by Darrena on 2013-12-27
I finally figured it out, using synclient I figured out what tweaks I needed to make and then added them to 50-synaptics.conf

The only issue I have now is selecting text doesn't work with the bottom part of the touchpad set only for clicking.  I will do more research but if anyone has figured this out and can drop a note it would be greatly appreciated.

---

