---
title: "apt-get error"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-02-06
```

pete@pete-laptop:~$ sudo apt-get build-dep tcl8.4 tk8.4
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_source_Sources - open (2 No such file or directory)
pete@pete-laptop:~$

```


after i try and do a "sudo apt-get build-dep xyz"  ... xyz being any program .. 

i've tried apt-get update and apt-get clean , but no use :(

any ideas
?

---

### Post by bodhi.zazen on 2007-02-06
What does your /etc/apt/soruces.list look like ?

---

### Post by PetePete on 2007-02-06
```

pete@pete-laptop:~$ cat /etc/apt/sources.list

deb http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy multiverse
#AUTOMATIX REPOS END

#easycam
deb http://blognux.free.fr/debian unstable main

# Skype packages
# deb http://download.skype.com/linux/repos/debian/ stable non-free

#kde 3.5.6
# deb http://kubuntu.org/packages/kde-356 edgy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.6/kubuntu edgy main

# E17 repository "edevelop.org"
# deb http://edevelop.org/pkg-e/ubuntu edgy e17
# deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

```

---

### Post by doobit on 2007-02-06
You don't have 
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main source open

---

### Post by PetePete on 2007-02-06
thanks ... works now

---

### Post by PetePete on 2007-02-06
ok i lied... it doesn't work

but if i comment out the lines ...
     deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
     deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

it does work ??????????

---

