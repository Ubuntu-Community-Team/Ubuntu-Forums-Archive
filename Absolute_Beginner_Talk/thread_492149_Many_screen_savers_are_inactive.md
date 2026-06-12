---
title: "Many screen savers are inactive"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Norman Thom on 2007-07-04
I have just installed Ubuntu 7.04 on an 80GB drive
When I tried to activate a screensaver (specifically 'Molecules' ) I found that it was inactive.
Checking several others I found most to be inactive.
I know that they work on this machine as I also installed it on a 4GB fujitsu drive and they all work fine.
Is there any way that I can reconfigure the screensavers to activate the inactive mdules
Thanking you in advance

---

### Post by shanepardue on 2007-07-04
Do you have a proprietary video driver that allows for opengl graphics? 
It may be that your driver doesn't support the many opengl screensavers.

---

### Post by Norman Thom on 2007-07-04
Unsure about video card
Know that all screensavers work when installed in this machine (hardware remains constant) but using a different hard drive

---

### Post by shanepardue on 2007-07-04
Copy and paste this into a terminal

```
glxinfo | less
```

and see if direct rendering says yes or no.

---

### Post by Norman Thom on 2007-07-04
Thanks for the info
unfortunately here are the results I get 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by shanepardue on 2007-07-04
What video card are you using?

---

### Post by Norman Thom on 2007-07-04
Honestly don't know is there any way I can check?

---

### Post by shanepardue on 2007-07-04
Click System > Administration > Resitrcted Drivers Manager.

It'll show any hardware that might need a driver installation. 
Click any unchecked boxes enable the driver, click close, and reboot.

---

### Post by Norman Thom on 2007-07-04
Thank you very much for that fix
It seemes to have corrected that problem . . . and brought on another
my screen resolution has reverted back to 800x600 and I no longer have listings for higher resolutions, might there be a solution for this also?

---

### Post by shanepardue on 2007-07-04
Did you see which video card you had in the restricted drivers manager?

---

### Post by alienexplorers on 2007-07-04
Please post your xorg.conf file.

---

### Post by Norman Thom on 2007-07-04
It doesnt seem to mention only says NVIDA accelerated graphics drivers (legacy cards) and now marks as in use

---

### Post by shanepardue on 2007-07-04
Hold alt while pressing F2 to open a run command box.

type "gksu nvidia-settings" to bring up the nvidia control panel.

From there you will set your desired resolution under X server Display Configuration.

When you're done, click apply and "save to X configuration" file.

Then Reboot.

---

### Post by alienexplorers on 2007-07-04
Without the nvidia-glx files active the opengl files will not run properly.  Follow Shanepardue's info and you should be up and running OK.

---

