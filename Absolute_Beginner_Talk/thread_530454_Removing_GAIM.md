---
title: "Removing GAIM"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-08-20
alan@ubuntu:~$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gaim nautilus-sendto ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5747kB disk space will be freed.
Do you want to continue [Y/n]? 

Can I remove GAIM without removing the other packages?

---

### Post by Steve1961 on 2007-08-20
I don't think you can.

---

### Post by Kosimo on 2007-08-20
> **Armman said:**
> alan@ubuntu:~$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gaim nautilus-sendto ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5747kB disk space will be freed.
Do you want to continue [Y/n]? 

Can I remove GAIM without removing the other packages?

Why do you want to remove GAIM without removing the (useless packages) ?

Are you may trying to install the latest pidgin?

---

### Post by MenZa on 2007-08-20
@Kosimo: "ubuntu-desktop" holds all your basic applications. Useless? I think not.

Gaim is part of the metapackage ubuntu-desktop, and can therefore not be removed, as far as I know. Sorry.

---

### Post by AlexenderReez on 2007-08-20
> **MenZa said:**
> @Kosimo: "ubuntu-desktop" holds all your basic applications. Useless? I think not.

Gaim is part of the metapackage ubuntu-desktop, and can therefore not be removed, as far as I know. Sorry.

ubuntu-desktop is just meta package...no need to worry about it....

---

### Post by becominglumberg on 2007-08-20
You are correct. Don't worry about removing it though - ubuntu-desktop is just a 'fake' package that has a boatload of programs as dependencies, all of what fills out Ubuntu's version of GNOME. If you remove it, it only removes this layer that is used to pull all the others along, but nothing else will be removed from your computer. It is pretty much the shrink wrap.

---

### Post by MenZa on 2007-08-21
> **becominglumberg said:**
> You are correct. Don't worry about removing it though - ubuntu-desktop is just a 'fake' package that has a boatload of programs as dependencies, all of what fills out Ubuntu's version of GNOME. If you remove it, it only removes this layer that is used to pull all the others along, but nothing else will be removed from your computer. It is pretty much the shrink wrap.

Ah, I thought it was meant such as all the applications in ubuntu-desktop depended on each other, and thus if you moved one, they'd all be removed.

---

### Post by nocturn on 2007-08-21
> **MenZa said:**
> Ah, I thought it was meant such as all the applications in ubuntu-desktop depended on each other, and thus if you moved one, they'd all be removed.

No, they won't.  But, it may cause problems when upgrading (the new ubuntu-desktop may pull in extra packages which won't happen if you removed it).

---

