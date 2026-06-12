---
title: "macbook backlight &amp; exterrnal monitor"
date: 2007-06-13
forum: Apple Intel Users
---

### Post by pveith on 2007-06-13
Hi,

i use a brand new macbook 2,16 GHz.

1. i can't get my grips on backlight. I am on feisty and i do have backlight under lsmod (associated with asus_acpi). 
2. i can't get my mini-DVI conector to work. And for some reason the xorg,conf given in the howtos don't work for me.

Else erverything seems fine now. Additionall the wireless driver seems to suck 2 Watt, even if it is not in use (unload of driver seems help here).I will probably check the iSigh(t)-Cam, too. I depend on battery-live-time, so ~10% less power-consumption is really good news. Will post a script as soon as i got it working.

I hope someone can shed some light on this...

---

### Post by pveith on 2007-06-13
Anyone with working backlight under feisty? If yes, please do check out if you have a backlight device in "/sys/devices/platform/applesmc/" and reply to this thread.

(If someone is more knolageable about this, i would really appreciate any help.)

---

### Post by pveith on 2007-06-14
ad 2. Installing the intel-driver from backports did fix the the external Monitor problem.

---

### Post by kzm. on 2007-06-14
can you more explicit describe what you did to fix?
i have troubels with my backlights as well.. and how does your xorg.conf look like? do you got tv working?

i posted this some time ago, i cross reference this for people looking for backlight issues, it discribes a fix (i couldnt get working yet.. but my keyboard is all ****** right now):
[http://ubuntuforums.org/showthread.php?t=467001](http://ubuntuforums.org/showthread.php?t=467001)

---

### Post by pveith on 2007-06-14
@kzm: i just installed the package "xserver-xorg-video-intel" from feisty-backports and used my old xorg.conf (i used with the xserver-xorg-video-i810 package). And voila i had the external monitor up and runing perfectly. i could post my xorg.conf, but it uses a german keyboard.

ad 2: Heureka i got backlight running with my macbook.
And now stay tuned for some really wierd stuff: Apple change its biosdata from "Apple Conputers, Inc." to "Apple Inc.". This makes the feisty fdi found under "/usr/sahre/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi" incompatible with newer macbooks. I changed the fdi file corespondingly and now i got it up and running smoothly.

All in all i solved my own puzzle, very satisfying.

---

