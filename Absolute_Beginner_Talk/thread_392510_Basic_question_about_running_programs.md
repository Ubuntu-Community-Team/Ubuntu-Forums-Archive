---
title: "Basic question about running programs"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bigdawg72987 on 2007-03-24
I am having a problem with finding programs after I install them.  Through the package manager I installed network-manager and the gnome frontend for network-manager, as well as wine.  They show up in the package manager as installed, but I don't know where to find them now or how to run them.  I assumed they would show up in one of the menu's but they aren't there.  This is a totally noob question but I would greatly appreciate the help.  I am trying to move completely to linux from windows and really know nothing about linux.:)

---

### Post by eljalill on 2007-03-24
For the Network Manager you need to run
nm-applet 
in a terminal, for it to show in this session.
Adn wine is more used as a way to invoke commands.
So you use it like
wine program.exe 
in a terminal. That way you open a program.
with 
winecfg
you open the wine settings.

---

### Post by annda on 2007-03-24
the network manager should be accessible as a panel applet - right-click on the panel, choose 'add to panel' and select what you want (i think it's mistakingly called network monitor).

wine is a command line thing, i suppose. so you will have to type things in the terminal or create lauchers with commands like for example:

wine /media/your_windows_drive/some_path_to_file

HINT: use the TAB key for autocompletion of paths and filenames.

---

### Post by zvacet on 2007-03-24
One more wayto access wine is
```
winefile
```
and go to C>program files>exe_of _your_choice>double click

---

