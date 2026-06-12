---
title: "Ubuntu 9.10 on PowerBook G4 - power management not detecting battery"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by kingharvest on 2010-01-08
Hi --

I've just installed Ubuntu 9.10 on an old PowerBook G4 I have, and when I go to Power Management, it doesn't provide the tab for battery-related settings (nor do I get the little battery/charge icon in the upper-right panel).

I'm comparing this to the version of Ubuntu 9.10 I installed on my EeePC netbook, where those things are present.

Is there anything I can do to get the Power Management preferences to recognize that the machine has a battery?

If it helps: the PowerBook had Ubuntu installed on it using the 9.10 "alternate" .iso, as I was having trouble burning the "desktop" .iso to a CD.

Thanks for any advice!

Best,

--Carl.

---

### Post by linuxopjemac on 2010-01-08
Do you have pmu_battery loaded?

```
sudo modprobe pmu_battery
```

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/458004](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/458004)

to have it working at every boot:
add pmu-battery to the etc/modules

---

### Post by kingharvest on 2010-01-08
Thanks! That worked like a charm.

Another question, which I doubt is related, but it just happened: The little black notification windows that come up (for things like info about the wireless connection or when I use fn+f2 to up the screen brightness) are now filled with nothing but dots and lines, no readable text. After the initial install they were displaying just fine. I've tried restarting, but the problem remains.

Thanks again,

--Carl.

---

