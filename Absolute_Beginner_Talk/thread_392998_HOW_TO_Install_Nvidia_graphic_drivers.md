---
title: "HOW TO: Install Nvidia graphic drivers"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-03-25
Hello

I am wondering if somebody can tell me how can I install latest NVIDIA-Linux-x86-1.0-9742-pkg1.run, graphic drivers to my Ubuntu 6.10?

Thnx

---

### Post by overdrank on 2007-03-25
> **Urko said:**
> Hello

I am wondering if somebody can tell me how can I install latest NVIDIA-Linux-x86-1.0-9742-pkg1.run, graphic drivers to my Ubuntu 6.10?

Thnx

Hi this method worked for me.
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Good luck!:guitar:

---

### Post by Urko on 2007-03-25
I dowload latest envy_0.9.1-0ubuntu3_all.deb drivers on my home folder than typed in terminal :
$ sudo dpkg -i envy_0.9.1-0ubuntu3_all.deb
Selecting previously deselected package envy.
(Reading database ... 126528 files and directories currently installed.)
Unpacking envy (from envy_0.9.1-0ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

It give me this?

What can I do now:confused:

---

### Post by ndube on 2007-03-25
> **Urko said:**
> I dowload latest envy_0.9.1-0ubuntu3_all.deb drivers on my home folder than typed in terminal :
$ sudo dpkg -i envy_0.9.1-0ubuntu3_all.deb
Selecting previously deselected package envy.
(Reading database ... 126528 files and directories currently installed.)
Unpacking envy (from envy_0.9.1-0ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

It give me this?

What can I do now:confused:

I would start by installing the packages that are required by envy, listed in the error message quoted.

sudo apt-get install xserver-xorg-dev module-assistant fakeroot dh-make debhelper

Then try to install envy.

---

