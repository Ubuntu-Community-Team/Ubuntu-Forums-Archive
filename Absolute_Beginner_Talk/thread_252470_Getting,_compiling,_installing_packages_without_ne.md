---
title: "Getting, compiling, installing packages without network"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by bbalpha on 2006-09-06
So I've managed to borrow someone's cd burner, got myself the alternate install cd burned.  A couple of bumps and false starts later, and I finally have Ubuntu 6.06 installed on this machine as a dual boot with XP.  Yay, progress!

Except - I have a USB wifi device that isn't supported by the standard installation and, since I can't connect to the internet from Ubuntu, I can't get Ubuntu to pull down applications.

Near as I can figure, I've downloaded (in XP, saved to a FAT partition that I can access from Ubuntu) the source code for native drivers for my network device.  But as far as I can tell, I don't have make or gcc or any of those things installed, so I can't compile the drivers.  If I don't have a compiler, I can't pull down the source for gcc/make/etc and compile them.

Did I overlook them?

---

### Post by monktbd on 2006-09-07
you will need a few more packages for that.

the easiest way would be to launch an 

> sudo apt-get install build-essential 

from ubuntu. unfortunately you dont have that option.
looking at what is installed there you need the following packages:
> 
libc6-dev 
libc-dev
gcc (>= 4:4.0)
g++ (>= 4:4.0)
libstdc++ -dev 
make
dpkg-dev (>= 1.13.5)
base-files
base-passwd
bash
bsdutils
coreutils
debianutils
diff
dpkg
e2fsprogs
findutils
grep
gzip
hostname
login
mount
ncurses-base
ncurses-bin
perl-base
sed
sysvinit
tar
util-linux


very likely some dependencies arent met but usually automatic resolved by apt-get.
some probably are already installed so you dont need to get them.

the first 6 seem to be the most important.
download them, try to install them with dpkg and then see what dependancies are still missing. and get them as well.
can get a bit tedious though.

edit:
just read in this thread
[http://www.ubuntuforums.org/showthread.php?t=246585](http://www.ubuntuforums.org/showthread.php?t=246585)
that the build-essential package is on the install cd.
look there for how to install it.

---

