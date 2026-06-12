---
title: "Help On Video card"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by fecalites on 2006-09-20
Help on Nvidia Graphics Card.

I have an Nvidia GeForce MX4000 video card with 128MB video memory. I'm running on a P4 1.6 Ghz processor. After installing
the package nvidia-glx on my system, I typed the following to know if I had the driver installed correctly.

hackman@supercomputer:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Could you please tell me what does this messages mean? I'm just new to linux and don't know what does this mean.

---

### Post by croak77 on 2006-09-20
Did you load the nvidia driver, change your xorg.conf, and restart X?

---

### Post by fecalites on 2006-09-20
Nope, i haven't done that. See the problem is I don't know what should I be putting in the config file... can you help me on this one? Thanks.

---

### Post by croak77 on 2006-09-20
Just open up your xorg.conf, From a terminal type;

```
gksudo gedit /etc/X11/xorg.conf
```

Look for the Section "Device". It should have your driver as nv. Just change to nvidia, save and logout and log back in . You should see the Nvidia logo before gdm boots.

---

### Post by fecalites on 2006-09-20
Ok! Thanks for the Help!

---

### Post by muffinhead on 2006-09-20
Actually Wouldn't it be easier to change it in a gui like window, instead of manually editing the xorg.conf, this might not be a very good idea for beginners to attempt.


After installing nvidia-glx or the nvidia driver

i.e. type in a terminal:

sudo dpkg-reconfigure xserver-xorg

that should allow you to edit your xorg.conf, in a small sort of gui based terminal window;)

---

### Post by croak77 on 2006-09-20
No biggie. I prefer editing xorg.conf and changing 'nv' to 'nvidia'. Really not that hard. GUI doesn't always mean newbie friendly.

---

