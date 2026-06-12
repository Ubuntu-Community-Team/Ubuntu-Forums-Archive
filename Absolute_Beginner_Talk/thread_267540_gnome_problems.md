---
title: "gnome problems"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by dr1445 on 2006-09-28
greetings forum
new to gnome and having the some set up problems.
1. single click mouse, system>preferences>mouse no option for single click? is one available?
2. copy # gedit /etc/X11/xorgconf to the desktop. i highlight the file, click edit>copy,
right click on the desktop and no paste is available? i also made a desktop file called xorg and tried to edit>paste there, nothing?
3 i have google earth installed and look in /usr/ to drag a start icon to the desktop. everthing is ghosted, no click and drag.
please advise lost kde user
regards
dave

---

### Post by pstep9407 on 2006-09-28
#1 -- can't help there
#2 --the most cost-effective thing a user can do is to learn how to do things from the terminal.  

Open a terminal (that little black monitor image) and type:
```
cp /etc/X11/xorgconf ~/Desktop
```
Translation: copy [that] [there]

For #3, try right-clicking your desktop and look for the 'create launcher' dialog. To get a right-click with a one-button mouse, try various combinations of clicking + keystrokes, such as Control+click.

---

### Post by orb9220 on 2006-09-28
run in term
gksudo nautilus

Which will give you sudo nautilus for copying and deleting,etc

Drag a home folder or computer icon to panel and rightclick icon change command to gksudo nautilus.

Which will give you a superuser nautilus too.

When I installed google earth it put a icon in the menu under internet. Which you can drag to panel for icon.

Prefs in nautilus will allow you to set 1 click.

---

### Post by dr1445 on 2006-09-28
great, thanks!

---

