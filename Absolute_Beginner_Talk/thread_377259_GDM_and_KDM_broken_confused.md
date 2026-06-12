---
title: "GDM and KDM broken :confused:"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2007-03-05
Ever since installing kubuntu-desktop over my ubuntu I've been having problems with gdm and kdm.
I've tried```
dpkg-reconfigure kdm
```and```
dpkg-reconfigure gdm

```and it didnt help.
Whenever I started my computer up, it took me to a terminal login and when I typed startx, it logged me into GNOME, when I wanted KDE.
So, stupidly I uninstalled both gdm and kdm (selecting completely remove), planning on reinstalling kdm afterwards, and when I tried to reinstall it I got this message.> luke@swan-desktop:~$ sudo apt-get install kdm
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
kdm: Depends: kdebase-bin (= 4:3.5.5-0ubuntu3) but 4:3.5.5-0ubuntu3.2 is to be installed
E: Broken packages
I need help cause I know if I log out I'll have one hell of a time trying to log back in again.
WHAT DO I DO

---

### Post by taurus on 2007-03-05
Double post.  Please check the original thread here.

[http://www.ubuntuforums.org/showthread.php?t=377248](http://www.ubuntuforums.org/showthread.php?t=377248)

---

