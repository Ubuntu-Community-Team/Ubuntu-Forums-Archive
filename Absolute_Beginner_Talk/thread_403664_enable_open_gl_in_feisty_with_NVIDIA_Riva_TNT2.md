---
title: "enable open gl in feisty with NVIDIA Riva TNT2"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by wcampbell on 2007-04-07
Hello,

I'm trying to enable open gl in feisty.  It was working in the previous distrubution, but not since.  I have installed the nvidia-glx-legacy driver through the restricted drivers manager, but the status says "needs computer restart" and has stayed that way since the install (tried it a few times actually).

Most of what I have read seems to indicated that in previous distributions this was solved using Envy, but I doesnt look like there is a version of Envy that will work with Feisty.

Thanks in advance for any help you might be able to provide.

Warren
P.S.
maybe this is useful info:

warren@warren-desktop:~$ glxinfo | grep direct
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by wcampbell on 2007-04-07
hmmm... why has no one even viewed this post?

---

### Post by Valstorm2323 on 2007-04-11
I get same thing, I have Nvidia RIVA TNT2 

I swear our logs are exactly the same.


I have edgy, got envy, installed driver manually, rebooted and got a whie screen+vertical lines.

Rebooted grap recovery mode, ran envy again, installed manually and configured Xserver-xorg file manually.

Rebooted and boom I had my nvidia working but the GLX stuff comes out like yours.

---

