---
title: "Help Required"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by pulldogg on 2007-04-21
mhatre@mhatre:~$ sudo /etc/resolv.conf
Password:
sudo: /etc/resolv.conf: command not found
mhatre@mhatre:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
mhatre@mhatre:~$

Y is this happening,also i have to manually add dns servers everytime i start up to get the net going,my repositores do not seem to be working,im very new using 6.06  win xp 1.9 ghz 1 gb ram,180 gb hdd pls help

---

### Post by ffxr on 2007-04-21
sudo gedit /etc/resolv.conf

then add your DNS servers to that file.. and then you wont have to add your DNS servers everytime (fingers crossed)

add these 2 free & very fast DNS servers:

nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by wormser on 2007-04-21
/etc/resolv.conf is a configuration file.  If you just want to view it you can use less /etc/resolv.conf.  You have to use a text editor to make changes.  To edit it you need root privileges:  sudo nano /etc/resolv.conf.

---

### Post by pulldogg on 2007-04-21
mhatre@mhatre:~$ sudo gedit /etc/resolv.conf
Password:

(gedit:5620): Gdk-WARNING **: locale not supported by Xlib

(gedit:5620): Gdk-WARNING **: cannot set locale modifiers
mhatre@mhatre:~$


is this mssg normal,also i added the nameservers in resolv.conf yet every time i come on i have to go to system>administration>networking and then add dns servers there manually

---

