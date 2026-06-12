---
title: "I can't get anything to work...worked before..."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-02-05
I just switched back to Ubuntu (fluxbox) from WinXP.  And I can't get anything to work.  The last time I was using fluxbox, everything worked perfectly...Now I'm getting tons of apt-get errors, gnome just deleted itself, etc...What should I do, just do a clean Ubuntu install and start over or what?:mad: :mad: :mad: :mad:

---

### Post by taurus on 2007-02-05
From a terminal, run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by zetsumei on 2007-02-05
if you dont mind me asking what does this do exactly...im trying to learn about ubuntu...

EDIT: ok i ran those commands and it just installed a bunch of stuff, but when I try to use default session in the options menu on the login screen it just hangs at a brown screen

---

### Post by zetsumei on 2007-02-05
no one can help me?

---

### Post by Happy_Man on 2007-02-05
what those commands do is install the default ubuntu settings, i.e. what you'd get with a clean install. As for your login problem, try manually specifying GNOME in the Sessions menu on login and see if that works.

---

### Post by zetsumei on 2007-02-05
how would i manually specify GNOME in the sessions menu?

---

### Post by Happy_Man on 2007-02-05
It'll give you a list, in the sessions menu on login. One fo those choices will literally say "GNOME". Highlight that, click OK, and log in as normal.

---

### Post by Zuuswa on 2007-02-05
Try hitting F10 in the login screen.  It will bring up a menu, from which you can click on sessions -> gnome

---

### Post by zetsumei on 2007-02-05
the only thing that says gnome is Failsafe Gnome and when I selected that it put me in the failsafe terminal b/c it couldn't load the gnome one...

what I don't get is it was working before I installed fluxbox, now its not...

---

