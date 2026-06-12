---
title: "Ubunut10.10 on 500mhz mac G3 laptop"
date: 2011-05-13
forum: Apple Hardware Users
---

### Post by moh2010 on 2011-05-13
Hi,
I am trying to install Ubuntu 10/10 on Mac PowerPC G3 laptop 500mhz with  320mb ram.I have downloded the ppc version but there is no xserver in  live cd.I google it and it seems it is a common problem.I try to fill in  empty xorg.conf from one post but it is not working ,please help.

 I tried to restart gnome but it is blank I have to alt-f1 to drop into shell.

Display Chipset Model is ATi,RageM3 and it is 8mb agp.

thanks

---

### Post by moh2010 on 2011-05-13
The following post on ubunut forum I tried to follow

[http://ubuntuforums.org/showthread.php?t=1306706](http://ubuntuforums.org/showthread.php?t=1306706)

[http://ubuntuforums.org/showthread.php?t=296870&page=2](http://ubuntuforums.org/showthread.php?t=296870&page=2)

---

### Post by linuxopjemac on 2011-05-14
Do you own a Pismo G3 ?

---

### Post by moh2010 on 2011-05-14
It says ibook on the laptop


In the OS it says

Processor 500Mhz PowerPc G3

Machine PowerBook 4.1

CPU  Type PowerPC 750 (22.15)

---

### Post by linuxopjemac on 2011-05-14
in a live session you have to get into a terminal:
CTRl-Alt-F1 for example
then do:
```
sudo passwd
```
give the temporary root password
this will be your temporary root password
then
```
wget http://mac.linux.be/files/xorg/ibook1.txt
sudo mv ibook1.txt /etc/X11/xorg.conf
```
then restart GDM:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```
you will get back into the X session with hopefully a correct GUI

---

