---
title: "wine"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by james1978 on 2007-06-19
I installed wine  just to guide me through a few installations but i want to use it to open and install a game demo from a cd  but when i right click on the demo wine doesnt seem to be in the list.. any ideas anyone ?

---

### Post by cogadh on 2007-06-19
Open a terminal and type"
```
wine /media/cdrom0/install.exe
```
Change the path and executable name as needed.

---

### Post by buzzmandt on 2007-06-19
If your wine is sintalled correctly

right click on the file, choose open with, in the box just type in "wine" without the quotes and it will go.

if it don't go, use the run command to run winecfg to make sure it's installed and ready

---

### Post by cogadh on 2007-06-19
Using the right-click method will work fine, but I don't recommend it for Wine beginners. If you use the terminal method, any error messages or problems Wine encounters will be reported in the terminal, while they don't get seen at all using the right-click.

---

