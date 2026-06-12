---
title: "Install GNOME from KDE using Dapper live CD"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by ubuntumaybe on 2006-12-14
Hi,

From KDE I managed to install LAMP from the server CD by using apt-cdrom add. I have added the Dapper live cd packaged list using the same command. I have attempted to install the gnome desktop by trying  apt-get install ubuntu-desktop and apt-get install gnome-desktop but no luck. I cannot find a reference to the gnome desktop in KDE GUI install. So how can I install the gnome desktop from within KDE using the Dapper live CD. THanks.

---

### Post by pay on 2006-12-14
Well ubuntu-desktop is a meta package so that might be why it won't install off the cd. try apt-get install gnome

---

### Post by Bachstelze on 2006-12-14
IIRC, you can't use Desktop CDs as repositories for installing packages. You need an Alternate CD for this.

---

