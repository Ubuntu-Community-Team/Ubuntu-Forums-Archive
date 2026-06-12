---
title: "I installed msttcorefonts, but still no text/fonts in flash"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-16
Hello,
I've installed msttcorefonts  because I wanted to see the text in flash, but even after installing it, I don't see any text. Please help.

Thank you very much!

---

### Post by Jagot on 2006-08-16
Try installing the gsfonts and gsfonts-x11 packages.

---

### Post by hanzj on 2006-08-16
I tried installing gsfonts and gsfonts-x11, but  they seem to be not in repository:

> sudo aptitude install gsfonts
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

hanzj@ubuntu:~$ sudo aptitude install gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by Jagot on 2006-08-16
They're certainly there:

[http://packages.ubuntu.com/dapper/x11/gsfonts-x11](http://packages.ubuntu.com/dapper/x11/gsfonts-x11)
[http://packages.ubuntu.com/dapper/text/gsfonts](http://packages.ubuntu.com/dapper/text/gsfonts)

Can you post your sources.list?

---

### Post by Perfect Storm on 2006-08-16
Hanzj you need to enable universe/multiverse in your sourcelist.

---

### Post by hanzj on 2006-08-16
Looks like I have enabled universe.

cat /etc/apt/sources.list

> # deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Release i386 (20060601)]/ dapper main restricted


# deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Release i386 (20060601)]/ dapper main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper[COLOR="Red"] universe multiverse[/COLOR]
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#to get opera
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


---

