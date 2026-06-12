---
title: "A few questions on Ubuntu - Drapper"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by davydany on 2006-11-17
hey guys
i got a few questions on Ubuntu - Drapper. I installed a few things and I am completely confused now. 

1. I installed wine and I wanted to run iTunes 7, because i need to reinstall the firmware on my iPod. well, it installed it but i don't know where it installed it to. i tried: "wine "C:\\Program Files\\iTunes\\iTunes.exe"" well, it said wine cannot find this application.

My Question is this: How do I access the applications I installed or atleast know where they are installed?

2. I installed things from Synaptic Package Manager and I can't see it in the Applications Menu. I can access it through the Deskbar (which I added to the panel)

is there a way to see this on the Applications menu?

I did install the _Debian Menu_ from Automatix2. I heard if I have this, both my problems would be solved but it doesn't seem to have been solved. 

can some one please help me out? i searched this forum but couldn't find the help I needed.

---

### Post by bruenig on 2006-11-17
to try to find your itunes, go into the home folder with nautilus press ctrl + h and then go into the directory called .wine, then go into drive_c and start looking.

Also if you are trying to run something with wine, assuming it was the same path that you were using it would be
```
wine "/home/USERNAME/.wine/drive_c/Program Files/iTunes/iTunes.exe"

```
Or something similar not too sure about those spaces but the quotes should do it. That is assuming of course that itunes is located there, it may not be. You need to find it.

As for the apps you can't see, which ones are you talking about. Some apps are command line only and so a menu entry is kind of unnecessary.

---

