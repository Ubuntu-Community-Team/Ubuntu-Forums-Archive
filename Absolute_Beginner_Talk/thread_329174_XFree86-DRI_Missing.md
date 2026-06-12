---
title: "XFree86-DRI Missing"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by jay81 on 2007-01-01
When I try to start an OpenGL program like glxgears or beryl, I get this error message

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

Does anyone know how to install XFree86?

---

### Post by steve.horsley on 2007-01-01
I don't know what your problem is, but I don't think you should be looking to install XFree86. Ubuntu started using xorg instead of XFree86 a year or two ago. 

The error message above is about a missing GL extension. This may mean that you don't have 3D accelerated drivers installed for your graphics card. What version of Ubuntu are you running, and what type of graphics card do you have?

You may find the answer you want here:
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
Follow the link to your version and then search for "Graphics Driver".

---

### Post by jay81 on 2007-01-01
I have an ATI Radeon 9200 video card.

I did think this was an issue with the OpenGL drivers.  My thinking that if I install latest ATI video drivers, this should hopefully sort this out.:confused:  I have been have not been able to get beryl running, even after following various guides.

I have downloaded the latest drivers from the ATI website and it is .RUN file, what do I do with that?

---

### Post by taurus on 2007-01-01
Have you tried using this guide to install the latest ATI driver for your card?

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by jay81 on 2007-01-01
I followed the above guide a now my system won't even boot now :( 

All I get is the Ubuntu splash screen, and then a black screen then the monitior turns off.

Any ideas??:confused:

---

### Post by steve.horsley on 2007-01-01
Ctrl-Alt-F2 might get you a text screen where you can log in and attempt to undo the mess.
Ctrl-Alt-F7 should switch you back to the GUI screen.

---

