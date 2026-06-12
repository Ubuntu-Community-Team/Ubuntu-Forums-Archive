---
title: "installing programs help for a newb"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-13
i am trying to install a program called synergy for mouse and keyboard sharing from source i type ./configure and it seems to work fine but when i type make or make install i get "bash: make: command not found" 

plz help
inmate

---

### Post by lime4x4 on 2006-08-13
more then likely you don't have the build tools installed try this in a terminal

sudo apt-get install linux-headers-`uname -r` build-essential

that should install everything u need to make and install a app

---

### Post by ciscosurfer on 2006-08-13
The program you want can be found in the repos.  First you need to enable your Universe repo.  Look [at this page]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html#id2542172") to find out how.

Then copy/paste this into a terminal```
sudo aptitude update && sudo aptitude install synergy
``` If you absolutely need to compile any program, I would recommend instead of the typical "*./configure, make, make install*" that you use **checkinstall** instead (you need to dowload this) so it would go something like this: ./configure, make, checkinstall

The reason it's cool is because it creates a .deb file that you can use to uninstall later on if you so choose by doing the following in a terminal```
sudo dpkg -r *package_name_you_are_uninstalling*
``` If you compile a program the other way using *make install* it becomes much, much more difficult to remove a program.

---

### Post by inmate#001 on 2006-08-13
thanks for the help i followed ciscosurfer's advice and installed synergy but now i cant find where it installed so i can configure and run it plz help

---

### Post by ciscosurfer on 2006-08-14
Synergy is controlled by synergyc and synergys.

Type or copy/paste any of the following into a terminal```
whereis synergyc && whereis synergys
which synergyc && which synergys
sudo updatedb && locate synergy | less    {use Enter key (line by line) or Spacebar (page by page) to scroll through it.  When you reach "end" hit "q".}
find /usr/bin -name synergy*
```

---

