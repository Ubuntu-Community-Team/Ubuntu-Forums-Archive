---
title: "ACPI problems"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by rhart211 on 2008-03-11
I am having an issue with ACPI. I can install Ubuntu 7.10 from the Live CD, but I am presented with the following error when ubuntu boots up:
```
ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
```
I have added acpi=force to the /boot/grub/menu.lst, however, I am still presented with this error. I have updated my bios, whose age is 2002. I have also selected ACPI in the Bios Power Management.  Is there a way I can get this error to stop showing during boot?
Thanks

---

### Post by plucky on 2008-03-11
rhart211,

Try ```
acpi=off apm=on
``` instead of **acpi=force** as older systems use **apm** for power management.

Good luck

---

