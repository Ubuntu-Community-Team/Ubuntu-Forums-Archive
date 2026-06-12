---
title: "an error occured during update installation"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-28
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

is what i get when i try to install updates with the update manager. i tried out the code that it gave me in the terminal it told me that i needed superuser privileges

---

### Post by kellemes on 2008-03-28
> **daberger said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

is what i get when i try to install updates with the update manager. i tried out the code that it gave me in the terminal it told me that i needed superuser privileges

```
sudo dpkg --configure -a
```

[sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Inxsible on 2008-03-28
in the terminal, run that code again. this time put a sudo in front of it, like so
```
sudo dpkg --configure -a
```

---

### Post by daberger on 2008-03-28
it asks me for my password but my keyboard locks up

---

### Post by Inxsible on 2008-03-28
> **daberger said:**
> it asks me for my password but my keyboard locks up
No it does not. It won't show any *'s or .'s but it is taking in the password.
Simply type it in and hit enter

---

### Post by daberger on 2008-03-28
never mind i think its working

---

### Post by daberger on 2008-03-28
andrew@andrew-laptop:~$ sudo dpkg --configure -a
[sudo] password for andrew: 
Setting up libexempi3 (1.99.9-1) ...

Setting up libgvfscommon0 (0.2.2-0ubuntu1) ...

Setting up jockey-common (0.3.3-0ubuntu1) ...







































Setting up lsb-release (3.2-4ubuntu1) ...

Setting up libnm-util0 (0.6.6-0ubuntu4) ...

Setting up bluez-gnome (0.25-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/bluetooth-applet.desktop ...

Setting up gnome-media-common (2.22.0-0ubuntu2) ...

Setting up pidgin-data (1:2.4.0-1ubuntu1) ...

Setting up libpulsecore5 (0.9.9-1ubuntu4) ...

Setting up libsmbclient (3.0.28a-1ubuntu3) ...

Setting up libbluetooth2 (3.29-0ubuntu1) ...

Setting up mysql-common (5.0.51a-3ubuntu5) ...
Setting up libpulse0 (0.9.9-1ubuntu4) ...

Setting up jockey-gtk (0.3.3-0ubuntu1) ...
Setting up gvfs (0.2.2-0ubuntu1) ...

Setting up libpulse-browse0 (0.9.9-1ubuntu4) ...

Setting up libgnomeui-common (2.22.01-0ubuntu2) ...
Setting up gnome-desktop-data (1:2.22.0-0ubuntu3) ...
Setting up libnm-glib0 (0.6.6-0ubuntu4) ...

Setting up libwnck-common (2.22.0-0ubuntu2) ...
Setting up ubuntu-docs (8.03.4) ...

---

