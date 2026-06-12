---
title: "how to install glipper"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-01-30
hey, i'm pretty new at installing apps in linux.

im running ubuntu 6.06 and i'm trying to install glipper 0.95.1

i found a .deb installer but i get an error about packages, even though that package is already installed. any ideas?

see here: 
[IMG]http://www.cse.buffalo.edu/~dhfine/screenshot2.jpg[/IMG]

---

### Post by bruenig on 2007-01-30
```
cd Desktop
sudo dpkg -i glipper_0.95.1-1_i386.deb
```

Paste the output.

---

### Post by finer recliner on 2007-01-30
```
Selecting previously deselected package glipper.
(Reading database ... 109154 files and directories currently installed.)
Unpacking glipper (from glipper_0.95.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of glipper:
 glipper depends on libatk1.0-0 (>= 1.12.2); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 glipper depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.2.
 glipper depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 glipper depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 glipper depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 glipper depends on liborbit2 (>= 1:2.14.1); however:
  Version of liborbit2 on system is 1:2.14.0-0ubuntu1.
 glipper depends on libpango1.0-0 (>= 1.14.7); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 glipper depends on libpopt0 (>= 1.10); however:
  Version of libpopt0 on system is 1.7-5.
 glipper depends on libxfixes3 (>= 1:4.0.1); however:
  Version of libxfixes3 on system is 1:3.0.1.2-0ubuntu3.
 glipper depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing glipper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 glipper

```

---

### Post by bruenig on 2007-01-31
```
sudo apt-get update && sudo apt-get upgrade
```
It looks like you have a lot of old packages that should have been upgraded. Perhaps you also could paste the output of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by finer recliner on 2007-01-31
@bruenig: 

i ran your command, and i am up to date on my packages

last line of output:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


sources list:```

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez games

```

---

### Post by bruenig on 2007-01-31
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

That line is malformed. You need to put the deb-src part on another line.

```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

If you don't know how to edit it, just do 
```
gksudo gedit /etc/apt/sources.list
```
to open it and then make that change and save. After you do that run that 'sudo apt-get update && sudo apt-get upgrade' again.

---

### Post by finer recliner on 2007-01-31
thanks for the reply, unfortunately there must have been a typo (idk how!) between copying and pasting, because my sources.list file is now intact. I have carefully examined each line in the file, and it looks ok. synaptic still has nothing to update on my system

here it is again:

```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez games

```

---

### Post by finer recliner on 2007-02-02
bump

the installer still thinks there are version upgrade problems. any suggestions?

---

### Post by deadgobby on 2007-02-02
How about using the super cow powers of aptitude?

sudo aptitude install glipper

Gobby

---

### Post by finer recliner on 2007-02-02
already tried:


...
No candidate version found for glipper
...

---

### Post by lamego on 2007-02-02
The problem is that the package libatk1.0 has an internal version and the glipper you are trying to install was packaged requiring a newer version.

Use this .deb instead:
[http://www.getdeb.net/app.php?name=glipper](http://www.getdeb.net/app.php?name=glipper)

---

### Post by finer recliner on 2007-02-02
you sir, are a gentleman and a scholar!


thank you so much, i was ready to pull out my hair, as i tried searching for a bunch of library packages manually. grrr


thanks again.

---

### Post by chavo on 2007-02-02
Looks like that deb was built for edgy and you are still on dapper. But nice to see you found a package that works!

---

### Post by szxuzhou on 2007-03-18
Hi LAMEGO,
Thank you so much for your useful information. Glipper is working fine.

---

