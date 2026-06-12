---
title: "Battery wont charge, Macbook 2010"
date: 2016-02-01
forum: Apple Hardware Users
---

### Post by Red_Dark on 2016-02-01
I recently installed Elementary OS, Linux Mint, and Ubuntu Gnome onto my old 2010 Macbook. Everything was working fine until my friend dropped it. Now the battery is stuck at 34% on the indicator. This was not a problem before the laptop was dropped. And the drop was from about 3 feet in the air. The laptop was in my backpack as well. The power adapter does not light up orange/green when connected anymore, and running ```
acpi
``` outputs:
 ```
Battery 0: Full, 41%
``` I have restarted my laptop several times, and no change. The output of ```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```
is
```
 native-path:          BAT0  vendor:               SMP
  model:                bq20z451
  power supply:         yes
  updated:              Mon 01 Feb 2016 09:31:22 PM MST (275 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              21.3744 Wh
    energy-empty:        0 Wh
    energy-full:         52.122 Wh
    energy-full-design:  63.1815 Wh
    energy-rate:         16.0746 W
    voltage:             11.364 V
    percentage:          34%
    temperature:         32.3 degrees C
    capacity:            82.4957%
    technology:          lithium-ion



```

If someone could help me figure out how to fix this, that'd be great

---

### Post by Bucky Ball on 2016-02-02
*Thread moved to **Apple Hardware Users**.*

Please post here for Mac hardware. You had your first post moved here also.

Of the three distros you've mentioned we only support UbuntuGnome. Linux Mint has a vibrant, active community of its own and I know Elementary has a forum, but not sure how active that is. What are you using now? 

Anyhow, not sure if moving here will make much difference. Sounds like your battery was damaged somehow or, worse, the connectors for the battery on the computer itself.

I'd suggest switching off, taking the battery out, unplug the machine from the wall if it is plugged in, hold the power button down for about thirty seconds, put the battery back in and boot up. 

Keep this in mind, though: dropping a machine is not going to jumble up the code on the hard drive. There is no way it can damage software, only the hardware it resides on and/or controls. Therefore, if whatever distro you're using is showing 41% where it was showing 100% before, 41% it probably is and I'd say it's the battery, not the software. It's not a box of dice in there that's going to be jumbled up by a heavy knock to the head. :D

---

