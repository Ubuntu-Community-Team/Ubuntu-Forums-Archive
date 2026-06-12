---
title: "Installation Problem"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by typon on 2006-05-19
This is really pissing me off, so PLEASE help me out.

I followed the "unofficial wiki" of Ati driver installation (link from this forum)

and this is what happens...
 --------------------------------------------------------
$ sudo apt-get install gcc-3.4 module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp-3.4 dpkg-dev g++ g++-4.0 gcc gcc-3.4-base gcc-4.0
  libstdc++6-4.0-dev make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-3.4-doc libc6-dev-amd64
  gcc-4.0-locales lib64gcc1 libstdc++6-4.0-doc stl-manual dialog
Recommended packages:
  libmudflap0-dev libterm-size-perl libterm-readkey-perl
The following NEW packages will be installed:
  binutils build-essential cpp-3.4 dpkg-dev g++ g++-4.0 gcc gcc-3.4
  gcc-3.4-base gcc-4.0 libstdc++6-4.0-dev make module-assistant
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 2459kB/8872kB of archives.
After unpacking 33.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
---------------------------------------------------------------

i have tried capital Y and just pressing enter, like on this other post... but still doesnt work

can any one PLZ help urgent...

---

### Post by catlett on 2006-05-19
I've never seen that before. This might end up the same way but it can't hurt. Try using aptitude instead of apt-get. So instead of ```
sudo apt-get install gcc-3.4 module-assistant build-essential
``` Enter it like this```
 sudo aptitude install gcc-3.4 module-assistant build-essential
``` It is the same package being installed except aptitude is another variation of the apt package system. Maybe that will get by that y bug you have.

P.S. did you try n?

---

### Post by S{yndrom}e on 2006-05-19
umm i dunno have you tried seeing if you have enough space?

---

