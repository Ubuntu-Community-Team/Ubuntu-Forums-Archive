---
title: "cant run ePSXe in gutsy :S"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-18
trying epsxe in terminal, nothing happens no messages nothing :S

---

### Post by Redflame on 2007-10-18
same here ):

---

### Post by @vijay@ on 2007-10-19
same here too

---

### Post by comp9z on 2007-10-19
[pSX]("http://psxemulator.gazaxian.com/") works great at least :) 
Just need to install libgtkglext1 package (sudo apt-get install libgtkglext1) and run the executable from the archive.

---

### Post by dynamethod on 2007-10-20
actually pSX doesnt work for me either :S

driver im using is the fglrx driver for ATI
fglrxinfo output:

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6747 (8.40.4)

However i still get this when trying to run pSX:

Xlib: extension "XFree86-DRI" missing on display ":3.0".

when starting pSX, its really really laggy and the sound is very choppy too

getting this as well:

sound: underrun

m using pSX v 1.13

---

### Post by Dark Aspect on 2007-10-24
You can use the windows version of epsxe on wine with almost no problems,thats what I do since I can't install epsxe natively anyway since I am using 64-bit Ubuntu.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3801]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3801")

With any luck maybe a fan of epsxe will create a 64-bit version some day,Although I don't think its open source.

---

### Post by alcatraz678 on 2007-10-26
> **Dark Aspect said:**
> You can use the windows version of epsxe on wine with almost no problems,thats what I do since I can't install epsxe natively anyway since I am using 64-bit Ubuntu.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3801]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3801")

With any luck maybe a fan of epsxe will create a 64-bit version some day,Although I don't think its open source.

I can't choose any plugins in the menu while using Wine for epsxe. Even if I installed all the required plugins. The drop down menu just don't show the plugins I installed.

---

### Post by mekura on 2007-10-26
The solution posted [_here_]("http://ubuntuforums.org/showthread.php?t=95835&page=18") worked wonderfully for me.

---

### Post by Dark Aspect on 2007-10-28
> **alcatraz678 said:**
> I can't choose any plugins in the menu while using Wine for epsxe. Even if I installed all the required plugins. The drop down menu just don't show the plugins I installed.

I don't have that problem oddly,try using an older version of wine.

> **mekura said:**
> The solution posted [_here_]("http://ubuntuforums.org/showthread.php?t=95835&page=18") worked wonderfully for me.

This really defeats the purpose of running ePSXe though wine,Thanks for the link,now I just have to find those Linux plugins again.

---

