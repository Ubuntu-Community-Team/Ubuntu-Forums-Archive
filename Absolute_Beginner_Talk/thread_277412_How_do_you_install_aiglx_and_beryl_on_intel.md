---
title: "How do you install aiglx and beryl on intel?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-10-14
I tried using this guide [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

but something went horribly wrong when I did it so I had to formate. Now does anyone have another guide which I can try to use to set it up?

---

### Post by jincast90 on 2006-10-15
Bump

And another question. What should I use?

Compiz/xgl
Compiz/aiglx
Beryl/xgl
Beryl/aiglx

I dont know what would be the best

---

### Post by almahtar on 2006-10-20
In general AIGLX is preferable to XGL, but it's hard to get AIGLX working with NVidia and ATI cards (ESPECIALLY ATI...).  It's actually pretty easy with Intel video, so you're in luck.  I'd go with AIGLX if I were you.

As far as Compiz vs Beryl: depends.  Beryl seems to have more active development and faster release cycles, so you'll get lots of bling bling with it, but it may (I'm not sure) be less stable than official Compiz.  I'd try both if I were you.

---

### Post by jordanmthomas on 2006-10-20
That wiki looks like it should work fine.
However, you need to be careful at this part:
> 
EXACTLY like this (depends on your graphic chip):

Section "Device"
 Identifier "Intel Corporation Intel Default Card"
 Driver "i810&#8243;
 Option "XAANoOffscreenPixmaps"
 BusID "PCI:0:2:0&#8243;
EndSection

In this section, leave everything alone and just add the XAANoOffscreenPixmaps part in.  Chances are, you renamed your graphics card but not in both places it's needed.

---

