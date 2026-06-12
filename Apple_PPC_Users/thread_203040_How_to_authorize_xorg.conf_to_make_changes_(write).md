---
title: "How to authorize xorg.conf to make changes (write)???"
date: 2006-06-24
forum: Apple PPC Users
---

### Post by zachws on 2006-06-24
Hey
im trying to fix my mouse problem by editing some lines in xorg.conf in etc/x11

however, i make the changes but the text editor won't let me save as it is locked and i have no option to unlock it with my credentials.

---

### Post by Sye d'Burns on 2006-06-24
You need to use sudo to edit

gksudo gedit
sudo nano 
etc

---

### Post by zachws on 2006-06-24
[QUOTE=Sye d'Burns]You need to use sudo to edit

gksudo gedit
sudo nano 
etc[/QUOTE]

hey i really appreciate the quick response. i assume i do this in terminal? k, i typed in 'gksudo gedit' ... it asked for my password, i put it in and it was rejected and g edit opened in a blank document. ai ya yai.

what am i missing?

---

### Post by aysiu on 2006-06-24
```
gksudo gedit
``` will open a blank Gedit document.
```
gksudo gedit /etc/X11/xorg.conf
``` will open the xorg.conf file with Gedit with root privileges.

Of course, you'd always do this first, though: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_backupincaseiscrewthingsup.org
```

---

### Post by zachws on 2006-06-24
thanks a lot asiu. my mouse is now working. not greatly but much more conveniently.

---

