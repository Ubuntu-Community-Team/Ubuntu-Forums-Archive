---
title: "whats the command to load the cd"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by hitspace on 2008-02-01
ive been trying to load a game i had . its a windows based code but im pretty sure wine could run it .l only problem is that i dont know the code to load  the cd's autorun . help

---

### Post by mbrush on 2008-02-01
autorun is just an info file that points to a program

open up the autorun file in a text editor to see what it's pointing to and just manually run that program/file.

Good Luck

---

### Post by bluewraith on 2008-02-01
I don't believe autorun is supported under linux as all, but if you go into the CD and launch "setup.exe" or "install.exe" or whatever the program uses to install the game, WINE should pick it up and install.

Do you already have WINE installed?

---

### Post by Christmas on 2008-02-02
Go to where your CD was mounted (probably /media/cdrom0) and run 'wine setup.exe' or 'wine install.exe' or 'wine autoexec.exe', whichever is there. The installer should start.

---

