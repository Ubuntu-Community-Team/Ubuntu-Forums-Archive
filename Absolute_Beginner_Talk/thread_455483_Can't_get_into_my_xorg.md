---
title: "Can't get into my xorg??"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-05-26
andrew@andrew-desktop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
andrew@andrew-desktop:~$ sudo /etc/X11/xorg.conf
sudo: /etc/X11/xorg.conf: command not found
andrew@andrew-desktop:~$ 

what am i forgetting?

---

### Post by taurus on 2007-05-26
```
gksudo gedit /etc/X11/xorg.conf
```
or
```
sudo nano -Bw /etc/X11/xorg.conf
```

---

### Post by azizzle on 2007-05-26
thanks, is there a thread that lists all of the basic commands somewhere?

---

### Post by Ek0nomik on 2007-05-26
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

cd - change directories
ls - list files/directories
mv - move file
mkdir - make directory

some of the basics.

---

