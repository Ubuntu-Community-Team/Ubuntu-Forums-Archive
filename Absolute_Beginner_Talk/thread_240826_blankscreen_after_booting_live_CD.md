---
title: "blankscreen after booting live CD"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by ego_brain on 2006-08-21
after booting ubuntu i get a blank screen...i tried editing xorg.conf (adding Option "MonitorLayout" "LVDS,Auto")
but then i get problems with restarting gdm...it stops, but wont restart...

my configuration is:
intel centrino 1.7
1gb ddr2
radeon x700 (128mb)
...

Domen

---

### Post by Ziox on 2006-08-21
> **ego_brain said:**
> after booting ubuntu i get a blank screen...i tried editing xorg.conf (adding Option "MonitorLayout" "LVDS,Auto")
but then i get problems with restarting gdm...it stops, but wont restart...

my configuration is:
intel centrino 1.7
1gb ddr2
radeon x700 (128mb)
...

Domen

confirmed bug: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/22985](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/22985)

---

### Post by WhiteHorse on 2006-10-20
That link is broken. Still having probs with the live CD going blank after X loads on the X700. I think it's channeling the video to the VGA port instead of the laptop LCD.

---

### Post by junglepeanut on 2006-10-20
This is a sort of a get used to with a aftermarket graphics card. Just 

sudo dpkg-recongifure xserver-xorg

choose vesa instead of ati

Then test by 

startx

You might have to restart, though.

Then install drivers with a screen so you can look at the web while you do steps (copy and paste)

Or if you feel confident, just install the drivers (make notes on sheet of paper) at the cli then it should be good.

If you can not even get to the terminal (ctrl+alt+f1) then choose single user mode and you will be root, so be careful and follow same steps.

---

