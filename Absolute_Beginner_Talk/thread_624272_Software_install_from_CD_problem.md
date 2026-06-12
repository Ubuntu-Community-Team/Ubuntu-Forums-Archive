---
title: "Software install from CD problem"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by foundryman on 2007-11-26
I tried to install a French language program, Talk Now Instant Immersion French v2.0. the exe will not operate, nor will it install. Message read "no application available to...". What do I need to do to enable Linux Ubuntu to run this program?

---

### Post by bluepowder7 on 2007-11-26
Linux != Windows

you need to either get a linux version of that program, or install it under windows like it was designed to be, or install a windows emulator of sorts and then install your program

---

### Post by master_kernel on 2007-11-26
You have to install WINE, the Windows emulator for Linux. It probably won't work, but you can try it. *.exe are files limited to Windows operating systems. The EXE stands for executable. Normally these cannot be run under Linux without an emulator. You can install WINE in Ubuntu from a terminal using
```
sudo apt-get install wine
```
and run the following to configure it
```
winecfg
```

WineHQ: [http://www.winehq.org/](http://www.winehq.org/)

You can also try the AppDB to see if somebody using your program has tried it with WINE: [http://appdb.winehq.org/](http://appdb.winehq.org/)


Good Luck!
master_kernel

---

