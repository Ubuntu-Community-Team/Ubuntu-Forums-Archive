---
title: "X Server doesn't work"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by moneylosr20 on 2005-12-29
My friend and I are trying to get a Toshiba Portégé 7020CT with 150MHz to work with Breezy Badger 5.10. The OS works fine until the moment before the login screen... the X server doesn't load. Breezy Badger booted up fine without any problems when we put the laptop's hard drive in a different computer, yet when we put it back in the same computer, X refuses to work. We'd like to get it working for a friend that needs the computer. Is there something we need to edit or is putting Breezy Badger (or any other version of Ubuntu) on a 150MHz system a lost cause? 

Help would greatly be appreciated.

-Thanks, Bryan K.

---

### Post by d1337 on 2005-12-29
150mhz may be more like a slothy badger, but this is also relative to the amount of Ram you have.  X starting may be hanging you up due to lack of Ram.  Otherwise, Xorg.conf will likely need some editing (if it's gonna happen).  The only Protege 7020CT's that I can find via google boast a P2 366mhz, so it's likely not the same configuration of yours.  I would think that the standard vesa drivers for X would work though...but you won't be playing any Tux Racer.

There seems to be alot of folks using XFCE as a desktop instead of Gnome or KDE for older machines.  This could be accomplished by doing a server install, then installing the needed packages.  A shortcut may be to try a server install and the sudo apt-get install xubuntu-desktop which I think uses XFCE by default.  There are plenty of threads and different ideas about installing Ubuntu on older machines.  If that's the route you need to go, search a bit.

d1337

---

### Post by moneylosr20 on 2005-12-29
btw    the laptop has 128 mb of ram
and how do u install XFCE
also i am a n00b

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=moneylosr20]btw    the laptop has 128 mb of ram
and how do u install XFCE
also i am a n00b[/QUOTE]

Honestly, if you are a noob its better to install a distro meant for older hardware. I suggest Damn Small Linux:

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Easiest solution.

---

### Post by d1337 on 2005-12-29
In my opinion, since you haven't really done anything to this machine yet, I would suggest starting with a fresh install (although you could pick out all of the Ubuntu-desktop stuff by hand), but use the server option.  Basically, put the 5.10 install cd in, reboot the machine, wait for it to come up and type "server" at the prompt (exclude the quotations).  Go thorugh the install process like you did before.  It will be somewhat faster of an install because there are many packages that will not be installed/unpacked/downloaded.  Once the OS is installed, you will boot to a command prompt instead of a graphical login.  Login with your username and password that you set up during install.  

The simplest method, after server install

At the prompt, type in
```
sudo apt-get install xubuntu-desktop
```
and let it roll.  This will pull down some light but functional applications for a GUI to include a light word processor (abiword) and a light webrowser (can't recall which one, but you can add epiphany or something else later).  After download and install of packages, you should be able to have a funtional laptop.

d1337

---

### Post by afhp on 2005-12-29
[QUOTE=moneylosr20] the X server doesn't load. Breezy Badger booted up fine without any problems when we put the laptop's hard drive in a different computer, yet when we put it back in the same computer, X refuses to work.[/QUOTE]

Do you mean, another computer of the same type, or a completely different computer ?

Because from what you say, X is configured for the "other computer", not the Protege.

As I understand your post, the system comes up fine, it's just X that fails to start... Try reconfiguring it when the HDD is in the Protege : 

sudo dpkg-reconfigure xserver-xorg

---

### Post by moneylosr20 on 2005-12-29
We Got It To Work
Thanks To All Who Posted!!!

---

