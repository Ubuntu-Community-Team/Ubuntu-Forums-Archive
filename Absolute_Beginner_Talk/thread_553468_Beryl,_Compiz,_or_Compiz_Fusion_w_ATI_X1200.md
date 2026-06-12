---
title: "Beryl, Compiz, or Compiz Fusion w/ ATI X1200"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by GraFfiX420 on 2007-09-17
I have a Toshiba Satellite A215-S4757. I was able to get my ATI restricted drivers installed, and my wiFi working with ndiswrapper. But, using several guides, as good as I can do with compiz fusion is get Xgl to work and wobbly windows. Is their any suggestions as to how I could get this working with cube effects? The laptop has 2 gig of ram, an AMD Turion64/1.8, and a 250gb HD. It has a radeon mobility X1200. Any help would be greatly appreciated.

---

### Post by oilchangeguy on 2007-09-17
try this:
[http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/)

---

### Post by asmoore82 on 2007-09-17
the current proprietary ATI drivers do **not** support the AIGLX extension of Xorg.
so while is it possible to get compiz working with them by using Xgl **instead of** Xorg,
I would just wait until next month when the 8.42 version of ATI Linux/Xorg drivers come out,
which have promised to support Xorg/AIGLX/compiz.

---

### Post by GraFfiX420 on 2007-09-17
Thanks for the replies. I have to say right from jump, ubuntu us without a doubt one of the most impressive OS's i've ever seen. I can't wait for the proprietary ATI drivers next month, but, being the impatient guy that I am, i'm gonna try looking glass. Does anyone have a definitive guide for making compiz work under XGL? Like I said, I can get it to work partially, but no cube, which, to me, make's it pretty much not working.

---

### Post by asmoore82 on 2007-09-17
> **GraFfiX420 said:**
> Thanks for the replies. I have to say right from jump, ubuntu us without a doubt one of the most impressive OS's i've ever seen. I can't wait for the proprietary ATI drivers next month, but, being the impatient guy that I am, i'm gonna try looking glass. Does anyone have a definitive guide for making compiz work under XGL? Like I said, I can get it to work partially, but no cube, which, to me, make's it pretty much not working.

oh sorry, I missed the Xgl bit in your original post ...

you need to configure compiz to load the "cube" plugin.
up until very recently, the only way to configure compiz was by changing its keys in 'gconf-editor'
now, there is the compizconfig system which, if you have installed the recent 0.52 beta
of compiz, should show up at "System -> Preferences -> CompizConfig Settings Manager"

the cmd for this compizconfig control panel is
```
~$ ccsm
```

---

### Post by GraFfiX420 on 2007-09-18
This is weird, I got it to work for a while last night, until I tried to adjust the brightneww on my monitor, then it freaked. Now, it will only work until I try to zoom out of the cube, then it will zoom out for a second and then zoom back in and doesn't work anymore...

---

### Post by GraFfiX420 on 2007-09-18
Figured it out, it was the opacity plugin, and I guess it's fairly well documented that it doesn't work in the updated builds. What's weird is that it would never work with the proprietary drivers from ATI. I had to use the xorg fglrx drivers. Will the drivers released next month be proprietary or will they be from xorg? Also, are they the same drivers that are posted in the experimental section?

---

