---
title: "XScreenSaver and Number lock"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by zeeone01 on 2006-02-19
Hoary on an HP a610n
Being a very long time KDE user, Gnome and I are having heartburn about two things.

1.  Auto start XScreenSaver at login.

2.  Number Lock on at login.

Can someone be so kind as to point me in the right direction to fix these two things, so that Gnome and I will quit yelling at each other. :???:

---

### Post by Mustard on 2006-02-19
Number lock I believe is..

```
sudo apt-get install numlockx
```

I'm not sure what you mean by autostart X screensaver.  As far as I know its on by default in gnome.  It should be under System>>Preferences>>Screensaver.

---

### Post by zeeone01 on 2006-02-20
couldn't find package numlockx. :???: 

Auto start XScreenSaver, turn on machine, login, machine sits idle for what ever time, XSceenSaver starts without going to System>Preferences>Screensaver to start it. :neutral:

---

### Post by Mustard on 2006-02-20
[QUOTE=zeeone01]couldn't find package numlockx. :???: 

Auto start XScreenSaver, turn on machine, login, machine sits idle for what ever time, XSceenSaver starts without going to System>Preferences>Screensaver to start it. :neutral:[/QUOTE]

numlockx is in the universe repository, so you need to enable the universe and multiverse repositories.

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

As I said earlier, xscreensaver is normally enabled by default.  I don't know why it wouldn't be setup to run by default on your system.

---

