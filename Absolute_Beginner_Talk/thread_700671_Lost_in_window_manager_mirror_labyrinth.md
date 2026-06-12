---
title: "Lost in window manager mirror labyrinth"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by luria on 2008-02-18
Hi! I use my ubuntu 7.10 with the openbox window manager.  Somehow i managed to rescue a borked mythtv install my removing mythtv packages and setting ubuntu to use openbox. This worked fine, and i really like openbox.

Today my problems started:
I did an apt-get update and an apt-get upgrade.

After reboot all i get is some flicker after the load bar is full, then a window saying that "Ubuntu is running in low-graphics mode".  Trying to reconfigure xorg trough this window OR doing a "dpkg-reconfigure xserver-xorg" goes nowhere - the settings does not stick, xorg.conf is unchanged.

However, ssh'ing to the PC and doing a /etc/init.d/gdm stop followed by a killall Xorg does the magic - the screen goes black momentarily  and then my good old desktop is back.

Pls can someone help me remove the settings that obiously are trying to load two window managers?

---

### Post by luria on 2008-02-18
I resolved it.  First I removed nvidia-glx, then reinstalled nvidia drivers. I also did a rm -rf .gnomerc .gnome2 .metacity  Not sure what did the trick though.

---

