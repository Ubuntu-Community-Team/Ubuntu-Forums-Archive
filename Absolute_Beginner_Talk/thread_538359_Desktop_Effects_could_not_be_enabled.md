---
title: "Desktop Effects could not be enabled"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by dorogavtsev on 2007-08-29
Desktop Effects could not be enabled...

When I'm trying command: desktop-effects
Is gives me: nvidia hardware not available

How to fix it?

---

### Post by rsambuca on 2007-08-29
What videocard do you have, and what drivers are you using?

---

### Post by abhilash82 on 2007-08-29
Try installing the restricted drivers for your graphics card. In order to run desktop effects your xorg.conf must have you Nvidia card configured properly. You can find the file at /etc/X11/xorg.conf.

```

glxinfo | grep

```This should return the rendering as yes. Also post your Xorg.conf file.

You can also use the link given below for your driver installation.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

