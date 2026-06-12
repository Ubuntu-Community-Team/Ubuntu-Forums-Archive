---
title: "Strange error"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by champ_rock on 2006-07-07
hi whenevr i try to open gedit or xmms, (i know only these 2 right now :) ) then this error comes.. 
> root@ubuntu:/home/ubuntu/Desktop# gedit menu.lst~

(gedit:10456): Gdk-WARNING **: locale not supported by Xlib

(gedit:10456): Gdk-WARNING **: cannot set locale modifiers

(gedit:10456): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


i mean they work fine.. gedit opens up fine.. xmms plays songs fine.. then i cant understand whats this error for...

---

### Post by richbarna on 2006-07-07
> **champ_rock said:**
> hi whenevr i try to open gedit or xmms, (i know only these 2 right now :) ) then this error comes.. 


i mean they work fine.. gedit opens up fine.. xmms plays songs fine.. then i cant understand whats this error for...

You should use gksudo with gedit, other graphical programs.
Some people post telling you to us sudo but this can damage your operating system, maybe even leading to not being able to log in.

NOTE: Even using gksudo will produce an error message, but this is just a bug, don't worry about it.

---

### Post by 3rdalbum on 2006-07-07
It happens with a lot of Gnome programs when you launch them from the terminal. I don't know what it means, but it happens to everyone and it doesn't affect their performance.

Using sudo to launch a graphical program from the terminal doesn't do any damage. You only need to use gksudo when not launching programs from the terminal.

---

