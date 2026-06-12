---
title: "upgrade to 10.10 on MacBook2,1"
date: 2010-10-15
forum: Apple Hardware Users
---

### Post by dvandok on 2010-10-15
I've upgraded to Ubuntu 10.10 (Maverick) yesterday and I want to share some of the hilights. This is on an Apple MacBook 2.1.

The upgrade went ok, but after the reboot I couldn't log into my normal Gnome session. The failsafe did work, and after much prodding around I came upon a file ~/.config/autostart/xrandr.desktop that I probably created myself. It runs

```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```which I used to need for the brightness buttons to work. This caused a crash of the X server. Apparently I no longer need this hack since the brightness buttons work fine now.

The touchpad behaved very erratically, but after unloading/reloading the appletouch module this got a bit better. I messed around with the gpointing-device-settings and I managed to crash that app. It now crashes consistently and I don't even know why.

I ended up getting rid of almost all of my .gconf, .gconfd, .config, etc. settings because the panel had become a mess. I had two separate, but different volume control settings, neither seemed to have anything to do with the actual sound settings.

It seems that if you upgrade a pristine system, it's allright, but once you've made some manual tweaks (and these are needed, unfortunately!) this may mess up your experience after the upgrade. Better keep track of those tweaks!

The resume from sleep when I opened the lid this morning failed; I've heard this from other people as well on other hardware.

But overall the experience is that it's mostly business as usual, which is good.

---

