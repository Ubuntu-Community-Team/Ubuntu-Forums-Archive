---
title: "graphical issues"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by zeroti on 2011-05-15
Hi everyone, I've installed 11.04 on my Powerbook G4, and so far I like it. :)

However, I'm unable to get hardware acceleration to work at this point.

Also, I see graphics distortion in certain windows from time to time until that window is updated by scrolling or some other change. I've attached a screenshot of a distorted window.

Here is some trimmed output of the Xorg.0.log:
```

$ cat /var/log/Xorg.0.log | grep -B 10 -E 'EE|AIGLX'
...
[    19.985] (II) Initializing built-in extension XKEYBOARD
[    19.985] (II) Initializing built-in extension XC-MISC
[    19.985] (II) Initializing built-in extension SECURITY
[    19.985] (II) Initializing built-in extension XINERAMA
[    19.985] (II) Initializing built-in extension XFIXES
[    19.985] (II) Initializing built-in extension RENDER
[    19.985] (II) Initializing built-in extension RANDR
[    19.985] (II) Initializing built-in extension COMPOSITE
[    19.985] (II) Initializing built-in extension DAMAGE
[    19.985] (II) Initializing built-in extension GESTURE
[    20.013] (II) AIGLX: Screen 0 is not DRI2 capable
[    20.013] drmOpenDevice: node name is /dev/dri/card0
[    20.014] drmOpenDevice: open result is 9, (OK)
[    20.014] drmOpenByBusid: Searching for BusID pci:0000:00:10.0
[    20.014] drmOpenDevice: node name is /dev/dri/card0
[    20.014] drmOpenDevice: open result is 9, (OK)
[    20.014] drmOpenByBusid: drmOpenMinor returns 9
[    20.014] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    20.014] drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
[    20.014] (II) AIGLX: Trying DRI driver /usr/lib/dri/r300_dri.so
[    20.261] (EE) AIGLX error: Calling driver entry point failed
[    20.262] (EE) AIGLX: reverting to software rendering
[    20.262] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    20.281] (II) AIGLX: Loaded and initialized swrast

```For comparison, here is some output from my Debian Squeeze installation:
```

$ cat /mnt/var/log/Xorg.0.log | grep -B 10 -E 'EE|AIGLX'
...
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
SELinux: Disabled on system, not enabling in X server
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so

```Any clues?

Thanks!

---

