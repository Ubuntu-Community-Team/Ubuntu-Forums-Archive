---
title: "extension &quot;GLX&quot; missing on display &quot;:0.0&quot;..."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-09-21
When i tried running alien arena it would load.

then i ran it in shell to see what was the output.

i got...


" /usr/games/alien-arena
using /root/.alien-arena/data1/ for writing
using /root/.alien-arena/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - invalid mode
Initializing OpenGL display
...setting mode 3: 640 480
Received signal 11, exiting..."


This also got into the way of compiz and other games.

---

### Post by asmoore82 on 2007-09-21
What video card do you have?

---

### Post by phizikal on 2007-09-21
Nvidia.. I forgot what model...

---

### Post by phizikal on 2007-09-21
Please help someone? Sorry for the double post tho... =/

---

### Post by asmoore82 on 2007-09-21
have you loaded the proprietary driver?
also check these just to make sure(my output is included):
```

**crystal@crystal-desktop:~$** grep nv /etc/X11/xorg.conf
        Driver          "nvidia"
**crystal@crystal-desktop:~$** grep glx /etc/X11/xorg.conf
        Load            "glx"
```

---

### Post by phizikal on 2007-09-21
Yes I did...

"r# grep nv /etc/X11/xorg.conf
    Driver         "nvidia"
# grep glx /etc/X11/xorg.conf
    Load           "glx"
"

---

### Post by phizikal on 2007-09-21
bump*

---

### Post by asmoore82 on 2007-09-21
check/post the output of
```
~$ glxinfo | grep vend
```

how did you install the nVidia driver(Restricted Drivers Manager,ENVY,etc.)?

---

### Post by phizikal on 2007-09-21
# glxinfo | grep vend
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

### Post by raposatu on 2007-09-22
To fix it, you may need to disable composite extension.

Add this to your xorg.conf

```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

---

