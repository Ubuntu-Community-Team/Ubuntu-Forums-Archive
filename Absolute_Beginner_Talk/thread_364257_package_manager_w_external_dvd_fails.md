---
title: "package manager w/ external dvd fails"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by jokeeeffe on 2007-02-18
Hi,

I dont have internet access for my ubuntu 6.02 and im trying to load new packages from an external dvd player (sony drx-830U) w/ ubuntu 6.10 dvd. i select a package to upgrade/install, for example, mysql-client, click apply but it requests to put the disk in /cdrom. sigh! can i add the ability for ubuntu to check my external dvd player? i try to add my dvd player via Settings ->Repositories but it won't let me add a dvd player and the ability to edit the cdrom is greyed out. I believe its recognizing the dvd player cuz the icon is showing on the desktop and i can see files for that dvd. some reason the package manager won't. do i need to manually mount the dvd player? the funny thing is if i restart w/ the dvd in as it starts, it will allow me to successfully update/install a package via the dvd without any setting changes but after i make one change, if fails to find the disc again!?!

Hopefully this makes some sense, ill explain more if you dont understand my jibberish. thanks

---

### Post by istrebitjel on 2007-02-18
Try this
```
apt-cdrom -d=/media/WhatEver add
```

Otherwise, try editing /etc/apt/sources.list

---

