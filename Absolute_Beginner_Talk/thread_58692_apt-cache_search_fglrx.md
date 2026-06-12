---
title: "apt-cache search fglrx"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by olope on 2005-08-21
Hi people!  :) Just my first post.

I'm trying to install my ATI drivers and I saw that I have to do it to install fglrx-drivers but when I put ** apt-cache search ^fglrx** just it return to me the following:

[B]xfree86-driver-fglrx - Video driver for the ATI graphics accelerators
xfree86-driver-fglrx-dev - Video driver for ATI graphics accelerators (devel files)[/B] 

I have installed Xorg, but seems that I haven't the drivers on my repositories.

Thanks  :)

---

### Post by DJ_Max on 2005-08-21
Take a look here.
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

If you're using 4.10 "Warty" then you have XFree86, if you have 5.04 "Hoary", then you have Xorg.

If you're using Hoary, the package is *xorg-driver-fglrx*

---

