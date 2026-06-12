---
title: "trouble getting my nvidia card going"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by wadetuple on 2006-09-02
hello...

i'm trying to use google earth, but it's having trouble with my nvidia riva tnt card - i installed the nvidia-legacy-glx package and thought i had installed it ok, but when i did:

glxinfo | grep rendering

i got...

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

any help or ideas gratefully received..

---

### Post by NESFreak on 2006-09-02
have you loaded the glx extension in xorg.conf?
check in /etc/X11/xorg.conf for the line 
```
	Load	"glx"
``` in Section "Module"
NESFreak

---

### Post by wadetuple on 2006-09-04
hello NESfreak,

under "section  module" in xorg.config there is a line that says Load "glx"

this is as it should be?

---

