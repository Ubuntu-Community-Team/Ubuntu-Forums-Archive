---
title: "getting and installing packages without network"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2006-03-13
I have a computer where I need a number of packages, but it is not connected
to the world around it except for the power cable. I can transfer the packages
to it by usb memory, but how would I obtain them? On the connected computer
I tried to run apt-get -d install stuff but since the packages already are installed on
that box it errored out. Is there any website or something? Or a way of obtaining
an address to the packages in the repositories so I could dl them with wget or firefox?

---

### Post by Brunellus on 2006-03-13
[http://packages.ubuntu.com](http://packages.ubuntu.com)

remember to download and install all the dependencies of any given package.

---

### Post by Aine on 2006-03-13
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then sudo dpkg-install  (I think that's the command)

---

### Post by Brunellus on 2006-03-13
[QUOTE=Aine][http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then sudo dpkg-install  (I think that's the command)[/QUOTE]
```
sudo dpkg -i $PACKAGENAME
```

---

### Post by red_Marvin on 2006-03-13
Thanks all!
If you got any ideas for somethings to stuff on an 266MHz Dell laptop with 128mb 
RAM, 4Gb hdd and ubuntu server, then shoot.

---

### Post by AtinLango on 2006-03-13
[QUOTE=Brunellus]remember to download and install all the dependencies of any given package.[/QUOTE]

This is where the real problem is. You can get scared by the too many dependencies listed. However I have come to learn that in many cases, a number of those dependencies are already installed, in which case just doownloading a few dependencies works. But it is a matter of experience.

---

### Post by aysiu on 2006-03-13
Depending on what you need, there's an Add-On CD out there.

More info at [this thread](http://www.ubuntuforums.org/showthread.php?t=136955).

The CD is [here](http://www.tikal26.net/ubuntu/breezyaddon.iso). The list of packages included on it is [here](http://www.ubuntuforums.org/showpost.php?p=813538&postcount=115).

Instructions for how to create your own add-on CD are here:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by AtinLango on 2006-03-13
[QUOTE=aysiu]The CD is [here](http://www.tikal26.net/ubuntu/breezyaddon.iso).
[/url][/QUOTE]

If I can get my hands on this, it would be great. Unfortunately, I tried the link but it was not working. Could it be a temporary problem?

---

