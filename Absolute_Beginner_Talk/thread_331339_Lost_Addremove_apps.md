---
title: "Lost Add/remove apps"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2007-01-04
Hi,
I came back from my vacation/holidays, and installed the updates that were available.  Not sure if that is related.  However, I no longer can see add/remove applications.  Synaptic works fine, but I sometimes like just browsing for programs and not getting cluttered with various packages.

[IMG]http://img362.imageshack.us/img362/2120/noaddremaa4.jpg[/IMG]

Wonder if anyone has any ideas?  I'm lost for ideas myself.

Thanks a lot,
Matt

---

### Post by zmuth734 on 2007-01-04
right click on applications and click edit menus

click applications and check add/remove

if its not there then add new item:

name: Add/Remove...
command: /usr/bin/gnome-app-install

You can find the icon under /usr/share/icons/hicolor/24x24/apps/gnome-app-install.png

Let me know how it goes!

---

### Post by MkfIbK7a on 2007-01-04
zmuth gave very good advice


also you could just use synaptic package manager
Systems > Adminatsration > Synaptic package manager

---

### Post by Hurricane on 2007-01-04
Thanks for the reply!

Followed your advice, and worked like a charm... except for one thing ;) 

It seems gnome-app-install isn't installed.  I used sudo apt-get install gnome-app-install to install this, but for the last few days I've not been able to do this due to problems with one update server:

Install these packages without verification [y/N]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main gnome-app-install 0.2.21
  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.2.21_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.2.21_all.deb)  Temporary failure resolving 'au.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
matthew@matthew-desktop:~$ 

apt-get update results in:
99% [Connecting to au.archive.ubuntu.com]   and sticks there.

Just my luck, heh.

Thanks for the help though, getting warmer :)

---

### Post by Hurricane on 2007-01-04
Just to add, I manually downloaded the .deb from [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.2.21_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.2.21_all.deb)

(same url as given in the error, with au.  removed)... this has allowed me to install gnome-app-install.  However, a few (around 5% of packages) keep giving me similar errors.

Thanks for your help, helped me find out where this problem lies :).

Happy new year,
Matt

---

