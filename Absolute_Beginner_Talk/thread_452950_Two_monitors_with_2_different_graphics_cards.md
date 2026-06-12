---
title: "Two monitors with 2 different graphics cards"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by theenglishmidget on 2007-05-23
ok so ive tried this quite a few times and all have ended up in reinstall the system. I am currently running on an ati all in wonder graphics card, and i also have a nvidia geforce. On windows i plugged in both cards, both monitors and it all worked fine. 
As i have said i have tried re writing stuff in the console and such but ive lost the xserver and had to reinstall. Again i an running an ATI All in wonder and i have an Nvidia GeForce. If someone could walk me through it i would be extremely appreciative.

---

### Post by veloce on 2007-05-24
> **theenglishmidget said:**
> ok so ive tried this quite a few times and all have ended up in reinstall the system. I am currently running on an ati all in wonder graphics card, and i also have a nvidia geforce. On windows i plugged in both cards, both monitors and it all worked fine. 
As i have said i have tried re writing stuff in the console and such but ive lost the xserver and had to reinstall. Again i an running an ATI All in wonder and i have an Nvidia GeForce. If someone could walk me through it i would be extremely appreciative.

Yes, this is something that is easy in windows and HARD in Ubuntu.  Unless someone has the exact same hardware, a walk through over the internet is not going to be feasible.

Some tips:

1. before modifying your xorg.conf, make a backup copy. "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.this1works"
2. When gdm fails to load, you can switch to a console with the ctl+alt+F1 (or F2) key combo.  From here you can go back to your working config at any time with "sudo cp /etc/X11/xorg.conf.this1works /etc/X11/xorg.conf"
3. You can restart X with the key combination ctl+alt+bksp - BUT its not as "tidy" as a restart - if it still fails try rebooting before you make more modifications.
4. When in a console you can reboot with the "sudo reboot" command. 

Now you're suitably armed to start on the howto:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

