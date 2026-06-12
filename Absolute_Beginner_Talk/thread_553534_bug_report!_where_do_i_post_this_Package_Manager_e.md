---
title: "bug report! where do i post this? Package Manager erroring. pls help!"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-17
hey all. i was trying to install Maya 8.5 and managed to find a bug - or so the error message says. 

here's the back story: i converted the packages from RPM to DEB using alien, and installed the DEB packages by double-clicking and using the package manager utility. then, later, i was following a different tutorial and tried installing the DEB again using the terminal as instructed in this ([http://www.wouz.dk/autodesk-maya-misc/maya-8-installation-under-kubuntu-6061-lts/](http://www.wouz.dk/autodesk-maya-misc/maya-8-installation-under-kubuntu-6061-lts/)) tutorial. i got a bunch of errors with the dpkg command - not the command itself, but while its unpacking or whatever it spits out some errors, and now my update-manager is giving me this error :

> A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Unknown Error: '<type 'exceptions.SystemError'>' (E:The package awcommon needs to be reinstalled, but I can't find an archive for it.)

i've tried running the package manager and it only gives me the option of closing it. i wouldn't think that it's a bug except for 1) the original error code told me it was a bug, and 2) there's no way for me to stop package-manger from trying to find the DEB again and again.

---

### Post by Maestro23 on 2007-09-17
Try using the following command on the package in question:

> sudo dpkg --force-remove-reinstreq –remove pkgname

---

### Post by ijason on 2007-09-17
thanks for the suggestion. here's the error message that gets. :

> jason@jason-laptop:~$ sudo dpkg --force-remove-reinstreq –remove awcommon_10.80-14_i386.deb
Password:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jason@jason-laptop:~$ 


i'll try to get the dpkg to work, i think you're on the right track, just need the syntax tweaked.

---

### Post by FuturePilot on 2007-09-17
You don't need the whole package name. awcommon should do it
```
sudo dpkg --force-remove-reinstreq –remove awcommon
```

---

### Post by Maestro23 on 2007-09-17
Try just the name of the package** without** the **.deb** at the end.

---

### Post by ijason on 2007-09-17
it's still saying i need an action option.  am i missing something? 

> jason@jason-laptop:~$ sudo dpkg --force-remove-reinstreq –remove awcommon
Password:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jason@jason-laptop:~$ 

---

