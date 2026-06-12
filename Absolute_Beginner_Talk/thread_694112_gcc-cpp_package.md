---
title: "gcc-cpp package?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Ramthebuffs on 2008-02-11
I'm trying to install this and it says it can't find the package, where can I get it?

---

### Post by taurus on 2008-02-11
Try installing the build-essential package.

```
sudp apt-get update
sudo apt-get install build-essential
```
And if you can't install it, post your /etc/apt/sources.list to make sure you have enable all the repos in there.

```
cat /etc/apt/sources.list
```

---

### Post by Joeb454 on 2008-02-11
What're you trying to do?

If you want to Compile C++ code I think you need to use g++

As far as I know, it's the same syntax as gcc :)

---

### Post by Ramthebuffs on 2008-02-11
Thanks for the help on this, I'm still getting nowhere



> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2008-02-11
Can you post the exact error message when you ran those two commands from a terminal?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by nemilar on 2008-02-11
The build-essential package should be in the main repositories.  Does this command produce nothing at all?

```
apt-cache search build-essential
```

---

### Post by Ramthebuffs on 2008-02-11
Theres no errors @ all.  Build essential is newest etc.  The only error I get is when I run this

> sudo apt-get install gcc-cpp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-cpp


---

### Post by taurus on 2008-02-11
> **Ramthebuffs said:**
> Theres no errors @ all.  Build essential is newest etc.  The only error I get is when I run this

When you install build-essential package, you have installed gcc/cpp or whatever C compiler on your machine.  So, no need to install gcc-cpp since there is no such a package.

```
gcc -v
```

---

### Post by nemilar on 2008-02-11
If you're looking for the g++ package, it's named g++

build-essential will have installed that for you, and all the libraries necessary.

---

### Post by Ramthebuffs on 2008-02-11
Thanks for the help, I'm guessing these fall into the same category then? openssl-devel libgcrypt-devel

---

### Post by nemilar on 2008-02-11
I'm not sure off the top of my head if those are included in build-essential ; if you go to compile something and you get an error (probably during the ./configure stage) that you're missing a header file, just find it's -dev package and install it, and you should be all set.

---

