---
title: "Powerbook brightness adjustment problems"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by mwoenker on 2008-04-25
I just installed Hardy on my 1.5 Ghz powerbook, and it seems to work pretty well, with a few issues.  The main problem is the brightness adjustment keys - when I press F1/F2, the brightness indicator pops up, but it always displays zero brightness, and the screen stays at full brightness.

I also have a somewhat similar issue with the volume keys, but it's just cosmetic - the volume changes, but the volume level displayed onscreen is sometimes the actual volume, and sometimes zero.

The backlit keyboard doesn't work either, but I don't particularly care about that.

---

### Post by russo.mic on 2008-04-26
Do you have the package pommed installed?

---

### Post by mwoenker on 2008-05-02
Sorry it's taken me so long to respond to this... I've installed pommed, but it doesn't appear to be starting.  If I run "sudo pommed -d", I get:

```
mwoenker@mwoenker-laptop:~$ sudo pommed -d
I: pommed v1.15 ($Rev: 434 $) Apple laptops hotkeys handler
I: Copyright (C) 2006-2008 Julien BLACHE <jb@jblache.org>
pommed configuration:
 + General settings:
    fnmode: 1
 + sysfs backlight control:
    initial level: -1
    step: 8
    on_batt: 40
 + Audio volume control:
    card: default
    initial volume: -1
    step: 10%
    beep: yes
    volume element: Master
    speaker element: Master
    headphones element: Headphone
 + Keyboard backlight control:
    default level: 100
    step: 16
    auto on threshold: 20
    auto off threshold: 40
    auto enable: yes
    idle timer: 60s
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Beep:
    enabled: no
    beepfile: /usr/share/pommed/goutte.wav
device-tree copyright node: [Copyright 1983-2004 Apple Computer, Inc. All Rights Reserved]
device-tree model node: [PowerBook5,4]
I: PMU machine check: running on a PowerBook5,4
Failed to access brightness node: No such file or directory
E: LCD backlight probe failed, check debug output

```

---

### Post by clakes on 2008-05-07
Same problem here on my PB G4... =(

---

### Post by revcompgeek on 2008-12-24
Has there been any fixes for this yet? I am having the same problem and would like to see it fixed.

---

### Post by stream303 on 2008-12-24
How about pbuttonsd?

There is a quick fix in the wiki about half way through:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Although this has been a sticky problem for ages - the guys in cupertino just won't let go of the hardware specs for the Linux devs to work on.

You can mitigate it somewhat by messing around with gamma, or using a dark theme, although the background in firefox is always white-hot.

```
xgamma -gamma 0.5
```

The usable range is from about 0.5 to 1.5, with 1 being the default.  Of course this changes your gamma, so I wouldn't go editing critical photos with this kind of change.  When you find a setting you like, you can make it permanent in your xorg.conf file.

Xubuntu (and XFCE in other distros) has two great gamma controls.  One will adjust the red, blue, and green gamma separately, while there is also an overall brightness adjustment which may help.

These aren't as good as a dedicated hardware brightness controls, but may serve to make the system usable.  Although using xgamma techniques might not save you much battery power.

You can also try using a very dark them, such as "darkroom", which I've seen in Intrepid and make other tweaks to darken everything.

This might enable you to at least live with the system until a hardware fix is applied or found.

---

### Post by moviemaniac on 2009-05-21
I know this thread is quite old, but this might be of help to some:

I've had the same problem on my brothers PowerBook G4 (Geforce 4 Go 440) and Ubuntu Jaunty. My "fix" was to ditch the included kernel and compile a custom 2.6.29.4 kernel specifically designed to work with just that machine (and leaving out all the junk it doesn't make sense using - like DVB cards). Now I can control the brightness with the F1/F2-keys, the bootsplash shows the real colours now and a few minor things are also fixed. If anyones interested, I can supply you with the corresponding config-file for the 2.6.29-series.

---

### Post by bigpenguin on 2011-05-26
I have an old PowerBook G4 that I wanted to bring back to lfie.  I've installed 10.10 without any problems, but the first bug I found was the brightness hotkeys not working.  I've installed both pommed and pbbuttonsd and still nothing.  The volume keys work fine, it's just the brightness keys.  Anyone know of any simple fixes?  Thanks.

---

