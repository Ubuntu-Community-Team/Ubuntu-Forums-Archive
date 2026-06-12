---
title: "Aptitude update and upgrade only checks cdrom not internet"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-11-24
Im fully connected and online but whenever I run sudo apt-get update or upgrade it only checks the cdrom. This is the output I get when I run the command.

> Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


Im connected online right now through my Gutsy machine so im not sure if there are settings I need to change with aptitude in order for it to browse online packages. Please help.

If it helps im trying to install xorg-driver-fglrx and this is the output when I try the install from aptitude.

>  sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx


---

### Post by Partyboi2 on 2007-11-24
In gusty you can go to Software Sources under System>Admin and untick the cdrom box, can't remember if its the same for Feisty.
Or you can change it in your source.list
```
gksudo gedit /etc/apt/sources.list
```Where you see a line like this at the top:
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
Put a # in front of deb cdrom:, so that it will look like mine except yours will say feisty not gusty, save.
then:
```
sudo apt-get update
```

---

### Post by celticbhoy on 2007-11-24
You will also have to got into System-->Administration-->Software Sources, and mark all tabs under Downloadable from the internet.

---

### Post by devosion on 2007-11-24
I found the uncheck box. Im actually using Gutsy, just recently did a clean wipe and install. 

Aptitude no longer checks the cdrom but I still cant find and download xorg-driver-fglrx. Maybe its just down...

---

### Post by celticbhoy on 2007-11-24
Have you checked if what you are looking for is available under sysnaptic, if it is listed you should be able to download.

---

### Post by devosion on 2007-11-24
Thanks Celticbhoy and partyboi2 for all the help.

When I noticed I was checking proprietary drivers it just clicked and I realized I hadnt enabled this after my install. At least now I can see if I can get my ATI card to work now.

---

