---
title: "installing wine"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-05-03
hello
 I've just installed the wine package using dpbi and can't find where it has installed. I've looked in places applications and system. Any place it would be?

---

### Post by Clay_Banger on 2007-05-03
as far as i know wine doesnt place itself in any menus. you use it via the terminal:
```
user@computer:~$ wine winprogram.exe
```it will then install it to /home/user/.wine/drive_c/Program Files/
you can then cd to the directory and wine it from there.

---

### Post by zvacet on 2007-05-04
First you have to configure wine.**programs>accessories>terminal**

```
winecfg
```

Open your home folder<view>show hidden files and there is .wine folder.

---

### Post by teddybairs1 on 2007-05-04
Easiest graphical way of using wine is by launching winefile. You can do this from the terminal, or you can set up a shortcut on the desktop. For command, just type "winefile". You can also use the Run Command tools as well. This will launch you into a windows like file manager where you can launch executables from. You can also add winefile to your menu as well if you don't like a lot of icons on the desktop.

---

