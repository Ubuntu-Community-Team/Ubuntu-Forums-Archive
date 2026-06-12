---
title: "[SOLVED] deconstructing molecules"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by MelissaEpiphany on 2007-12-08
Can someone tell me some very simple commands I can use to get rid of the 'constructing molecules' screensaver from Gutsy? It constantly freezes my computer up. All other ones seem to work though. I have heard it has something to do with my graphics driver? But for now I just want to remove it.

Thanks, Mel

---

### Post by Dr Small on 2007-12-08
Just put it on a different screensaver and it won't freeze your system.

---

### Post by Arthur Archnix on 2007-12-08
Look in /usr/share/applications/screensavers/

---

### Post by MelissaEpiphany on 2007-12-09
Have been doing that Dr Small, but a few ppl use my computer, including kids, someone other than myself might mess around and accidentally try and add the screensaver - can't afford that mistake cause I have to install Gusty all over again every time - pain in the proverbial.

Looked in /usr/share/applications/screensavers/ but can't delete file from there. Does anyone know the basic commands in a terminal? I read someone's commands to remove the same file from Fiesty, but it brings up a different screen saver for me.

---

### Post by philinux on 2007-12-09
Use ```
gksudo nautilus
``` - browse to that folder and delete what you dont want.

---

### Post by MelissaEpiphany on 2007-12-10
Thanks - perfect :)

---

