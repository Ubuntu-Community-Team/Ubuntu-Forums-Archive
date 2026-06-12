---
title: "Xorg Server Install in Gutsy Barebones"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-11-08
Alright, well, I installed Xorg on a Ubuntu Gutsy Server install. When I type sudo /etc/init.d/gdm start, it goes blank, goes to the text screen, goes blank again, and then stops trying all together. What's wrong with my Xserver?

---

### Post by Dr Small on 2007-11-08
```
xinit -- :0 vt7
```

---

### Post by kevCast on 2007-11-08
Didn't work.

---

### Post by Dr Small on 2007-11-08
Well, you wasn't very descriptive as to "What" didn't work.
Did it open an X display on vt7 or did it just output an error ?

---

### Post by kevCast on 2007-11-08
I'm sorry. It gave me an output error.

---

### Post by louieb on 2007-11-08
Did you install a WM too? or just xorg?
[Fluxbox - Ubuntu Documentation]("https://help.ubuntu.com/community/Fluxbox")
[HOWTO: get a Fluxbox menu (and customization) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=371144")
[HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")
[Window Managers for X: Introduction]("http://xwinman.org/intro.php")

---

### Post by Dr Small on 2007-11-08
> **louieb said:**
> Did you install a WM too? or just xorg?
[Fluxbox - Ubuntu Documentation]("https://help.ubuntu.com/community/Fluxbox")
[HOWTO: get a Fluxbox menu (and customization) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=371144")
[HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")
[Window Managers for X: Introduction]("http://xwinman.org/intro.php")
You don't need a WM just to start an X session.
But of course, he would need one, once he has the X session started. Icewm works nice.

Dr Small

---

### Post by kevCast on 2007-11-08
I've got fluxbox installed. I just can't get X going.

---

### Post by Dr Small on 2007-11-08
Have you tried just:
```
xinit
```
or
```
startx
```

??

---

