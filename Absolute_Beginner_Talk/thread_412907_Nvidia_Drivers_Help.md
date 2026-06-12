---
title: "Nvidia Drivers Help"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by thypeacefrog on 2007-04-18
HI I'm using edgy on my dell m1210 and was for a while, then I took it off and wiped my hard drive so that I could set up a dual boot with vista. I reinstalled Edgy today and now my nvidia drivers aren't working I've been trying uninstalling and installing trying to get them working all day but can't see to find how. When I check if direct rendering is enabled I get this error message:

jack@jack-laptop:~$ glxinfo | grep direct
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


Any ideas? I saw stuff about this on other forums but not really a solution I could understand I'm pretty nub when it comes to linux so some help would be greatly appreciated.

---

### Post by annda on 2007-04-18
first, add this line to /etc/X11/xorg.conf in the nvidia device section

Option          "AddARGBGLXVisuals"             "True"

while you look at the file, make sure that you are using the nvidia, not the nv driver.

---

### Post by Michl on 2007-04-25
I had the same problem after I installed nvidia-glx legacy package.  I chose
it because I have NV5 TNT2...  Then I replace it with nvidia-glx and nothing
helped.  So I took both of them out and rebooted and everything is on track
but no direct rendering.   However, all the screensavers work although some
are not as smooth as they should be.  I am using the nv driver that comes with
the kernel.

---

