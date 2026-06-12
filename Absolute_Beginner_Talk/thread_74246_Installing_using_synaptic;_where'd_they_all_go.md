---
title: "Installing using synaptic; where'd they all go?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2005-10-11
Hey, I've gone through synaptic and found some really neat stuff to junk up my computer with, and installed them all, and when I go looking for them, they aren't in the apps menu. Well, some are, like audio players, but other stuff just doesn't show up. Like some games and all. Is this because they can only be started from the command line?

---

### Post by Manny C on 2005-10-11
If you are using Gnome:
```
killall gnome-panel
```
If you are using KDE: Log out and then back in. 

Anyone with better suggestions?

---

### Post by rmjokers on 2005-10-11
It is possible that the app maker didnt bother to take the necessary steps to put an icon in the menu (I dont think synaptic does this automatically).  This is especially true if you are installing an app from the universe or multiverse repositories.  These are not officially supported by Ubuntu.

---

### Post by Kyral on 2005-10-11
Commandline time

```
sudo apt-get install menus
```

This snags the so called Debian Menu, which is a catchall for programs.

Once its installed do

```
update-menus && killall gnome-panel
```

---

### Post by Wolki on 2005-10-11
[QUOTE=rmjokers]It is possible that the app maker didnt bother to take the necessary steps to put an icon in the menu (I dont think synaptic does this automatically).  This is especially true if you are installing an app from the universe or multiverse repositories.  These are not officially supported by Ubuntu.[/QUOTE]

This is supposed to be fixed in Breezy, If you find a (appropriate) application that does not include a Menu entry there, please file a bug. Does not apply to cli tools, of course.

Synaptic will tell you on a right click which files were installed by a certain package. Look for the file it placed into "/usr/bin", this is the executable. Try running it from a command line. If it works, add a starter to your panel or edit the menus with smeg.

---

