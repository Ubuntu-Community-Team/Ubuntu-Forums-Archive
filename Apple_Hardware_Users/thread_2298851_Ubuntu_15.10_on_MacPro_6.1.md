---
title: "Ubuntu 15.10 on MacPro 6.1"
date: 2015-10-14
forum: Apple Hardware Users
---

### Post by denics on 2015-10-14
Hi, I have installed Ubuntu 15.10 on a MacPro 6.1 and almost everything works out of the box.
The only exceptions are the two integrated ATI R9 270X that works ONLY with VESA drivers! I have tried all the possible combinations:

- fglrx with radeon.modeset=0 : dark screen with a pointer X shaped (like the long time ago pointer when no window manager was loaded), I can boot at runlevel 3 to resume my system;
- fglrx with radeon.modeset=1 : everything freeze;
- fglrx-update: same as above;
- radeon with radeon.modeset=1 : everything freeze;
- fglrx manually installed from catalyst installer 15.9: same as above;
- radeon with radeon.modeset=0 : I can enter X but using the VESA drivers. 

In the last case, when I do ```
dmesg | egrep 'drm|radeon'
``` I get:
```

[drm] Initialized drm 1.1.0 20060810
[drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!

```
That I understand is logical because of the nomodeset.

Did anyone successfully run X with radeon or fglrx?

---

