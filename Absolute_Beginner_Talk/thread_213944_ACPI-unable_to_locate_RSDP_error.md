---
title: "ACPI-unable to locate RSDP error"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Podman on 2006-07-12
I have a Digital 200 mmx Pentium computer I was going to try
Ubuntu on.  The cd starts loading the system but the first error msg is:  ACPI unable to locate RSDP then it seems to go ok until it gets to the x-window system then hangs and msg comes on screen which says: infomation-out of scan range.
Then nothing.  Tried safe mode and ends up at command prompt.
Tried boot= no acpi but still didn't work.   Knoppix works fine on machine.  Any ideas how to get Ubuntu to run?

---

### Post by MonkeyNet on 2006-07-12
> **Podman said:**
> The cd starts loading the system but the first error msg is:  ACPI unable to locate RSDP then it seems to go ok until it gets to the x-window system then hangs and msg comes on screen which says: infomation-out of scan range.
Then nothing.

The problem of X-Windows hanging could be more to do with the resolution of the xorg configuration. I have an older machine which is a PIII 700 and have the same issue of the RSDP. The ACPI is basically the interface between the motherboard and your software for shutdown procedures. I had Windows 2000 installed on the machine and instead of turning off, it would just got to a now safe to off your computer. The only way I was able to fix this was with the proper drivers for my motherboard. I am setting up this machine again over the next couple of days with Ubuntu so am going to see if I can resolve this issue. Will let you know if I have any luck

> **Podman said:**
>  Tried safe mode and ends up at command prompt.

This is normal for the safe mode

Cheers,

Andrew

---

### Post by Podman on 2006-07-12
OK, thanks for the info. I tried to boot with noacpi but it still didn't work.  I would like to try and boot in safe mode without acpi but couldn't figure a way to do it yet. I will keep playing with it for awhile and see what I can come up with.

John

---

