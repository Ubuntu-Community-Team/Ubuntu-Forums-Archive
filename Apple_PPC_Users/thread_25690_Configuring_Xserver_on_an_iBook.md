---
title: "Configuring Xserver on an iBook"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by Gray Ghost on 2005-04-10
I've searched the support files and I have not been able to find any help on the configuration of Xserver on an iBook.  When I installed Ubuntu, it said that it could not load XServer and than it gave me what looks like a command line so I can configure it myself, anyone know what I have to do to get Ubuntu to run?

---

### Post by erkki70 on 2005-04-11
Hi,
on console try typing the following to configure your X server correctly:
```
sudo dpkg-reconfigure xserver-xfree86
```
enter your password and answer the questions, it should go fine this way.

Hope it helps.
Cheers,
Erkki

---

### Post by Gray Ghost on 2005-04-11
It says that the package is not installed and no info is available, any way to fix this?

---

### Post by erkki70 on 2005-04-12
Hi,
Are you **sure** you're running Warty 4.10?
If you're running Hoary 5.04, then type  ```
sudo dpkg-reconfigure xserver-xorg
```
If you're sure your version is Warty then you have to install X with apt-get command.

Hope this helps.
Cheers,
Erkki

---

### Post by Gray Ghost on 2005-04-12
[QUOTE=erkki70]Hi,
Are you **sure** you're running Warty 4.10?
If you're running Hoary 5.04, then type  ```
sudo dpkg-reconfigure xserver-xorg
```
If you're sure your version is Warty then you have to install X with apt-get command.

Hope this helps.
Cheers,
Erkki[/QUOTE]
 Still says the package is not installed... I hate to ask so many questions, but I have no idea how to fix this.

---

### Post by erkki70 on 2005-04-13
Hi,
I'm afraid that without more infos it's almost impossible to really help.
Precise which Ubuntu version you're trying to install, Warty or Hoary.
Try to tell what was your install procedure step by step, which installer you loaded (kernel), any special settings, etc...
At this point you should have X installed, XFree86 if Warty version or Xorg if Hoary.

Maybe reinstalling with the right options might be the best solution. If X didn't properly install other essentials might be also missing.

Before this you could try the following:
 ```
sudo apt-get install ubuntu-desktop
```
This should install all necessary packages, hopefully inclunding a X server.

Hope this helps,
Cheers
Erkki

---

### Post by directrealist on 2005-05-13
[QUOTE=Gray Ghost]I've searched the support files and I have not been able to find any help on the configuration of Xserver on an iBook.  When I installed Ubuntu, it said that it could not load XServer and than it gave me what looks like a command line so I can configure it myself, anyone know what I have to do to get Ubuntu to run?[/QUOTE]

I had the same general symptoms as you. but with hoary. i tried reinstallang and noticed that xserver was not installing corectly. if you got a message that says some pacages were corupt. i reburned teh iso using a different progam and a better cd. it solved the problem. 

if you are SURE you are not getting errors on intstall then this prob wont help.

---

