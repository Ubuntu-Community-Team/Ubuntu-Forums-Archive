---
title: "Gdk-WARNING **: locale not supported by Xlib"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by geck07 on 2007-02-18
when i run :

sudo gedit /etc/apt/apt.conf

i get the error message:
[B]
(gedit:9753): Gdk-WARNING **: locale not supported by Xlib

(gedit:9753): Gdk-WARNING **: cannot set locale modifiers
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@gecko:/home/saumya# gedit /etc/apt/apt.conf

(gedit:9771): Gdk-WARNING **: locale not supported by Xlib

(gedit:9771): Gdk-WARNING **: cannot set locale modifiers
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

[/B]
kindly help!
Thanks in advance.

---

### Post by g3k0 on 2007-02-18
Does this work when you are not on root?

---

### Post by geck07 on 2007-02-18
yes it does...but i still get the warning:

[B](gedit:11496): Gdk-WARNING **: locale not supported by Xlib

(gedit:11496): Gdk-WARNING **: cannot set locale modifiers
[/B]

---

### Post by g3k0 on 2007-02-18
Well the error was caused by running it in root.  It has something to do with the X server not sure exactly whats going on though.  The warning seems to be some type of language setting.

I found this line in another thread not sure if it will help
sudo aptitude install language-support-en

---

