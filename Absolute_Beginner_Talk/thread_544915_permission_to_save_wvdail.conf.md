---
title: "permission to save wvdail.conf"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Andranik on 2007-09-06
hey guys, I know this is probably a noob question but here it is,

how can I get permission to save the file" /etc/wvdial.conf." ?
when i try in text editor I get an error message saying.
"Could not save the file /etc/wvdail.conf. you do not have the permission necesary to save the file.


can anyone help me?

---

### Post by reckless2k2 on 2007-09-06
throw sudo in front of the edit command...ie sudo nano or gksudo gedit

---

### Post by Andranik on 2007-09-06
Is that with terminal?
do i have to cd to the file?

---

### Post by Seisen on 2007-09-06
Yes that is in the terminal. It would basically look like this

```
gksudo gedit /locationoffile/wvdial.conf
``` anytime you need super user rights for a graphical application use gksudo.

---

### Post by reckless2k2 on 2007-09-06
yeah you'll have to run it from the terminal but to get a GUI output you can use gksudo


gksudo gedit /etc/whateverthefileis

not sure what that file is so always copy it first to a backup just in case you blow something up. 

sudo cp /etc/thatfiles.conf /etc/thatfile.conf.bak

then do the edit

---

### Post by Andranik on 2007-09-06
thanks for the help guys.

---

