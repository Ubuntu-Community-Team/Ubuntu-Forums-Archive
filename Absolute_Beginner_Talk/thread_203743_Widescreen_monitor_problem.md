---
title: "Widescreen monitor problem"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by elevation2k on 2006-06-25
I was wondering how to change my screen resolution. I've heard that Ubuntu doesn't really like widescreen LCDs, and tried Googling to find an answer, but so far, not a whole lot that I've found seems to be very helpful. I'm using a Sony Vaio FS notebook with integrated Intel GMA graphics and a 15" screen. I'd like to set the resolution to 1280x800 but the only option in System>Preferences>Screen Resolution is 1024x768. Can someone help me out please, or at least direct me somewhere that can walk me through changing it step by step?

---

### Post by Winblowz on 2006-06-25
Open the terminal and do...
```
sudo dpkg-reconfigure xserver-xorg
```
then, reboot

---

### Post by aysiu on 2006-06-25
[This](http://www.linux-laptop.net/hosted/fs215e-slackware.html) may help.

---

### Post by aysiu on 2006-06-25
[QUOTE=Winblowz]Open the terminal and do...
```
sudo dpkg-reconfigure xserver-xorg
```
then, reboot[/QUOTE]
When you've edited the xorg.conf file, you don't need to reboot. Just do Control-Alt-Backspace. This resets the X server and takes you back to the login screen.

---

