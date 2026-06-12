---
title: "MBP Keyboard light doesn't work"
date: 2012-09-07
forum: Apple Hardware Users
---

### Post by vdrummer on 2012-09-07
Hey everyone,

I installed Ubuntu 12.04 on my MBP 9,2 yesterday.
However, the keyboard light does not work. When using the function keys (F5 and F6), there's a pop-up in the upper right corner indicating maximum brightness, but the keyboard light is still off.

Writing a value (such as 255) into
```
/sys/class/leds/mmc0\:\:/brightness
```doesn't help either.

Any suggestions on how to activate the light would be highly appreciated.

-vdrummer

---

### Post by Bachstelze on 2012-09-07
Have you installed pommed?

---

### Post by vdrummer on 2012-09-08
No, I didn't install pommed.
I downloaded and installed it some minutes ago but the keyboard light is still not working.

"pommed -f" gives me
```
+ Keyboard backlight control:
    default level: 100
    step: 10
    auto on threshold: 20
    auto off threshold: 40
    auto enable: yes
    idle timer: 60
    idle level: 0
```which should set it to 100 (out of 255 I think).

But I also get the following errors:
```
E: Unknown Apple machine: MacBookPro9,2
E: Unknown Apple machine
```Apparently, there's no pommed for the MBP 9,2 out yet.

---

### Post by Bachstelze on 2012-09-08
Could you post the entire output?

---

### Post by vdrummer on 2012-09-08
> **Bachstelze said:**
> Could you post the entire output?
Sure!

```
I: pommed v1.39 Apple laptops hotkeys handler
I: Copyright (C) 2006-2011 Julien BLACHE <jb@jblache.org>
pommed configuration:
 + General settings:
    fnmode: 1
 + sysfs backlight control:
    initial level: -1
    step: 1
    on_batt: 6
 + ATI X1600 backlight control:
    initial level: -1
    step: 10
    on_batt: 80
 + Intel GMA950 backlight control:
    initial level: 0xffffffff
    step: 0xf
    on_batt: 0x40
 + nVidia GeForce 8600M GT backlight control:
    initial level: -1
    step: 1
    on_batt: 6
 + Audio volume control:
    card: default
    initial volume: -1
    step: 10%
    beep: yes
    volume element: PCM
    speaker element: Front
    headphones element: Headphone
 + Keyboard backlight control:
    default level: 100
    step: 10
    auto on threshold: 20
    auto off threshold: 40
    auto enable: yes
    idle timer: 60s
    idle level: 0
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Beep:
    enabled: no
    beepfile: /usr/share/pommed/goutte.wav
 + Apple Remote IR Receiver:
    enabled: no
E: Unknown Apple machine: MacBookPro9,2
E: Unknown Apple machine
```

---

### Post by Bachstelze on 2012-09-08
You can try to install the applesmc kernel module (package applesmc-dkms) from the mactel PPA [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa) and reboot.

If it still doesn't work, I guess there's not much you can do but wait for MBP 9 support to be added in pommed...

---

### Post by vdrummer on 2012-09-08
Installing "applesmc-dkms" worked! Keyboard light is now on.

&#25163;&#20253;&#12387;&#12390;&#12367;&#12428;&#12390;&#26412;&#24403;&#12395;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#65281;

---

