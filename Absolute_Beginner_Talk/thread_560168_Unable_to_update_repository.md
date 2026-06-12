---
title: "Unable to update repository"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2007-09-26
Hi,

I'm unable to update my repository. Whenever I try to do so, the follow error message is thrown:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

As a result, I'm cannot install basic things like Multimedia Codecs etc. Help me out!

My repository:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://packages.medibuntu.org/ feisty free non-free
# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu feisty-commercial main


deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by mysticmatrix on 2007-09-26
Wow Another Automatix user :)
Well for starters try changing the server to the main servers.
This can be done by opening System-->Administration--> Software Sources.

The problem is Automatix repo's are conflicting with normal repositaries.
So comment out last few lines.
```

#AUTOMATIX REPOS START
#deb http://archive.canonical.com/ubuntu feisty-commercial main
#deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
#deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by rkakkar on 2007-09-26
Worked! And removed Automatix :)

---

