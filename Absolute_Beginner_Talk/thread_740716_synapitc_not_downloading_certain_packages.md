---
title: "synapitc not downloading certain packages"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2008-03-31
I have this error when I reload synaptic:

```
W: GPG error: http://ftp.debian.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
```

Also downoading certain servers also does not work, heres my repository list
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ftp.debian.org sarge main
```

I mucked around a little bit before to install a gutsy program on feisty, how can I save myself?

---

### Post by Oldsoldier2003 on 2008-03-31
> **Belliinator said:**
> I have this error when I reload synaptic:

```
W: GPG error: http://ftp.debian.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
```

Also downoading certain servers also does not work, heres my repository list
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ftp.debian.org sarge main
```

I mucked around a little bit before to install a gutsy program on feisty, how can I save myself?

usually when you install from a repo that is from a higher version than you are running you are hosed as it injects incompatibilities to your system. What I would do to be honest is back up my data and install gutsy or hardy. In the future if you must have a program version that is not available in your supported repo due to the repo freeze at release, just compile the program from source.

---

### Post by Belliinator on 2008-03-31
Ok, I was just doing what the howto(different website) said. In future I will compile from source.

I dont have the bandwidth to upgrade yet. is their any other solotion?
Apart from downloading every inconsistent file individually.

---

### Post by wormser on 2008-03-31
> **Belliinator said:**
> Ok, I was just doing what the howto(different website) said. In future I will compile from source.

I dont have the bandwidth to upgrade yet. is their any other solotion?
Apart from downloading every inconsistent file individually.

You just need to use the repository that matches your version.  A Feisty install needs a Feisty repository.  There is no need to compile from source if it is in a repository.

---

