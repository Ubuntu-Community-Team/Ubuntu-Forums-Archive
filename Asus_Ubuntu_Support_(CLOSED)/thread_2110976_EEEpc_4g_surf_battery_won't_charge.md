---
title: "EEEpc 4g surf battery won't charge"
date: 2013-01-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by superchar42 on 2013-01-31
I just got this old 4g surf from a friend. It wouldn't start, so I left it on the charger for a while and finally I could boot up. No battery to speak of but it ran while plugged in.
Then it stopped turning on altogether.

So I thought a new battery would do. Bought a new battery, that's drained, and now the box won't run without being plugged in, and also won't charge. 

The ac adapter is shown as being plugged in. It blinks dark and light in the applet panel (switching between charging and fully charged) and the orange light to show charging is sometimes on and sometimes off whether the computer is running or not.

Clicking on the applet, it shows "Laptop battery is charged" sometimes adding 100% to that
```

charlie@dinner:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0A:00/power_supply/BAT0
  vendor:               ASUS
  model:                701
  power supply:         yes
  updated:              Thu Jan 31 14:55:18 2013 (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              0.84 Wh
    energy-empty:        0 Wh
    energy-full:         0.84 Wh
    energy-full-design:  43.68 Wh
    energy-rate:         0.0084 W
    voltage:             8.408 V
    percentage:          100%
    capacity:            1.92308%
    technology:          lithium-ion
```


This is a brand new battery!!! I'm still in the scope of being able to return it. It worked fine out of the box, though.

Any ideas? I looked through some other asus battery threads and there wasn't much hope...

---

### Post by tgalati4 on 2013-01-31
It's possible that the charging circuitry on the motherboard is damaged.  An old battery will draw a lot of current, similar to a short.  This is why your machine wouldn't boot with the old battery in place.  The new battery had some charge, enough to boot, but if the charging circuit is blown, it won't charge the new battery, even though it looks like it is charging.

I would pull the machine apart and examine the motherboard near the charging jack and examine all components from there to the internal battery tabs.  There might be a fuse that is blown that could be replaced (with some delicate soldering).

Good luck.

---

### Post by superchar42 on 2013-02-01
What would I see regarding the internal circutry that would indicate "yes this is bad"?

also, looking at the battery power statistics, I'm watching the voltage jump between 3.2, 6.8, 8.4, 6.7, 2.5, and so on, seemingly random, but I didn't watch long enough to see if there's a pattern. 

Is it possible it's an issue with the charger?

---

### Post by superchar42 on 2013-02-02
okay, it's been apart and is back together now. 

I saw nothing suspect regarding the motherboard. 

Is there anything else to check?

---

