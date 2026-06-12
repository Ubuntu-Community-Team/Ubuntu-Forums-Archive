---
title: "weird backlight problem with MacBook"
date: 2007-07-14
forum: Apple Intel Users
---

### Post by anujseth on 2007-07-14
I have this really strange backlight trouble on the 2nd gen (i think) mac book. The backlight control buttons worked out of the box with feisty 7.04, this however was not persistent across boots. a better thing however was a slider option in the power management tab under System -> Preferences ... this macbook backlight control persisted across boots ... kinda of like the power managers brightness controls in sebastian kuglers power manager on kde ... now however this setting has gone ... the keyboard buttons also dont work ... thank fully however the brightness setting has persisted and i am able to use ubuntu without being blinded by white light :) .... possible causes -

1) xorg.conf got corrupted with the touchpad improvements from mac book wiki ... i have however gone back to the original so im not sure 

2) multiple kernel recompiles including the feisty update from 2.6.20.15 to 16 

i have however made the original feisty kernel my default in /boot/grub/menu.lst and should therefore be back with the original unadultrated ubuntu feisty install ... 

comments

---

### Post by benanzo on 2007-07-14
I experience the backlight control issue periodically as well.  However, it never happens to me after a cold boot, it's always after I resume from suspend.  But even then it happens maybe one in twenty times.  The problem is that the backlight control keyboard keys don't work and the screen brightness applet has a red circle with a line through it.  The screen brightness is set at maximum when this happens.

My quick fix has been to log out, then restart X (CTRL-ALT-BACKSPACE) then log back in.  I have 100% success with that.  However, it is important to log out first in order to properly stop/start your GNOME session cleanly so you don't leave any lingering bits or crashed apps.  I have had mixed success when I just kill X right from my desktop session.

This leads me to believe that it's a GNOME issue more than something like kernel or Xorg.

---

### Post by anujseth on 2007-07-14
mines different as in the problem ... i read some where that beryl causes such things ... but its not that ... 
it was either the kernel update from update manager or one of the stunts on the mac book wiki ... not sure ... re - installed ...

---

