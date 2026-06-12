---
title: "Xubuntu xserver-xorg"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-13
Hi my question is that i choose the wrong option on the xserver-xorg.Is there anyway to change it after installation of xubuntu?

---

### Post by 1/0 on 2007-08-13
Yes, either by editing (via nano, gedit or whatever you use):

```
sudo nano /etc/X11/xorg.conf
```

or by:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by jambarama on 2007-08-13
> **Dionysus135 said:**
> Hi my question is that i choose the wrong option on the xserver-xorg.Is there anyway to change it after installation of xubuntu?

Absolutely.  Just go to a terminal (if Xorg is broken, press ctrl-alt-F1 and you'll be brought to tty1, which is a terminal) and type > sudo dpkg-reconfigure xserver-xorg.  That should let you reconfigure X.

---

### Post by Dionysus135 on 2007-08-14
> **1/0 said:**
> Yes, either by editing (via nano, gedit or whatever you use):

```
sudo nano /etc/X11/xorg.conf
```

or by:

```
dpkg-reconfigure xserver-xorg
```

where do i edit it using the code sudo nano /etc/x11/xorg.conf

---

