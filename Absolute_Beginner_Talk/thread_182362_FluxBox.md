---
title: "FluxBox"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by flaak_monkey on 2006-05-25
i want to install this. I also want to know though first, if i re-install Ubuntu in server mode, then apply this?

---

### Post by IYY on 2006-05-25
sudo apt-get install fluxbox. You don't have to re-install Ubuntu.

---

### Post by uzi09 on 2006-05-25
nope! no need to go into server mode. you should just be able to do:
```
 sudo apt-get install fluxbox 
```

then restart. when the login screen comes, on the bottom, look for sessions, select fluxbox and enjoy :D

---

### Post by Sef on 2006-05-25
Read the wiki first:

[Fluxbox]("https://wiki.ubuntu.com/Fluxbox")

then read this:

[FluxboxSource]("http://doc.gwos.org/index.php/FluxboxSource")

---

### Post by Personatech on 2006-05-27
For whatever reason, doing an apt install does not seem to correctly install fluxbox - it installs OK but doesn't configure menus so you can't really do anything.  I'm running Dapper RC.  This may be specific to my machine or my noobeness, but either way it's not a smooth install.  IceWM seems to install OK as does XFCE.

---

### Post by uzi09 on 2006-05-27
that's odd.

i've installed it on my last machine and it worked fine for me!

btw, try to use aptitude instead of apt-get -- aptitude seems to work a lot better.

---

### Post by Personatech on 2006-05-27
Just got it working - I actually RTFWiki (noted in an above post) and then configured my menu.  Neat.

---

### Post by Sef on 2006-05-27
> Just got it working - I actually RTFWiki (noted in an above post) and then configured my menu. Neat.

It does help to read them.  Have learned that lesson myself.

---

