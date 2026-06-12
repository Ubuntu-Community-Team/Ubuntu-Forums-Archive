---
title: "weird sources.list line"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2006-10-17
getting ready to upgrade and i get this error

etomic13@etomic13:~$ sudo apt-get update
E: Type 'sudo' is not known on line 5 in source list /etc/apt/sources.list
etomic13@etomic13:~$ sudo apt-get -y dist-upgrade

is my source list messed up how do i fix it

---

### Post by meng on 2006-10-17
Is your sources.list messed up? Yup, that's the important thing to sort out first. Please:
cat /etc/apt/sources.list
and post the output here. (Look for a problem in line 5)

---

### Post by etomic13 on 2006-10-17
etomic13@etomic13:~$ cat /etc/apt/sources.list
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx


sudo apt-get [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


Line 5 appears to be blank

---

### Post by meng on 2006-10-17
Nope, line 5 reads:
sudo apt-get [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Easy solution: delete it.

---

### Post by etomic13 on 2006-10-17
how do i get back to my source list

---

### Post by meng on 2006-10-17
Sorry.
gksu gedit /etc/apt/sources.list
and edit away. You can put a # at the beginning of line 5 to make it a comment (i.e. will be ignored by apt-get/aptitude) but keep the http address there in case you need it later. I don't know anything about beryl, so depending on your blingy desktop needs you may eventually need to get packages from there again.

Package lines typically begin with deb or deb-src, not with sudo apt-get.

---

### Post by etomic13 on 2006-10-17
Hey i like blingy desktops lol, didnt work anyway so i just customized gnome.thanks for the info i just deleted it

---

