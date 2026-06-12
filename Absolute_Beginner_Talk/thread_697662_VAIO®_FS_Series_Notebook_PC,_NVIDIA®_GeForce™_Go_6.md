---
title: "VAIO® FS Series Notebook PC, NVIDIA® GeForce™ Go 6400 Problem"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by timusmma on 2008-02-15
Hey All,

I'm new to Ubuntu and have been working on a issue I have with the Nvidia graphics card/restricted driver.  I've got everything working, and finally correct resolution using the alternate cd for Gutsy.  For some reason I can't get the restricted driver for geForce 6400 to work.  I've tried about everything I've found with google to try to get it to work.  If I use the restricted drivers manager or envy, when I reboot I get a blank screen.  I have to use recovery mode and dpkg-reconfigure -phigh xserver-xorg to get everything back up and running, but it leaves me back to square one... my GeForce 6400 not enabled.

Please help if possible!

Many Thanks.

---

### Post by ashmew2 on 2008-02-16
After rebooting when you get a black screen , how about trying 

```
nvidia-config
```

and rebooting ?

if that too doesnt work , backup your Xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Restore your graphical interface by using the command you mentioned and post the contents of the /etc/X11/xorg.conf.backup here.
By the way , Instead of using the recovery mode , cant you just use a virtual terminal (open it by pressing CTRL ALT F1) and typing the commands in there ?

---

