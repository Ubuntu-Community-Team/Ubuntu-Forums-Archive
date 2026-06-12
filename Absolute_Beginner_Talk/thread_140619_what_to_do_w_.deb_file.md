---
title: "what to do w/ .deb file?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-03-06
so i have a package of fluxbox for ubuntu. But i dont know how to install it? is that the right word? im not quite sure what a package is...
any help would be great. thanks

---

### Post by Klaidas on 2006-03-06
To install a downloaded debian package:
```
dpkg -i file.deb
```

However, there might be a simplier way to do it:
```
sudo apt-get install programname
``` would download the program and install it with the dependencies :)

---

### Post by carlosqueso on 2006-03-06
If you have a decent internet connection, you shouldn't need or use that deb file.  You should use apt.  Simply make sure the universe repo is enabled by typing sudo gedit /etc/apt/sources.list and making it look like mine:

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
``` then typing ```
apt-get install fluxbox
``` If you are set on using the deb, cd into the directory that contains it and type ```
dpkg -i <name of deb>
``` where <name of deb> is the exact name of the .deb file.

---

### Post by animesh on 2006-03-06
[http://www.ubuntuguide.org/#installuninstalldebfiles](http://www.ubuntuguide.org/#installuninstalldebfiles)

this may help you

---

### Post by jinxjinx on 2006-03-06
Wow. Thanks for all the help. The reason i dont get fluxbox from the repositorys is I read that their version of fluxbox is out of date.

---

