---
title: "Installing Wine"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-02-20
Hi all:
I've tried to install wine through the add remove programs function, but nothing seemed to happen.  There must be more to it.

Anyone care to provide a beginner with some instructions?

Thanks,
Ziffnabb

---

### Post by Motoxrdude on 2007-02-20
```
sudo apt-get install wine
```
```
winecfg
```
Now just run those exe from the terminal
```
cd /where exe is
wine x.exe
```
just replace x with the name of the program.

---

### Post by Maestro23 on 2007-02-20
A site that can help you also:  [http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by Patrick K on 2007-02-20
Try typing in a terminal "winecfg". If wine is installed you'll see the configuration applet. Type winefile for wine's file manager. There is no real interface for wine. It's more like a shell for windows apps to run in. 

There is a man page, type "man wine". 

If none of this works, wine didn't install and you should give it another try.

---

### Post by ziffnabb on 2007-02-21
I did it!  It actually works!  And the application runs!  Bonus!!

Thanks to all that replied.

That windows  drive's gonna get formatted faster than I thought!

Ziffnabb

---

