---
title: "Wireless Assistant program install went wrong?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-04-12
Hi I am installing wlassistant or also known as wireless assistant and I thought I had all the dependencies installed but this is the error I get when I try to open it from the internet menu.

Oh also I reran wlassistant.........deb file in the terminal and this is what I got. Please note I have installed all of the dependancies it says I haven't got.
~/Desktop# dpkg -i wlassistant_0.5.6-1_i386.deb
(Reading database ... 95863 files and directories currently installed.)
Preparing to replace wlassistant 0.5.6-1 (using wlassistant_0.5.6-1_i386.deb) ...
Unpacking replacement wlassistant ...
dpkg: dependency problems prevent configuration of wlassistant:
 wlassistant depends on kdelibs-bin; however:
  Package kdelibs-bin is not installed.
  Package kdelibs4c2a which provides kdelibs-bin is not configured yet.
 wlassistant depends on kicker; however:
  Package kicker is not configured yet.
 wlassistant depends on menu; however:
  Package menu is not installed.
 wlassistant depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 wlassistant depends on libqt3-mt (>= 3:3.3.7); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing wlassistant (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wlassistant

---

### Post by kelbizzle on 2007-04-12
I use the nm-applet with gnome. Try using aptitude to install wlassistant so it will grab all the dependencies. 

```
sudo aptitude install wlassistant
```

---

### Post by rapattack1 on 2007-04-12
I am not connected to the net on that machine. That is another thing I am still yet to fix. I have gnome-ppp and I thought I had set wvdial right but I am still a newbie linux person after all.

---

