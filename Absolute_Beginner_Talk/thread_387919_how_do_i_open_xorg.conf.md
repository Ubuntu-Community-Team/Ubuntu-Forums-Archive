---
title: "how do i open xorg.conf"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-03-18
how do i open xorg.conf so that i can save it after making changes?

---

### Post by scxtt on 2007-03-18
in "X":

Gnome: gksu gedit /etc/X11/xorg.conf
KDE: kdesu kate /etc/X11/xorg.conf

in CLI:

sudo nano /etc/X11/xorg.conf
(follow the key commands at the bottom for how to save and then exit, ctrl+o should write and ctrl+x should exit)

enter YOUR user password in both cases ... :)

---

### Post by 23meg on 2007-03-18
Use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If using GNOME, 

```
gksudo gedit /etc/X11/xorg.conf
```

If using KDE,

```
kdesu kate /etc/X11/xorg.conf
```

In a terminal,

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by familyjules74123 on 2007-03-18
thank you for the speedy reply guys, installing beryl but needed to fix some settings and I am a little new so didnt know how to open it as a savable file.  thanks again

---

