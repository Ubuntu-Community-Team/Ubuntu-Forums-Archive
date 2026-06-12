---
title: "checking fan speed"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-04-04
is there a way of checking the cpu fan speed in gutsy?

---

### Post by joshrobinson on 2008-04-04
try this

```
sudo aptitude install sensors-applet lm-sensors
```
then right click your gnome panel and add the hardware sensor monitor
then when its on the panel right click it and go to preferences
then click sensors and see if you have a fan speed sensor in there

my laptop has no sensor for the fanspeed so i cant test it

---

### Post by .nedberg on 2008-04-04
You need to run ```
sudo sensors-detect
``` first. Just answer YES to everything.

---

### Post by Mick8882003 on 2008-04-04
no sensor, damn
funny though, has one in bios

---

