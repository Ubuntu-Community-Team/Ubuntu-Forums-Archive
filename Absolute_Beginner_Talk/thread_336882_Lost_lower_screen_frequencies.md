---
title: "Lost lower screen frequencies"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by SweVoyager on 2007-01-12
I just installed the Nvidia drivers on my Edgy system without problems, but I seem to have lost my trusty old 60Hz screen update frequency. Only 75Hz is available, but that makes my old LCD screen become blurry (compared to 60Hz).

I've looked over my /etc/X11/xorg.conf, but I cant decide where to change what into something else. :) 

Here's my monitor:

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 52.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

```

I guess DPMS is something that could bug out the frequency, but I have no idea what to change. or add to get 60Hz back.

I admit that it was stupid of me not to backup xorg.conf before updating the graphics drivers.

---

