---
title: "No Backlight Support for iMac 10,1 with ATI Radeon HD 4670 on 2.6.38"
date: 2011-05-11
forum: Apple Hardware Users
---

### Post by bloby on 2011-05-11
Hi,

My */sys/class/backlight* directory is empty.
The *backlight.c* hack compiles and runs but has no effect.
I tried to add *acpi_osi=Linux acpi_backlight=vendor* to my kernel line.
I'm using the *radeon* driver.

Help !

---

