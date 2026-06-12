---
title: "PowerPC 9.10 -- numerous Gnome errors after logging in"
date: 2010-02-20
forum: Apple Hardware Users
---

### Post by kingharvest on 2010-02-20
Hi --

I'm getting numerous Gnome errors after logging in... Previously everything was working fine; perhaps a software update messed things up? I have looked around for potential solutions, but none that I have tried have made any difference. The errors I get are:

The panel encountered a problem while loading:
OAFIID:GNOME_IndicatorApplet
OAFIID:GNOME_WorkspaceSwitcherApplet
OAFIID:GNOME_ShowDesktopApplet
OAFIID:GNOME_Panel_TrashApplet
OAFIID:GNOME_WindowListApplet
OAFIID:GNOME_ClockApplet
OAFIID:GNOME_FastUserSwitchApplet
OAFIID:GNOME_NotificationAreaApplet

Any advice on how I can fix this? This is Ubuntu 9.10 PowrePC installed on a PowerBook G4 -- I'd really love to be able to see the battery level remaining (and seeing the time would be nice, too ;)).

Thanks!

---

### Post by linuxopjemac on 2010-02-21
Gnome errors:
Classical problem of PRAM battery which is dead:
[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0)

Battery status:
Do you have pmu_battery loaded?
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/458004](https://bugs.launchpad.net/ubuntu/+s...er/+bug/458004)

Clock:
just add the "clock" panel to the header in Gnome (right click on header and Add to panel, then select Clock)

---

### Post by kingharvest on 2010-02-21
Thank you! Resetting the date and time via open firmware did the trick!

---

