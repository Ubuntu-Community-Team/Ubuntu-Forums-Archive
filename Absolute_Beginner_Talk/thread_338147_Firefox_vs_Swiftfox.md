---
title: "Firefox vs Swiftfox"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by shadowphoenix on 2007-01-14
I have manage to install both browser in my pc and i have decided to use Swiftfox.Does anyone knows how can i remove firefox because i want to save some space.

---

### Post by energiya on 2007-01-14
I tried to remove Firefox (using Synaptic), but a lot of things started functioning the wrong way, so i don't recomand it.

---

### Post by God.Jr on 2007-01-14
i would try typing this in the terminal:
general removal
----------------------
sudo apt-get remove <package name>

removing firefox
----------------------------
sudo apt-get remove firefox


i think that is how it would be done not to  sure these where the directions for uninstalling packages /programs.....should work

by the way i was wondering wat swiftfox is like compared to firefox............been thinking about changing

---

### Post by energiya on 2007-01-14
> **God.Jr said:**
> 
by the way i was wondering wat swiftfox is like compared to firefox............been thinking about changing

Faster ;)

---

### Post by shadowphoenix on 2007-01-14
Really fast:D

---

### Post by God.Jr on 2007-01-14
yeah thats wat i heard.......... ok off to install and give it a test

---

### Post by maxamillion on 2007-01-14
```
sudo aptitude purge firefox
```

That command should remove firefox and all of it config files (or otherwise associated files)

Swiftfox is nice but I have heard issues with firefox plugins being used under swiftfox

---

### Post by luisito on 2007-02-20
I read an article here:
[http://www.apcstart.com/3097/whats_the_worlds_fastest_browser](http://www.apcstart.com/3097/whats_the_worlds_fastest_browser)
where it says swiftfox is only marginally faster than firefox, but actually they are both quite a bit slower than konqueror. His test is quite limited though.

---

### Post by r4ik on 2007-02-20
To my knowledge they are both running the same engine wich imo means firefox can't be removed.
Could be wrong...

---

### Post by aysiu on 2007-02-20
From [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion): > Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine.

---

### Post by kerry_s on 2007-02-20
What i do is rename the swiftfox folder to firefox and replace the firefox folder and copy the plugins over. That's it 1 browser and every things still happy, the down side is if theres a firefox update swiftfox gets over written, but when was the last time firefox was updated. :)

---

