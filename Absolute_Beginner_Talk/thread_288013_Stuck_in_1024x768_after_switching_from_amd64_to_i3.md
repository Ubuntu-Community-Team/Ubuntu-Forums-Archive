---
title: "Stuck in 1024x768 after switching from amd64 to i386"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by glave on 2006-10-29
A few days ago I decided to make the switch from winxp, and I fired up edgy amd64. For the most part, everything was ok, but after a few days of struggling with some of the 64-bit issues (no flash in 64bit firefox, wine, etc) I decided to scrap it all and just use 32 bit for now.

Under the 64bit side, my monitor was detected properly, and my max res in X was 1600x1200 (default). Now that I'm back to 32 bit, it doesn't seem to recognize the monitor, and my max is 1024x768. I have the nvidia driver installed and functioning properly, but I'm not sure where my next first step should be. My monitor is a 21" Dell P1110 (also a P1130, but their identical in their capabilities).

Any pointers?

---

### Post by whatintheworldisthat on 2006-10-29
You have to reconfigure your xserver so you can choose other resolutions. To do this you must go into command line mode (ctrl + alt + f1), log in and type 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
to backup up the configuration file. (reverse to use the backup if something goes wrong)
Once you backed up type the command
```
sudo dpkg-reconfigure xserver-xorg
```
and go through the setup. Once finished press alt + f7 to go back to your desktop, log out and press ctrl + alt + backspace to restart your xserver.

note: when going through the setup, press spacebar to select your resolution and THEN press enter.

---

### Post by glave on 2006-10-29
Thank you. Perfect execution and I'm now in glorious 1600x1200 again!

---

