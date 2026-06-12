---
title: "login screen resoultion to high"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Jchord.b on 2007-02-20
Hello All

I am running 6.10 and i installed the ati proprietary drivers. everything works good except my login screen resolution is to high for my monitor. the maximum my monitor can handle is 1280x1024 but the login screen is greater cause I get a: 

> Input not supported

Which is what i get if i set it to high. i tried changing my resolution and checking make default. but that did nothing to the login screen.

---

### Post by ed-j on 2007-02-20
Caution: This reply from a Novice!

If you open Terminal and type   sudo dpkg-reconfigure xserver-xorg   you will find the choices to set your monitor so it does not go above 1280x1024 in your login screen. Hope this helps!

---

