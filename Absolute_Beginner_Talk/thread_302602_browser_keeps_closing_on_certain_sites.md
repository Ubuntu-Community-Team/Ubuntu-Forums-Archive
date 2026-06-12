---
title: "browser keeps closing on certain sites"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by comradexiactura on 2006-11-18
hey all i just installed ubuntu and everything is running great. The only problem i have run in with so far is with the browser. For the most part it works fine but there are certain site that cause the browser to close. I installed all java add ons. I cant think of anything that might be causing my problem. Some of the sites are as, when i log into my myspace the page will begin to load and the the browser closes when it is almost through loading. also when i go to entensity.net it will work fine but when i click on a video it open a new window start to load the player on the page and then close before it visualizes. any suggestions at all would be very much appreciated. Thank you in advance

---

### Post by ewl1217 on 2006-11-18
I know nothing about that site, but it might just not play well with Firefox. I know it may not be the best or only solution, but, if you don't mind, you could try using another web browser, such as Opera, Epiphany, Galeon, or Konqueror. Just to warn you though, Konqueror will drag in a load of KDE dependencies (if you don't already have them installed) and Opera is closed source (but available for free).

---

### Post by 56phil on 2006-11-18
I just tried entensity.net on Opera and it says you need windows media player. Sorry. I don't know else to say.

---

### Post by comradexiactura on 2006-11-18
i tryed 2 of the browsers you recommended and the same thing happens. they crash when i go to these certain sites.

---

### Post by ewl1217 on 2006-11-18
Okay, that explains it. You probably need to install the w32codecs package so you can play Windows Media files. Try following [this guide]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

**WARNING:** Depending on where you live, this may be illegal.

---

### Post by AndyCooll on 2006-11-18
Surprising as it may seem the fault is probably related to your xorg.conf file. So try the following:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down and find the "DefaultDepth" for your "screen". Make sure it set to "24"

:cool:

---

### Post by comradexiactura on 2006-11-19
hey you guys are awesome i did both of the fixes suggested and after rebooting my pc firefox hasnt crashed and im able to log into the site now. thank you guys i really appreciate it!!:D

---

