---
title: "enlightement at the menu"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by ensenadaubuntulover on 2005-05-30
I instaled desktop enlightenment but how do I run it? at the begining I only can choose kde fluxbox and failsafe at the icon at the bottom left, how can I add other windowmanagers? :roll:

---

### Post by jobezone on 2005-05-31
[QUOTE=ensenadaubuntulover]I instaled desktop enlightenment but how do I run it? at the begining I only can choose kde fluxbox and failsafe at the icon at the bottom left, how can I add other windowmanagers? :roll:[/QUOTE]
 One quick way for you to try enlightenment and learn some command line skills is to do this:

[list]
[*]Press the keys Ctrl+alt+F1
[*]Login with your username and password
[*]Edit the file .xsession by doing:
```

nano .xsession

```
[*]It will probably be empty, just insert this text:
```

exec enlightenment

```
[*]Close nano by pressing Ctrl+X, and pressing Y when asked if you want to save the file
[*]Now to run X with the windowmanager you've just set, type:
```

startx -- :1

```
[*]To return to GDM at any time, press Ctrl+alt+F7
[/list]
Print this message if you want to follow it carefully, while staying in the virtual terminal.

As for being able to choose enlightenment from GDM(login greeter) create a file called "enlightenment.desktop" and place this text inside it:
```

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Exec=/usr/bin/enlightenment

```

Now move or copy this file to /usr/share/xsessions/ :
```

sudo cp enlightenment.desktop /usr/share/xsessions/

```

---

