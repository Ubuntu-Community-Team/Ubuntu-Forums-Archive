---
title: "Install software on PC with no Internet Connection"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by SRXy on 2005-05-23
Is it possible to download programmes for Ubuntu on a seperate machine (Running Windows) and then install them on a Ubuntu that has no Internet connection?

---

### Post by poofyhairguy on 2005-05-23
[QUOTE=SRXy]Is it possible to download programmes for Ubuntu on a seperate machine (Running Windows) and then install them on a Ubuntu that has no Internet connection?[/QUOTE]


Yes. Download the deb files on the interneted computer (along with their dependencies) here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

then install with this command:

sudo dpkg -i packagename.deb

Dependancies first of course.

---

### Post by Gustav on 2005-05-23
[QUOTE=SRXy]Is it possible to download programmes for Ubuntu on a seperate machine (Running Windows) and then install them on a Ubuntu that has no Internet connection?[/QUOTE]
 Yes, it is. But it might be hard to keep track of all dependencies.

You'll have to check the dependencies of the package you want to install and then the dependencies of the packages that the original package depends on and so on (mostly it doesn't end up in more than maybe three packages).
Then you'll have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and find and download the packages (they'll end with .deb) and somehow move them to your Ubuntu computer.
Then install the packages with the command:
```
sudo dpkg -i "package name".deb
```
Be sure to start with the packages that have their dependencies resolved (if package A depends on package B, install package B first)

Good luck!

<edit> AH.. I'm too slow

---

### Post by matej on 2005-05-23
You can download .deb files on windows machine and install them on Ubuntu. Main source will be probably [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Installation of downloaded package
 ```
 sudo dpkg -i package_name.deb
``` 
But this method doesn't care about security updates and new versions of packages. Maybe apt-zip tool could help you. It generates scripts, that download needed packages on machine connected to internet. Then you move them to your Ubuntu box and finish update.

[http://packages.ubuntu.com/hoary/admin/apt-zip]("http://packages.ubuntu.com/hoary/admin/apt-zip")

Also "Using apt-get offline" howto exists - [http://www.batmat.net/apt-offline/]("http://www.batmat.net/apt-offline/") but I think that apt-zip is far better solution.

---

### Post by SRXy on 2005-05-23
which is critical...

depends or recommends?

also,

Do I download all the packages that each successive package requires?? 

Which file to I download? 

on the [http://packages.ubuntu.com/hoary/admin/debconf](http://packages.ubuntu.com/hoary/admin/debconf) page, do I download the architecture>all or do I download the source at the bottom?

sorry so many q's

---

### Post by UbuWu on 2005-05-23
Take a look here: [http://ubuntuforums.org/showthread.php?t=34113](http://ubuntuforums.org/showthread.php?t=34113) 
Probably a bit too complicated for an absolute beginner though

---

### Post by SRXy on 2005-05-23
crikey.....this is gonna take sometime. I reckon it's just better to bite the bullet and spend some quality time downloading at home....<sigh>...mmmm, maybe it's time to get broadband

---

### Post by poofyhairguy on 2005-05-23
[QUOTE=SRXy]...mmmm, maybe it's time to get broadband[/QUOTE]

Let me straight up admit- everytime I download software/upgrade/update I wonder how people can stand using Linux (or heck, windows too, those updates are big) without broadband.

---

### Post by Gustav on 2005-05-24
[QUOTE=SRXy]which is critical...

depends or recommends?

also,

Do I download all the packages that each successive package requires?? 

Which file to I download? 

on the [http://packages.ubuntu.com/hoary/admin/debconf](http://packages.ubuntu.com/hoary/admin/debconf) page, do I download the architecture>all or do I download the source at the bottom?

sorry so many q's[/QUOTE]
 Depends is critical, recommends mostly adds features.

If there's required packages that you already have installed then you don't need to download them.

You should download the architecture>all.

Hope it helps!

---

### Post by SRXy on 2005-05-24
thanks...seeing as I'm cursed with a conexant winmodem, I'm gonna have to go through this everytime I need a programme before I get a my hardware modem

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=SRXy]thanks...seeing as I'm cursed with a conexant winmodem, I'm gonna have to go through this everytime I need a programme before I get a my hardware modem[/QUOTE]


Well at least you are willing to buy a better modem. That is the spirit that leads to success.

---

### Post by tenma on 2006-08-20
Hi, i'm in the same situation as the OP.  I have a winmodem and want to install programs on ubuntu without an internet connection.  The program i'm after is Video Lan Client (VLC)

[http://packages.ubuntu.com/dapper/graphics/vlc](http://packages.ubuntu.com/dapper/graphics/vlc)

I count over 30 dependancies i need to install.  How should i go about doing this?  Do i have to download and install each of them manually?

help is appriciated :)

---

