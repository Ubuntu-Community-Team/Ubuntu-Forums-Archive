---
title: "Dual monitors, primary monitor not working."
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Kevin Jones on 2008-02-29
Hello all,
I have 7.10 on a dell xps 200 and the Gnome desktop.
I have an ATI radeon X1300 graphics driver.
The driver is configured under the 'restricted drivers' application is set to 'enabled'.
I have dual monitors. When I boot in to the system the primary monitor remains blank. I am not at my  home pc now so I can't say exactly, but the message is... Cannot display resolution....
My second monitor is working but is set at the lowest resolution possible. The writing barely fits on the screen it is so large.
I have tried to set the screen resolution to higher but the screen will not allow me to make any adjustments. Despite  having logged in as an administrator.
I have been in a similar situation before, and I think it is there is a command I can input, something like
config glxr.
Or something like this.
Can any one help me with get the primary screen working?

Kevin

---

### Post by rapiscan on 2008-02-29
Dual monitors is non-trivial with an ATI card and proprietary drivers.  First, the resolution problem sounds unusual, I would start by reconfiguring X.
```
sudo dpkg-reconfigure xserver-xorg
```

Then, use this guide for dual monitor setup:
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

Unfortunately, I can't promise that it will work for you, but it worked for me and seems to work for most users with ATI cards.

---

