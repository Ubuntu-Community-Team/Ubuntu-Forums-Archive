---
title: "Screen Display on laptop external VGA"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by bribren on 2007-03-25
Hello all, 
I am absolute noob and cannot figure this one out.

I have a dell latitude with ATI rage mobility pci card and a screen that doesn't work.  I run this PC on an external VGA monitor.  

When I log into gnome, I have to scroll around to see the entire screen.  I only have one resolution choice under desktop display.

I can find the xconfig file in /etc? but have no idea how to use it.

ANythoughts would be appreciated. Thanks!

---

### Post by machoo02 on 2007-03-25
You could try reconfiguring X.org:```
sudo dpkg-reconfigure xserver-xorg
```This will walk  you through the reconfiguration of X, which will also redo xorg.conf.  For most things just choose the default settings, and be sure to select the correct driver for your video card (ati or fglrx, depending on what you use).  There is a section about monitor configuration: choose the resolution types that you would like to use (there are many choice, pick what you think/know will work with the monitor), and let it try to autodetect your monitor settings.

Hope this helps...

---

