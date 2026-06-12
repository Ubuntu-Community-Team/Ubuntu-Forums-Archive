---
title: "Installing Java"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kq6up on 2007-01-16
I have updated my sources list.  I am running xubuntu 6.06.  I am not able to install sun-jre.

Help.  Here is my sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by jvc26 on 2007-01-16
Have you had a look on [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) It has a section on installing JRE and on putting in new sources to your sources.list
Il

---

### Post by kq6up on 2007-01-16
On regular Ubuntu 6.10 I have been able to install Java just by adding them in the software add/remove tool.  xubuntu doesn't seem to  have this option.  I am following the directions from:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Is there something wrong with my sources.list file?  I have multiverse added, so shouldn't I be able to do # apt-get install sun-java5-jre # ?

---

### Post by kq6up on 2007-01-16
p.s.  When I did a:

# apt-get install java-package

I got the message:

Reading package lists... Done
Building dependency tree... Done
Package java-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package java-package has no installation candidate

So it seems like I am not able to install the thing that I need to make a package out of the sun bin self extracting file.

---

### Post by kq6up on 2007-01-16
I fixed it.  I had to follow the top of the article:

Prerequisites

/!\ To install proprietary Java, you must have the Multiverse repository enabled. Keep in mind that this repository is different from the backports Multiverse repository. That is, do not simply uncomment the "multiverse" line for backports. Instead, you will need to add "multiverse" to the existing main line in sources.list.

For more information about the Multiverse repository, please visit the following guide:

Managing Repositories.

---

