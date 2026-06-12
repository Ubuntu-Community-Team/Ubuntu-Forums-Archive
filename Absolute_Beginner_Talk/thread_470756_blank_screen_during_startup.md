---
title: "blank screen during startup"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2007-06-11
I get blank screen after initial booting. so I don't get to know whats happening. however the booting process continues and the log-in screen appears after few minutes. seems X does not start if I am not wrong. It happens with Kubuntu/xubuntu\Ubuntu\Edubuntu, live or harddrive installed. Can I solve the problem? if yes how?

Raj

---

### Post by Kobalt on 2007-06-11
The Usplash, which you should see instead of the blank screen, must use a too high resolution for your screen at boot time. To change this resolution, edit this file ```
gksu gedit /etc/usplash.conf
```
Set the resolution to something lower, like 800x600, or even 640x480 : > # Usplash configuration file
xres=800
yres=600
Reboot, and that should do it.

---

