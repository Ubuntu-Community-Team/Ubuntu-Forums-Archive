---
title: "Enable verbose startup/shutdown messages?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by phoenix_fire2005 on 2007-07-27
I see ubuntu has these nice splash screens covering up what's underneath during startup and shutdown... but I'd like to "look under the hood" and see what's going on.

I checked a few other similar threads but none of them were very clear on what to do. I have ubuntu V7.04 x86-64.

Thanks in advance for the help!

---

### Post by trent dillman on 2007-07-27
...

---

### Post by bodhi.zazen on 2007-07-27
You need to edit /boot/grub/menu.lst

You need to remove the word "splash" from your kernel lines.

If you want this to be the default , remove "splash" from the defoptions line as well. The kopt line is the options used on your kernel line with grub (kernel) updates :

# defoptions=quiet splash

See, no splash

use quiet if you do not want to see kernel messages.

# defoptions=quiet 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by RomeReactor on 2007-07-27
Hi. If you don't want  to make this a permanent setting or don't want to edit **/boot/grub/menu.lst**, you can press ALT+F2 as the system starts to boot to switch to verbose.

---

### Post by Contrarian on 2007-07-28
> **trent dillman said:**
> edit /boot/grub/menu.lst and find the line starting with 'defoptions'

erase the word 'splash', then run sudo update-grub

then reboot

is 'sudo update-grub' needed? Seems to me if yo usave the .lst file changes will take place at next reboot, or am I wrong?

---

