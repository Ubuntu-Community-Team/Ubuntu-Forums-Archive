---
title: "Problem when starting Automatix with terminal"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-03
I've just finished installing Automatix
I started it with Terminal and it just gave me these errors while auto script froze after entering the password:
```
isos@localhost:~$ Automatix

(zenity:9185): Gdk-WARNING **: locale not supported by Xlib

(zenity:9185): Gdk-WARNING **: cannot set locale modifiers

(zenity:9188): Gdk-WARNING **: locale not supported by Xlib

(zenity:9188): Gdk-WARNING **: cannot set locale modifiers
cat: /home/isos/automatix.log: No such file or directory

(zenity:9191): Gdk-WARNING **: locale not supported by Xlib

(zenity:9191): Gdk-WARNING **: cannot set locale modifiers
Warning: locale not supported by Xlib, locale set to C

```
What's the problem? any clues guys?

---

### Post by aktiwers on 2006-05-03
Have you tried with a small "A" in automatix?

EDIT: Oh sorry.. that should work anyways. I just made a mistake like that once.. Sorry dont know whats wrong here.

---

### Post by Isoss on 2006-05-03
np ... anyway .. it used to work before reinstalling ununtu ... does it have anything to do with the repositories?

---

### Post by Isoss on 2006-05-04
I dunno what's the problem ... it downloads and then is unable to install ... please help

---

### Post by mostwanted on 2006-05-04
try starting it with
```

LANGUAGE=en automatix
```

---

