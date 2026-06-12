---
title: "ACPI Overheating...causing beeping!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Greyhoundthethird on 2007-06-20
I have an ABIT IC7-MAX3 motherboard and it has started to beep because it has overheated. I've been working at it for ages and have found out it is because the ACPI (Advanced Configuration and Power Interface) is overheating. How can i cool this down? what is going on!?

---

### Post by ukripper on 2007-06-20
can you post output of:

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by Greyhoundthethird on 2007-06-20
I've given up, i've just disabled the beep! All my other components are running at a good temp! Thanks for your help and time though. Much appreciated.

---

