---
title: "compile from source?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-12
downloaded the new wine, it is source only, how do I use it?

---

### Post by emarkd on 2008-02-12
If you need to build it from source, see: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Rhubarb on 2008-02-12
The easiest way to install wine is use wine's online repository.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

No need to compile, automatically get updates to wine as they come in.

Edit:  This way will give you the latest version of wine and will always be updated.

---

### Post by TheBoat on 2008-02-12
wine is available in the add/remove applications, that way you don't have to worry about compiling from source.

---

### Post by TechDragon on 2008-02-12
Want the newest version 9.55 it says it has direct x fixes and driver emulation.

---

### Post by randy78 on 2008-02-12
> **TechDragon said:**
> Want the newest version 9.55 it says it has direct x fixes and driver emulation.

I did it a few days ago... just download the source, unzip it, change to the directory and do:
./wineinstall

Be warned however, because it took FOREVER to finish on my P4 machine...

Also, you might want to sudo apt-get remove wine to uninstall the old version, just to make sure that there aren't any conflicts...

To configure it, just do: winecfg

---

### Post by Rhubarb on 2008-02-12
> **TechDragon said:**
> Want the newest version 9.55 it says it has direct x fixes and driver emulation.

Compiling it would be your best bet if you want it sooner rather than later.
If you can wait a few days, my way by using the winehq repositories should include 9.55 very soon (currently it's 9.54).

---

### Post by TechDragon on 2008-02-12
yea, I will probably just wait

---

