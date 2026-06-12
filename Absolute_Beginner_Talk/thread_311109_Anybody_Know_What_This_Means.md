---
title: "Anybody Know What This Means?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Gen2oo on 2006-12-02
this keeps occuring when i install new software:

E: linux-igd: subprocess post-installation script returned error exit status 1

What does it mean? Should i be concerned? How do i fix it?

thanks in advance.....

---

### Post by lamego on 2006-12-02
It means there was an error running a script which is part of a package installation process.
Try removing and installing the package again, it will hopefully be fixed.

---

### Post by Gen2oo on 2006-12-04
i've tried but it happens everytime i install something. my add/remove programs tab has also disappeared as well as my debian menu tab. tried reloading it with automatix2 but it still has not appeared

last resort is going to be to re-install ubuntu!!!

---

### Post by spanella47 on 2006-12-13
same problem here.

```
Selecting previously deselected package linux-igd.
(Reading database ... 144894 files and directories currently installed.)
Preparing to replace linux-igd 0.cvs20060201-1 (using .../linux-igd_0.cvs20060201-1_i386.deb) ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing linux-igd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 linux-igd
```

won't reinstall or uninstall.  just keeps saying the package is in a very bad inconsistent state.

tried forcing install of newer version off of project website with no luck, wants previous version uninstalled (side note: dpkg says the repo version is newer than the site version although the repo is cvs from Feb 2006 and the site's package is from mid 2006)

also, do any of the linux music players support this (banshee, rhythmbox, amarak)?  would be a good new feature to support...

---

### Post by raul_ on 2006-12-13
U can add the add/remove programs by right clicking your Applications menu and choosing "Edit menus"

that error normally means that there is something wrong with your sources. try replacing your sources.list files with the ones here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

if u're using Dapper, just replace Edgy with Dapper in the link

---

### Post by spanella47 on 2006-12-13
all edgy repos here. its in the universe repository

how can we just remove it completely and try the newer version?

---

### Post by raul_ on 2006-12-13
Sorry, i didn't get your question =\ remove what?

---

### Post by spanella47 on 2006-12-14
linux-igd_0.cvs20060201-1_i386.deb
from the universe repo isn't installing correctly but asks to be reinstalled before it can be removed.  an endless cycle.  tried forcing the removal with dpkg but won't let me, is there another way to remove this package.

the other annoyance is that it gives that error every time you try to install anything.  complete removal would be nice.

---

### Post by Supersaiyan.IV on 2006-12-16
Same problem here. After multiple attempts to reinstall/remove/completely remove the 'linux-igd' package i get the following:

> 
Selecting previously deselected package linux-igd.
(Reading database ... 99412 files and directories currently installed.)
Preparing to replace linux-igd 0.cvs20060201-1 (using .../linux-igd_0.cvs20060201-1_i386.deb) External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-igd_0.cvs20060201-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Why is there a package claiming Edgy support but doesn't work anyway?
I want to know if there's ANY alternate way to remove this. How do I go about a 'manual' removal?

Thanx in advance

peace

---

### Post by FeraTech on 2006-12-26
This is how to fix your problem:

```
sudo gedit /var/lib/dpkg/status
```

Find linux-igd

Write down all the file locations.
Should look something like:
/etc/upnpdb

Delete the entire entry from /var/lib/dpkg/status

Now:
Manually delete all the files you wrote down listed in the /var/lib/dpkg/status
```
sudo rm -r "directory name"
```
```
sudo rm "file name"
```

---

