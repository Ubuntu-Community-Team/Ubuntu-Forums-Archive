---
title: "Gedit warning"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by kintsa on 2006-10-18
When I type in the terminal> sudo gedit I get the following message:
> (gedit:19380): Gdk-WARNING **: locale not supported by Xlib

(gedit:19380): Gdk-WARNING **: cannot set locale modifiers

Gedit opens without any problem but what is the meanning of the above???:-k

_Edit_ This is not just for gedit but for other programmes also..

---

### Post by CatKiller on 2006-10-18
You should use gksudo for graphical applications.

Of course, then you'll get a different error message, but one that is known to not be a problem.

---

### Post by Najand on 2006-10-18
It is ok... Just ignore them...
If you don't want any error, just send the error messages to /dev/null

---

### Post by taurus on 2006-10-18
Or use nano (or vim if you are up to it)!!!

---

### Post by kintsa on 2006-10-19
Using gksudo, I get this error

> (gksudo:5792): Gdk-WARNING **: locale not supported by Xlib

(gksudo:5792): Gdk-WARNING **: cannot set locale modifiers

(gedit:5793): Gdk-WARNING **: locale not supported by Xlib

(gedit:5793): Gdk-WARNING **: cannot set locale modifiers

(gedit:5793): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I understand that this error and the one posted earlier are harmless but are some how irritating me](*,) . Will try sending these error messages to /dev/null:-| ..

Used Nano and Vim.. Vim is not for me at all..:p

---

### Post by nyinge on 2006-10-19
How would I send those warning messages to /dev/null?
Like...
```

gksudo gedit > /dev/null

```
Like that?

---

