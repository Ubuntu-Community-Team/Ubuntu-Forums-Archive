---
title: "[SOLVED] fatal server error: failed to initialize core devices"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by tojulius on 2007-12-05
Hi there,

My specs: Acer aspire 1801 wsmi with Ati Radeon X600 PCi Express 64M 1440x900 resolution- Kubuntu Gutsy Gibbon 7.10 Always worked fine and never had any hardware issue whatsoever

yesterday I tried to connect a tv to my computer and set a clone screen.

I did not succeed. When I restarted I got a 800x600 screen. I tried to get my previous settings back but when I restarted I got this error in kdm

- Starting DirMngr /etc/rc2.d/S20hotkey-setup: line 17: /proc/acpi/video/*/DOS: No such file or directory.
- Startinf Powernowd:156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor :Directory nonexistent

*CPU frequency scaling not supported

*Starting AVahi mDns/dns-sd Daemon avahi-daemon [ok]
*Starting DHCP D-Bus daemon dhcdbd [ok]
*Starting Bluetooth Services [ok]
*Starting anac(h)ronistic cron acron [ok]
*Starting deferred execution scheduler atd [ok]
*Starting periodic command scheduler crond [ok]
*Checking battery state [ok]
*Running local boot scripts (/etc/rc.local)


Since I could not launch anything from there  I accessed the terminal with ctrl+alt+f1  and I tried, following the advice of many forums to reconfigure serverx (did almost 10 times)

I run startx and I got

Fatal server error:
failed to initialize core devices
disable montype:2
finished:PLL2
finished:PLL1
Entering Restore TV
Restore TV PLL
Restore TvHV
Restore TV Restarts
Restore Timing Tables
Restore Tv Standard
LEaving Restore tV

XIO: fatal IO error 104 (connection reset by peer) on server X ":0.0"
after 0 request (0 known processed) with 0 events remaining.

And that's where I am stuck

Please gimmie my Kubuntu back!!!:)

---

### Post by tojulius on 2007-12-05
The problem was solved changing the mouse input while reconfiguring serverx

I followed this thread

[http://lists.freedesktop.org/archives/xorg/2007-May/024441.html](http://lists.freedesktop.org/archives/xorg/2007-May/024441.html)

Cheers

---

