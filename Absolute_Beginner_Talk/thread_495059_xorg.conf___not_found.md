---
title: "xorg.conf   not found"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Darkcloud on 2007-07-07
This is the response I get when I try to bring up this file

lauri@lauri-laptop:~$ sudo cp/etc/X11/xorg.conf/etc/X11/xorg.conf_backup
Password:
sudo: cp/etc/X11/xorg.conf/etc/X11/xorg.conf_backup: command not found
lauri@lauri-laptop:~$ sudo gedit/etc/X11/xorg.conf
sudo: gedit/etc/X11/xorg.conf: command not found
lauri@lauri-laptop:~$ 

Help please

---

### Post by taurus on 2007-07-07
You need some empty spaces in there.

```
sudo  cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup
gksudo  gedit  /etc/X11/xorg.conf
```

---

### Post by Alterax on 2007-07-07
put a space after gedit and before /etc/X11/xorg.conf

It looks like they are all linked as one word, but /etc/X11/xorg.conf isn't part of the command, it's the destination.  Hence the error that the command was not found.

--Alterax

---

### Post by Darkcloud on 2007-07-07
oh wow  Thank you  that made all the difference   It works now

---

