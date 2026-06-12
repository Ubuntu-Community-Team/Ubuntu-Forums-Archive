---
title: "can't disable trackpad on my macbook 5.1 with Ubuntu"
date: 2011-06-07
forum: Apple Hardware Users
---

### Post by jonsatin on 2011-06-07
Hi, I was running Ubuntu 10.4 and for some reason lost the ability to disable the trackpad.  At first I could, but last night stopped working.  I upgraded to 11.4 today and still can't disable it.  I've tried going to mouse options in system and everything, any ideas?

---

### Post by dubmartian on 2011-06-08
try pasting the following into gnome-terminal (no sudo needed unless changing for root user)   gconf-editor /desktop/gnome/peripherals/touchpad/touchpad_enabled

---

### Post by jonsatin on 2011-06-08
Just tried it, but it didn't seem to disable tap to click still....

---

