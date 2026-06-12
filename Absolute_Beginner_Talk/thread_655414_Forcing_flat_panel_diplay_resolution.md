---
title: "Forcing flat panel diplay resolution"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by radi0j0hn on 2008-01-01
I have an HP machine with a 20' inch display,  I cannot find a way to set the resolution to the 1600 wide setting.  The screen is 100% filled, but all my images have the wrong aspect ratio. Some step-by-step help would be appreciated.

TIA  John

---

### Post by taurus on 2008-01-01
What graphic card do you have and you installed a driver for it?  See if you get the right resolution when you reconfigure the X server with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X again with <Ctrl><Alt>Backspace.

---

### Post by kestrel1 on 2008-01-01
Does your graphics card support 1600 wide resolution?
To change the Resolution go to System - Preferences - Screen Resolution.
That should show you the resolutions supported by your system.

---

