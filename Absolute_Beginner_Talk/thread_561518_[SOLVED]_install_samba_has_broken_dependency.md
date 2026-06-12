---
title: "[SOLVED] install samba has broken dependency"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by bren on 2007-09-27
I installed LAMP

then got rid of it.... SAMBA now seems to have a problem

I uninstalled it so I could install fresh and COULD NT install!

```
bren@bren-laptop:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  samba: Depends: samba-common (= 3.0.24-2ubuntu1) but 3.0.24-2ubuntu1.2 is to be installed
E: Broken packages
```

same error if i use synaptic

any ideas?

bren

---

### Post by perce on 2007-09-27
Maybe you mixed repositories, or you installed some package from he wrong repository? have you tried to run a apt-get update, and then try to install the package? if you still have the same problem after that, please post your file /etc/apt/source.list here.

---

### Post by bren on 2007-09-28
thanks perce

will try update and report back (tonight)

bren

---

### Post by bren on 2007-09-28
hi perce

i ran

sudo apt-get update
and then tried again but still the same result as post #1 above

here is my sources.list

> $ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## libpam-keyring only available in edgy backport apparently....
## commented out again after install
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## Beryl repo
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
# deb-src [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main


# Eye candy repo
# Installed to try kiba dock
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
#deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 
#deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

## vmware repo
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main



any ideas?
note the kiba and beryl refs are old - did fresh install of feisty since playing about with them and they have always been commented out since!

regards
bren

---

### Post by perce on 2007-09-28
The source.list looks correct. try the command sudo apt-get install -f

Btw, did you use sudo with apt-get update?

---

### Post by bren on 2007-09-30
yes to the update question 

solved this one actually by installing 

sudo apt-get install samba-common first

bren

---

