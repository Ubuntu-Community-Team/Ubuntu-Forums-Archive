---
title: "Xorg restore after ATI driver"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by benevolent on 2007-10-07
hi there....


I try to install ATI drivers from [www.ati.com](www.ati.com) but something went wrong (or maybe the driver is not supported from 7.04???) and i need to restore the Xorg.conf


1. what am i suppose to do?????


2. how can i enable 3d acceleration?????


I have ati x1650pro chipset


thx in advance

---

### Post by Irony on 2007-10-07
The open source driver is installed by default on installing 7.04 - if you want to install the closed source driver then go;

System > Admin > Restricted Drivers Manager

And thats it.

---

### Post by benevolent on 2007-10-07
hm... i forgot to mention that i cannot run the X, only command line......

---

### Post by Irony on 2007-10-08
The command is 

[PHP]sudo dpkg-reconfigure xserver-xorg[/PHP]

Full instructions at;

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Note that you can also use your live CD to access/alter files on the installed system.

---

### Post by benevolent on 2007-10-08
Irony, take a look at that please [http://ubuntuforums.org/showthread.php?p=3497204#post3497204](http://ubuntuforums.org/showthread.php?p=3497204#post3497204)


somehow i messed things up :/

---

### Post by benevolent on 2007-10-08
I follow exactly the steps at your link and i try the command startx to start X server, but the problem remain the same........

---

