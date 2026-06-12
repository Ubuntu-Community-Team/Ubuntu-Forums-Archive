---
title: "Kde/gnome Change?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-11-20
Greetings,

I am thinking about giving KDE  whirl but I am not too sure as to where to start, can I load KDE w/out destroying GNOME?  If I like KDE and want to keep it, will everything flow over and then can I remove GNOME?

Again just thinking about switching... thanks in advance...

---

### Post by ofek on 2005-11-20
Not sure about all your question (I only use gnome) but you can use both.
For installing kde on ubuntu you should type this in terminal:```
sudo apt-get install kubuntu-desktop
```
That will give you to gui options when you logon: gnome and kde.

---

### Post by matthewv on 2005-11-20
Easiest is to do a ```
sudo apt-get install kubuntu-desktop
```
This will install the full KDE suite, and keep gnome as well. You just select which to use at login time. Later you could always remove gnome.

---

### Post by Adrian on 2005-11-20
[QUOTE=garnertr]can I load KDE w/out destroying GNOME?[/QUOTE]

Your new KDE programs will show up in the Gnome menus. If you don't like this, check out the following HOWTO for a solution:
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

---

### Post by Kyral on 2005-11-20
And vice-versa. The various GUIs are all just different ways of accessing data :D

The one thing that WON'T carry over between KDE and GNOME are themes

---

### Post by flipkick on 2005-11-23
I've got a question concerning "gdm/kdm". I guess you'
d probably use kdm for the KDE DEsktop environment and gdm for GNOME, right ?

For some reason that i couldn't figure out, I suppose you either user kdm OR gdm. So by selecting the desktop environment before loggin in, you're not able to switch to it's comparable window manager.

If I choose gdm, the application windows look odd in KDE, do they ?
In GNOME everything will be fine.

Conclusion: I've to choose KDE or GDM and for the choice I made, the right window manager....

Please help me out with some input :rolleyes:

---

### Post by aysiu on 2005-11-23
KDM or GDM, as far as I can tell, just deals with logging in and logging out. You can use GDM and log into KDE or use KDM and log into Gnome.

---

