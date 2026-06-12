---
title: "Installed  3d  chess but can't find it?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-22
I  installed 3d chess  from  "Add/Remove  Program" but  can't find it anywhere.  It's  not listed under  Games.    In Synaptic Package  Manager it shows it  green.  Thank  you

---

### Post by seshomaru samma on 2007-03-22
open a terminal and put the name of the programme as it appears in synaptic probably:
```
3dchess
```

you can create a desktop launcher by right-clicking anywhere on the desktop

---

### Post by adam.tropics on 2007-03-22
..or cheat and extract, and then copy the attached file to /usr/share/applications with (assuming you are in the directory you save it to)

```
sudo cp 3D\ Chess.desktop /usr/share/applications/
``` then restart your panel with

```
killall gnome-panel
```and it will be in your games menu.

edit: Failing all that the command is 3Dc

---

### Post by jtx472 on 2007-03-22
Tried that and  got:

jtx472@Northgate:~$ sudo  cp 3D\ Chess.desktop /usr/share/applications
cp: cannot stat `3D Chess.desktop': No such file or directory
jtx472@Northgate:~$

---

### Post by adam.tropics on 2007-03-22
You weren't in the folder where you extracted the file then! (Just right click it and extract here, then in the terminal cd to that directory, then the command)

---

### Post by Stickymaddness on 2007-04-03
Type 

```

3Dc

```

In the application launcher (ALT-F2)  and hit enter. Alternatively type 3Dc in a terminal. Of course the first is easier :P

*Don't forget linux case sensitivity! *

---

