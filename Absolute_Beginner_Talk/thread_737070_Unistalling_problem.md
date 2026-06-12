---
title: "Unistalling problem"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2008-03-27
Hello there i'm trying to unistall a game named coldwar_demo...
```
chemical@chemical:~/coldwar_demo$ sudo ./uninstall
**Could not open product information for -L**
chemical@chemical:~/coldwar_demo$

```
and i get the bold line error what can i do?
above it's directory(the install was for source file)
```
chemical@chemical:~/coldwar_demo$ ls
bin  coldwar_demo  coldwar.xpm  config  data  icon.xpm  lib  README  README.licenses  uninstall

```
thanks in advance

---

### Post by Oldsoldier2003 on 2008-03-27
> **chemicalgr said:**
> Hello there i'm trying to unistall a game named coldwar_demo...
```
chemical@chemical:~/coldwar_demo$ sudo ./uninstall
**Could not open product information for -L**
chemical@chemical:~/coldwar_demo$

```
and i get the bold line error what can i do?
above it's directory(the install was for source file)
```
chemical@chemical:~/coldwar_demo$ ls
bin  coldwar_demo  coldwar.xpm  config  data  icon.xpm  lib  README  README.licenses  uninstall

```
thanks in advance

did you:
1) complie the game from source
2)install it using a script
3)install the game using a package manager

If you compiled the game you can usually "make uninstall" or if you compiled and used checkinstall you can use dpkg -r or apt-get remove

---

### Post by chemicalgr on 2008-03-27
here is the directoru from which i've installed the game this will definetelly gives the right answer
> chemical@chemical:~/Games/ColdWar$ ls
coldwar-demo.run  screenshot.jpg  screenshot_thumb.jpg


---

