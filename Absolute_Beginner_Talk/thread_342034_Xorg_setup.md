---
title: "Xorg setup"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by hanexar on 2007-01-19
Hi, 
  I remember using a setup program for the xorg.conf file some time ago, but I can't find out what the command line was :confused: ... Could someone refresh my mind, I'd appreciate.

Thanx

---

### Post by reverseninja on 2007-01-19
```
sudo dpkg-reconfigure xserver-xorg
```  should help

---

### Post by mand0 on 2007-01-19
Do you mean this?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by devils_casper on 2007-01-19
```

sudo dpkg-reconfigure xserver-xorg
```



EDIT: WOW ! same time.. i think milliseconds... :)




Casper

---

### Post by taurus on 2007-01-19
```
sudo dpkg-reconfigure xserver-xorg
-or-
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by SMS on 2007-01-19
what this one
 sudo dpkg-reconfigure -phigh xserver-xorg
or the word proccessor one
sudo gedit /etc/X11/xorg.conf

---

### Post by hanexar on 2007-01-19
That's the one:

```
sudo dpkg-reconfigure xserver-xorg
```

Thanx for being so fast! :cool:

---

### Post by reverseninja on 2007-01-19
:mrgreen:

---

