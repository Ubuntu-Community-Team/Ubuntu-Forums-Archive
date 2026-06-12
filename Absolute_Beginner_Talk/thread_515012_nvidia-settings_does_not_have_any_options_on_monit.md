---
title: "nvidia-settings does not have any options on monitor"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-08-01
I am using an nvidia dual head card, one of the monitors shows all possible resolutions and even the name of the monitor,but the second monitor shows nothing and is defaulted to 800x600.  Am i SOL with this monitor or is there a way to enter the horizontal and vertical syncs manually to get the second monitor working?

---

### Post by Wim Sturkenboom on 2007-08-01
You can add something like *HorizSync 27.0 - 96.0* and *VertRefresh 50.0 - 160.0* to the relevant *monitor* section in /etc/X11/xorg.conf. Please note that the numbers apply to my Iiyama Vision Master 403 and will more than likely be different for yours.

---

