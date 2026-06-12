---
title: "Tutorial : FreeBSD GNOME Installation."
date: 2012-10-05
forum: Any Other OS
---

### Post by Haghiri75 on 2012-10-05
Hi all. 

if u installed FreeBSD on your laptop or your Desktop system , you need a graphical environment :D . 
In this tutorial I want to say how to install gnome on FreeBSD. 

I use FreeBSD 9.0 . 

1st , We need Internet connection :)
2nd We're going to install packages :
A)X.org
```
pkg_add -r xorg
```
B) GNOME
```
pkg_add -r gnome-session
```
C)GDM 
```
pkg_add -r gdm
```

Optional :

D) Firefox :
```
pkg_add -r firefox
```

E) sudo 
```
pkg_add -r sudo
```

F)Nano
```
pkg_add -r nano
```

G)wget
```
pkg_add -r wget
```

Ok. now we have a FreeBSD with our installed packages. Now you should reboot the system by:

```
reboot
```

Ok. when system booted , you should login to your account (root or non-root). 

and run this command (Advanced) :

```
vi /etc/rc.conf
```

or (Beginner):

```
nano /etc/rc.conf
```

and add these lines to this file :

```

gnome_enable="YES"
gdm_enable="YES"
hald_enable="YES"
dbus_enable="YES"

```

If you want load KLD(s) at startup (Like linux kld) you should add this line (for example i want linux kld) :

```
linux_load="YES"
```

now you must save and exit this file. and do other optional configurations on your FreeBSD. 
then reboot your system and Enjoy the graphical FreeBSD :)

---

### Post by Haghiri75 on 2012-10-05
If you downloaded the 4GB ISO , you can install packages offline :)

---

### Post by Majorix on 2012-10-05
I don't get why you have to first reboot to edit rc.conf. You can edit it right ahead and THEN reboot.

---

### Post by Haghiri75 on 2012-10-06
> **Majorix said:**
> I don't get why you have to first reboot to edit rc.conf. You can edit it right ahead and THEN reboot.
Yes. You can edit rc.conf then reboot. 
Also if you want a GNOME FreeBSD Distro , Try GhostBSD ---> [http://ghostbsd.org](http://ghostbsd.org)

---

