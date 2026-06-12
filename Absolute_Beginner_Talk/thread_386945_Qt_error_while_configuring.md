---
title: "Qt error while configuring"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by sushii. on 2007-03-17
Whenever I try to install some software I always get this error:
```
checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

```
Can anyone help? Thanks. :confused:

---

### Post by christhemonkey on 2007-03-17
For compiling you will need develepmont files.

Generally found in -dev packages try installing libqt3-mt or libqt3-mt-dev:
```
sudo apt-get install libqt3-mt-dev 
```

Also you may want to attach the config.log as this will probably help us further assist you!

---

### Post by sushii. on 2007-03-17
I tried to install the package but i got this error:
```
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```
And I tried running the two commands shown but nothing worked. Here's my config.log:

[config.log]("http://www.MegaShare.com/131377")

---

### Post by christhemonkey on 2007-03-17
What is the output from sudo apt-get update?
```
sudo apt-get update 
```

---

### Post by sushii. on 2007-03-17
```
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper Release
Ign http://ubuntu.beryl-project.org dapper Release.gpg
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Ign http://ubuntu.beryl-project.org dapper Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper-updates/universe Packages
Ign http://ubuntu.beryl-project.org dapper/main Packages
Hit http://security.ubuntu.com dapper-security Release
Ign http://ubuntu.beryl-project.org dapper/main Packages
Err http://ubuntu.beryl-project.org dapper/main Packages
  404 Not Found [IP: 64.15.154.150 80]
Hit http://security.ubuntu.com dapper-security/main Packages
Err http://ubuntu.beryl-project.org dapper/main Packages
  404 Not Found [IP: 64.15.154.150 80]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Ign http://www.albertomilone.com binary/ Release.gpg
Ign http://www.albertomilone.com binary/ Release
Hit http://www.albertomilone.com binary/ Packages
Get:4 http://wine.budgetdedicated.com dapper Release.gpg [191B]
Hit http://wine.budgetdedicated.com dapper Release
Ign http://wine.budgetdedicated.com dapper/main Packages
Ign http://wine.budgetdedicated.com dapper/main Sources
Hit http://wine.budgetdedicated.com dapper/main Packages
Hit http://wine.budgetdedicated.com dapper/main Sources
Get:5 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Get:6 http://download.tuxfamily.org dapper Release.gpg [189B]
Get:7 http://download.tuxfamily.org dapper Release [7170B]
Hit http://download.tuxfamily.org dapper/beryl-svn Packages
Fetched 7176B in 16s (433B/s)
Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/main/binary-i386/Packages.gz 404 Not Found [IP: 64.15.154.150 80]
Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/main/binary-i386/Packages.gz 404 Not Found [IP: 64.15.154.150 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by christhemonkey on 2007-03-18
And what is the output of:
```
sudo apt-get --fix-missing 
```
?

Sounds like your repositories are slightly confused.

---

### Post by sushii. on 2007-03-18
It just gives me a usage thingy:
Usage: apt-get [options] command
```

       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.
...
etc.

```

---

### Post by Bachstelze on 2007-03-18
You have a down repo. Please paste your /etc/apt/sources.list

---

### Post by sushii. on 2007-03-18
sources.list
```


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://ubuntu.beryl-project.org dapper main

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/

deb http://ubuntu.beryl-project.org dapper main
deb http://download.tuxfamily.org/3v1deb dapper beryl-svn


```

---

### Post by h0ax on 2007-03-18
comment out that deb ubuntu.beryl-project.org 
It looks like it's the culprit of your 404 errors.

Just put a # in front of the line deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
save and retry

---

### Post by h0ax on 2007-03-18
Also - why is it in your list twice?

---

### Post by sushii. on 2007-03-18
oooo. I knew it had something to do with that! Thanks.
EDIT: Umm, it's in my list twice cuz I think I tried to install Beryl twice, and forgot I'd already included it. lol

---

### Post by sushii. on 2007-03-18
Ok, well now I get this error: *sigh*
```

yoshi@yoshi-pc:~$ sudo apt-get install libqt-mt-dev
Reading package lists... Done
Building dependency tree... Done
Package libqt-mt-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libqt3-mt-dev
E: Package libqt-mt-dev has no installation candidate
yoshi@yoshi-pc:~$ sudo apt-get install libqt-mt
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt-mt

```
Sorry to bother you.

---

### Post by christhemonkey on 2007-03-18
Try installing libqt3-mt-dev then! :)

```
sudo apt-get install libqt3-mt-dev 
```

---

### Post by sushii. on 2007-03-18
> **sushii. said:**
> Ok, well now I get this error: *sigh*
```

**yoshi@yoshi-pc:~$ sudo apt-get install libqt-mt-dev**
Reading package lists... Done
Building dependency tree... Done
Package libqt-mt-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libqt3-mt-dev
E: Package libqt-mt-dev has no installation candidate
yoshi@yoshi-pc:~$ sudo apt-get install libqt-mt
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt-mt

```
Sorry to bother you.
I did lol.

---

### Post by christhemonkey on 2007-03-18
libqt**3**-mt-dev!!

```
sudo apt-get install libqt3-mt-dev 
```

---

### Post by h0ax on 2007-03-18
You did

```
sudo apt-get install libqt3-mt-dev 
```

??

---

### Post by h0ax on 2007-03-18
It's saying "this package can't be found, but here's a similar one: name-of-other-package"
so now you install the name-of-other-package instead

---

