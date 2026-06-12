---
title: "poor MacbookPro3,1 fan control in maverick"
date: 2010-12-04
forum: Apple Hardware Users
---

### Post by jdc on 2010-12-04
I've just upgraded from jaunty to maverick on my MacbookPro3,1.  I have applesmc loaded, and use the stock Ubuntu packages, not the mactel packages.  With jaunty, when I started cpu intensive jobs, the fans would fairly quickly start speeding up to control the temperature.  But with maverick, it takes several minutes before the fans go about 2000 rpm, and during that time I get messages like

CPU0: Core temperature above threshold, cpu clock throttled (total events = 53653)

The fans *do* eventually speed up and the throttling stops, but it's a bit worrying.  I see temperatures of around 97C for a minute or two before the fans speed up, and then lower temperatures once they are running full speed.

Fan speeds are set to 2000 minimum and 6000 max, and the manual control is set to 0.  I've used pressurized air to make sure there's no dust.

Any idea why it takes so long for the fan speeds to ramp up?

(I could try the mactel fan control package, but I try to avoid too many third party repos.  And this used to work fine.)

Thanks in advance!

---

### Post by jdc on 2010-12-08
I'm still having the problem, but I installed macfanctld from the mactel-support repository, and it ensures that the fan speed increases as soon as the temperature goes up.  Nevertheless, I still get those warnings about the CPU speed being throttled.

---

