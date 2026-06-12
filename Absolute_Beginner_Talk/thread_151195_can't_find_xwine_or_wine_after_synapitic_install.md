---
title: "can't find xwine or wine after synapitic install"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-27
I hate microshaft however just out of sheer tinkering I wanted to try wine o xwine...After install I can't find it on my system. It does'nt show up on applications,places or system. What am I missing?

---

### Post by noswal on 2006-03-27
Mine is here:
~$ locate winefile
/usr/bin/winefile
/usr/lib/wine/winefile.exe.so

---

### Post by akiro.yamamoto on 2006-03-27
Wine enables you to run windblowz apps/games so after the wine install just double click on the windows app to install / run the prog.
Ususally the  M$ apps are installed to  /home/$USER/.wine/drive_c/Program Files directory.
Wine will not work with every M$ app or game so visit winehq and search their app database for any specific install instructions for the prog you want to install.
To configure wine use either the Run dialog or terminal and:
```
 winecfg 
```
To start the wine configuration utility.

Hope this info helps ;)

---

### Post by wolfee on 2006-03-27
Thanx I just relized it doesent "show up" till I try to install or run a microshaft program Duhhhhhh!!!! You Rock Akiro!!!

---

