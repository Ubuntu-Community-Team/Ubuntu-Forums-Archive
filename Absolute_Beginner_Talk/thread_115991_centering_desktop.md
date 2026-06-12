---
title: "centering desktop?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by wwuster on 2006-01-11
I just installed 5.1 and did all of the updates. Mostly everything is fine, but my desktop is shifted to the right about 3/16". I have an nvidia graphics card.

How can I get the desktop to be centered?

thanks,
William

---

### Post by Leif on 2006-01-11
are you using the nvidia drivers ?

---

### Post by Gimbo on 2006-01-11
I've no idea if this will work, but if your monitor has an "auto adjust" setting (or something similar), that might help. I find that changing my screen resolution sometimes moves the display off centre, and a quick auto adjust on the monitor clears things up.

---

### Post by wwuster on 2006-01-11
[QUOTE=Leif]are you using the nvidia drivers ?[/QUOTE]

I'm not sure. My /etc/X11/xorg.conf says that the driver is "nv"

Does that mean I'm using it?

William

---

### Post by Leif on 2006-01-11
no, nv is the opensource alternative to the nvidia drivers, and it ends up a bit to the right with me as well. try these instructions : [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=wwuster]I'm not sure. My /etc/X11/xorg.conf says that the driver is "nv"

Does that mean I'm using it?

William[/QUOTE]

Thats means the Nvidia drivers are not installed. When they are, you problem will be fixed.

Easiest way to do it is to use Automatix:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by wwuster on 2006-01-12
[QUOTE=Leif]no, nv is the opensource alternative to the nvidia drivers, and it ends up a bit to the right with me as well. try these instructions : [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)[/QUOTE]

Thank you. That worked. My screen is centered now.

William

---

### Post by Leif on 2006-01-12
that's great. but do keep automatix, which poofy suggested, in mind for other things. it could save you a lot of time.

---

