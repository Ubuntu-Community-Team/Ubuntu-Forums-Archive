---
title: "Movie player bug"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-20
My Totem movies player crashes if I run it.Still not able to fix it.I have done al possible updates and upgrades.


vivin@vivin-desktop:~$ totem

(totem:11158): Gdk-WARNING **: locale not supported by Xlib

(totem:11158): Gdk-WARNING **: cannot set locale modifiers
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
vivin@vivin-desktop:~$

---

### Post by LookTJ on 2006-12-20
Install mplayer

```
sudo apt-get install mplayer
```

then use mplayer instead of totem

---

### Post by vivin_west on 2006-12-20
Totem will crash if I run it.But if I go to a particular file and right click and choose run with Totem then that file will play.I have installed Mplayer and Gxine.Both dont play .wmv files.I have installed w32codecs, but totem is the only player that plays it.

---

### Post by vivin_west on 2006-12-20
Come on anyone 
any suggestions? 

It is cumbersome to go searching for a file and play it.

---

