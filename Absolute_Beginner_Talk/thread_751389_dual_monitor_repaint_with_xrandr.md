---
title: "dual monitor repaint with xrandr"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by perubu on 2008-04-10
Hi,

I am using Ubuntu / Gnome on a laptop with a 2nd monitor and xrandr to use a dual screen with the following command:

xrandr --output LVDS --mode 1440x900 --output VGA --auto --right-of LVDS --rotate left

this works fine but window refreshing is very slow, the monitor wipes a white shadow every time I want to move a window.

in xorg.conf I specified VideoRam 1000 in Section "Device" as follows,

Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
VideoRam 1000
Option "monitor-VGA" "VGA"
Option "monitor-LVDS" "LVDS"
Option "monitor-TV" "TV"
EndSection

any suggestion greatly appreciated

Père Ubu

---

