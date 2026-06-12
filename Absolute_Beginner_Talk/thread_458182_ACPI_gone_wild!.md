---
title: "ACPI gone wild!"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-29
Hi,

recently I noticed that the battery icon of Gnome Power Manager in the taskbar was displaying weird information (like displaying an empty battery icon while the AC was connected or displaying a full charge capacity about 2 times higher than the designed capacity of the battery. Then I checked with the following command:

acpi -t

This normally gives information about battery charge as well as the CPU temp. Sometime the battery charge was displayed (also wrong) but most important: the CPU temp was 208.0 degrees C :shock: Well I know this is not possible and this was not the correct temp (the fan was not blowing and gnome sensor applet displayed a CPU temp of 46 degrees C...). The power management also doesn't seem to recognize when I switch on/off AC while this was working previously. I didn't performed the kernel update so this is unrelated.

I don't know what can cause the problem. Any idea? I tried to reinstall packages related to acpi but this didn't solve the issue...

Thanks

---

### Post by init1 on 2007-05-29
Try using apm. Ubuntu may not have it, so you may need to install it.

---

### Post by kilou on 2007-05-29
Apm is already installed as well. I think this one works because I can get correct CPU temp from the Gnome sensor applet. However the acpi problem causes troubles with Gnome power manager. Previously everything was working fine....

This is really weird, both lines concern acpi but only one way works:

kilou@kilou-laptop:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             37 C

kilou@kilou-laptop:~$ acpi -t
     Battery 1: discharging, 0%
     Thermal 1: ok, 208.0 degrees C

---

