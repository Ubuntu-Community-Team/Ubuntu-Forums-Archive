---
title: "xclient script"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by hairyharry7 on 2008-03-08
when i login under the "run Xclient script" session i was wondering where to find the XClient Script...I noticed in [this]("http://ubuntuforums.org/showthread.php?t=683526") thread that the user had to create one, which is fine...but i was reading [this]("http://ubuntuforums.org/showthread.php?t=452231") thread and apparently you can change the default session in the "run Xclient script" session from gnome to something else, which is ultimately what i want to do...does anyone know how to do this? thanks

-HH

---

### Post by hairyharry7 on 2008-04-14
i got this working a while ago in case anybody is interested...to run programs at start-up:
in your home directory (~/user) make a file called .xsession and login under the "run XClient script"-this will execute the .xsession file at login...here's what mine looks like:
```
#!/bin/sh
#
#~/.xsession

#Any programs you want to run go here...
#Desktop sessions can also be started (in this case xfce)

xterm -geometry 80x30+750+0 &

xfce4-session
#gnome-session
.xsession (END) 

```

---

