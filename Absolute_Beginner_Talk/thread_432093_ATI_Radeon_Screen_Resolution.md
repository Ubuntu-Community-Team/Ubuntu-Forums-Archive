---
title: "ATI Radeon Screen Resolution"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by RyanFaith88 on 2007-05-03
I recently installed Ubuntu 7.04 on my computer as a dual boot with Windows MCE.  I have an ATI Radeon X600 graphics card, and I am having problems with my screen resolution.  When I first installed Ubuntu, everything worked great, and I started to use the Desktop Effects at 1280x1024 resolution.  About two days later, after one of many reboots, I am only able to boot into 800x600, which I find to be an annoying resolution.  I tried using the restricted driver provided by ATI, and that lets me have my screen at 1280x1024, but it takes away some of the functionality that I found great in Ubuntu, specifically the desktop effects.  I tried installing Beryl, but that doesn't want to work either.  Is there anything that I can do to use the open source driver at 1280x1024?

---

### Post by Kobalt on 2007-05-04
Check in you xorg.conf file if this resolution is present first (in the last parts of the file) : ```
cat /etc/X11/xorg.conf
```
If it's not, type in a Terminal ```
sudo dpkg-reconfigure xserver-xorg
```
Select the resolutions you want as available by hitting the spacebar and then validate with Enter. Restart your X with Ctrl+Alt+Backspace and it should be ok.

---

