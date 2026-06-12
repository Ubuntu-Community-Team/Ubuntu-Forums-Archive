---
title: "[SOLVED] Screen Issues"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-08-17
I am having issues with my laptop screen now that I have installed ubuntu 7.04 over xubuntu.  (I had the issue at first with xubuntu, but the autodetect brought the monitor back to full screen.  When I try to run dpkg=reconfigure xserver-xorg I get an error message.  xserver-xorg postinst warning: error while preparing new Xorg X server configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to update existing configuration.  I have tried four or five times with no luck.  Dimension 8000 piii 700mhz w/512mb RAM.

---

### Post by overdrank on 2007-08-18
> **soaklord said:**
> I am having issues with my laptop screen now that I have installed ubuntu 7.04 over xubuntu.  (I had the issue at first with xubuntu, but the autodetect brought the monitor back to full screen.  When I try to run dpkg=reconfigure xserver-xorg I get an error message.  xserver-xorg postinst warning: error while preparing new Xorg X server configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to update existing configuration.  I have tried four or five times with no luck.  Dimension 8000 piii 700mhz w/512mb RAM.

Hi I have had this happen to me one time. When you reinstalled did you happen to get a warning about installing the system on a unclean drive may cause problems? And on the command have you tried 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And which driver are you choosing when you run the command? And what type video card are you using?

---

