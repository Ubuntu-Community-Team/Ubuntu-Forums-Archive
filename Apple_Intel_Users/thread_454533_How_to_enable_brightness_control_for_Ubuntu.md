---
title: "How to enable brightness control for Ubuntu?"
date: 2007-05-25
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-05-25
Hi All!

Today I have installed Ubuntu for the first time for my Intel Mac.
How to make brightness control buttons work? Sound control buttons work pretty fine.

---

### Post by Gen2ly on 2007-05-25
I believe pommed is what is used for keys to do function control.  Maybe reinstall it?

---

### Post by Ubivetz on 2007-05-29
I have installed pommed. But it fails to run:
```

root@Mac:~# pommed -f
I: pommed v1.2 ($Rev: 290 $) Apple laptops hotkeys handler
I: Copyright (C) 2006-2007 Julien BLACHE <jb@jblache.org>
pommed configuration:
 + General settings:
    fnmode: 1
 + ATI X1600 backlight control:
    initial level: 100
    step: 10
 + Intel GMA950 backlight control:
    initial level: 0xffffffff
    step: 0xf
 + Audio volume control:
    card: default
    initial volume: -1
    step: 10%
    volume element: PCM
    speaker element: Front
    headphones element: Headphone
 + Keyboard backlight control:
    default level: 100
    step: 10
    auto on threshold: 20
    auto off threshold: 40
    auto enable: yes
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Apple Remote IR Receiver:
    enabled: no
E: Unknown Apple machine: iMac5,1
E: Unknown Apple machine

```

---

### Post by Gen2ly on 2007-05-29
Curious.  I saw this item listed on another forum as well.  I think features being built into the kernel now is conflicting with pommed.  Also it could possibly be a conflict with gnome-power-manager as it too controls brightness, but likely the former.  I don't use pommed, maybe talk to the author?

---

### Post by Ubivetz on 2007-05-29
> **Dirk.R.Gently said:**
> Curious.  I saw this item listed on another forum as well.  I think features being built into the kernel now is conflicting with pommed.  Also it could possibly be a conflict with gnome-power-manager as it too controls brightness, but likely the former.  I don't use pommed, maybe talk to the author?
It does not work with KDE too.

---

### Post by Ubivetz on 2007-05-29
I have found solution from here [http://ubuntuforums.org/showthread.php?t=434528](http://ubuntuforums.org/showthread.php?t=434528)

P.S. On my system (Feisty AMD64) it's not required to install so many packages manually.
You just need to install type 

```
sudo aptitude install pciutils-dev
```

---

### Post by Ubivetz on 2007-05-29
Then I have written two scripts

```

[root@slavik:backlight] cat dec_brightness
#!/bin/bash
Current=$(backlight)
if [ $Current -lt 50 ]; then
    exit
else
    backlight -10

```

```

[root@slavik:backlight] cat inc_brightness
#!/bin/bash
Current=$(backlight)
if [ $Current -gt 240 ]; then
    exit
else
    backlight +10

```

And then called xbindkeys-config  to bind these scripts to keys 183 (F14) and 184(F15).

---

