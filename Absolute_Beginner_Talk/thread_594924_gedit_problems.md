---
title: "gedit problems"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Mindrift on 2007-10-28
*noobie question*  This shouldn't be too difficult, but that's why it's buggin' me.  I'm tryin' to change the picture on the ubuntu_theme.desktop screensaver.  Started off by going to the directory (cd /usr/share/applications/screensavers) in terminal.  Switch to root (su -) then make a copy of the file (cp ubuntu_theme.desktop mynewfile.desktop).  Problem is, whenever I try to use gedit to change the file it tells me "cannot open display:".  I'm in root, so what gives.  I even tried to change the access (chmod 770 mynewfile.desktop).  Didn't get an error, but still won't let me gedit the thing.  Any ideas??

---

### Post by Celegorm on 2007-10-28
Maybe try 'gksu gedit' instead of using gedit while in 'su'.

---

### Post by taurus on 2007-10-28
Instead of "**su -**" to root (with root password), why don't you just use sudo/gksudo!

```
gksudo gedit mynewfile.desktop
```

---

### Post by Mindrift on 2007-10-28
gksudo worked. Thanks alot!! Just another thing they didn't teach us in class.

---

