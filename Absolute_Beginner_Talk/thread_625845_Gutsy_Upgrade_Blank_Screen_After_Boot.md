---
title: "Gutsy Upgrade: Blank Screen After Boot"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by vergeh on 2007-11-28
Well, I updated Feisty to Gutsy. Big mistake. The splash screen on bootup runs fine, but afterward by screen goes dark and the monitor goes into power saver mode. This is different than the documented error. I think my resolution for the gnome environment is set improperly, but I lack the command line skills to check and confirm this problem - how would I go about doing that from the recovery console?

---

### Post by civic_si on 2007-11-28
the refresh rate is set too high for the monitor. you can manually edit the Xorg.conf file its located in /etc/X11/xorg.conf

there should be a line there for the screen and you can edit the refresh rate section.

example

Section "Monitor"
             Identifier          "Monitor0"
             ModelName       "LCD Panel 1280x1024"
             HorizSync          31.5 - 64.0
             VertRefresh      56.0 - 65.0
             Option              "dpms"
EndSection

In order to find out what refresh rate you need you can look up the monitor specs online.

---

### Post by vergeh on 2007-11-29
Er...what command do I use to manually edit the conf?

---

