---
title: "I can't install programs"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by izua on 2006-11-25
hi everyone. i'm pretty new to kubuntu and linux in general.
i'm trying to install stuff with adept from kde, however, when i pick something up, they generally end up giving me a red "break(install)" near them. i don't know what that is. it happened on php5, apache, gaim, firefox. 
oh, one more thing. how do i run gcc? "gcc -o a.cpp a" doesn't seem to work.

thank you.

---

### Post by xyz on 2006-11-25
Hi,
Try this:
[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")
Simple and visual!

---

### Post by izua on 2006-11-25
well, i don't want to be rude, but i don't have synaptic, and i'm using kubuntu. and the respective tutorial doesn't explain what that break(install) thingy is, or how should i correct it, either ](*,)

---

### Post by taurus on 2006-11-25
For gcc, you need the build-essential package...  Open a terminal and type

```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

### Post by CaveRat on 2006-11-25
> **izua said:**
> well, i don't want to be rude, but i don't have synaptic, and i'm using kubuntu. and the respective tutorial doesn't explain what that break(install) thingy is, or how should i correct it, either ](*,)

If you're using the Kubuntu desktop, on the K Menu choose System-~,Package Manager (Synaptic Package Manager)

---

### Post by izua on 2006-11-25
```
izua@izuabox:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Get:2 http://repository.debuntu.org dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://repository.debuntu.org dapper Release
Hit http://repository.debuntu.org dapper/multiverse Packages
Hit http://repository.debuntu.org dapper/multiverse Sources
Fetched 2B in 0s (2B/s)
Reading package lists... Done
izua@izuabox:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
izua@izuabox:~$ gcc -v
bash: gcc: command not found

```

---

### Post by taurus on 2006-11-25
Can you paste your output of this command from a terminal?

```
cat /etc/apt/sources.list
```
p.s.  Build-essential is also available from the CD, the same one that you used to install Ubuntu on your machine...

---

### Post by izua on 2006-11-25
```
# Line commented out by installer because it failed to verify:
# deb http://ro.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ro.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://ro.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ro.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ro.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ro.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse

izua@izuabox:~$                                                               
```

I've enabled most of them, which were commented, and a friend also told me to add the ones in debuntu.org.

---

### Post by taurus on 2006-11-25
No wonder you can't get anything because you disable most of the repos!!!

```

# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse

```
Save it and run these three commands again...

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install build-essential
```

---

