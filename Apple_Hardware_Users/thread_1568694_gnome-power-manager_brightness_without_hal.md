---
title: "gnome-power-manager brightness without hal"
date: 2010-09-05
forum: Apple Hardware Users
---

### Post by heluani on 2010-09-05
Hi there, I'm running 2.6.35 on a macbook Air. Since Hal is being deprecated I got rid of it but now I cannot control brightness with the keyboard. 

Looking at the code on gnome-power-manager, if it doesn't find hal it defaults to xrandr, but I couldn't find a way of controlling brightness with xrandr. Also, I don't see any keybindings on XF86MonBrightness{Down,UP} with gnome-keybindings-properties.

I'm loading mactel's nvidia_bl module which creates /sys/class/backlight/nvidia_backlight and from there I can just adjust brightness by editing the corresponding file. 


Is there any patch to gnome-power-manager to use this sysfs entries and with udev, but not hal?

---

### Post by heluani on 2010-09-17
Well, in case someone is having my same setup: nvidia-bl module to control brightness and udev with no haldaemon, here's a small daemon on dbus to control brightness via /sysfs and a patch to gnome-power-manager-2.30.1 to control brightness via this daemon (the gpm* files should go in the src/ directory). It's quite simple with no error control but it does the trick for me. Later I found out that this is essentially what the guys in the mactel team had already done with the hald addition to nvidia. 

R.

[ATTACH]169781[/ATTACH]

[ATTACH]169782[/ATTACH]

---

