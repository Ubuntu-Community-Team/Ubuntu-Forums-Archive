---
title: "NEW Mysterious working NVIDIA card"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-10-12
OK! It took me aalllll day to get tha nvidia card in there to work. i had to black list my onboard to do it. 

But my problem is this, my nvidia 6200 that is running now wont output anything when i type

" glxinfo | grep render" it gives me this error. 

```
rav@rav-desktop:~$ glxinfo | grep render
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
rav@rav-desktop:~$ 

```

And when i go to my Nvidia settings it tells me this > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

But when i follow those instructions, it modify my Xorg, to use the 'Nvidia' driver, and my card only works on "NV' Driver...

So how can i really get the driver for my card when it sayin i need to use 'Nvidia" when it works with 'NV' only?

---

### Post by dcstar on 2007-10-12
> **ritterrav said:**
> OK! It took me aalllll day to get tha nvidia card in there to work. i had to black list my onboard to do it. 

But my problem is this, my nvidia 6200 that is running now wont output anything when i type

" glxinfo | grep render" it gives me this error. 

```
rav@rav-desktop:~$ glxinfo | grep render
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
rav@rav-desktop:~$ 

```

And when i go to my Nvidia settings it tells me this 

But when i follow those instructions, it modify my Xorg, to use the 'Nvidia' driver, and my card only works on "NV' Driver...

So how can i really get the driver for my card when it sayin i need to use 'Nvidia" when it works with 'NV' only?

Do a forum search on installing the right Nvidia driver for your card.

---

### Post by Daveth on 2007-10-12
have a wander through this

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by steve.horsley on 2007-10-12
> But when i follow those instructions, it modify my Xorg, to use the 'Nvidia' driver, and my card only works on "NV' Driver...

So how can i really get the driver for my card when it sayin i need to use 'Nvidia" when it works with 'NV' only?

It may be important that the default driver is "nv" not "NV", and the nVidia driver is "nvidia", not Nvidia" or "nVidia".

You did intall the nvidia drivers, didn't you? I don't know about the 6200 - whether it's supported by the drivers in the Ubuntu repositories. I suggest you try this command:
**sudo apt-get intall nvidia-glx-new**
to start with. If that doesn't work, you may need to get the latest drivers from nVidia and install/compile those.

---

