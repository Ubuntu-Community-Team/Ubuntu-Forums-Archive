---
title: "Cannot upgrade to gutsy"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2007-11-14
I am not able to upgrade my fiesty fawn to gutsy gibbon i get the following error

"Authenticating the upgrade failed. There may be a problem with the network or with the server. "

Wen i try gksu "update-manager" -c -d, i get following errors

```

$ gksu "update-manager -c -d"

warning: could not initiate dbus
extracting '/tmp/tmpaGSzbd/gutsy.tar.gz'
authenticate '/tmp/tmpaGSzbd/gutsy.tar.gz' against '/tmp/tmpaGSzbd/gutsy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpaGSzbd'

gpg: verify signatures failed: eof


```

Also wnever i try to update the sources


W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: The following signatures were invalid: NODATA 2


Cant figure out how to get over this problem, so someone plz help me out

---

### Post by taurus on 2007-11-14
Can you post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by rsambuca on 2007-11-14
If you are trying to upgrade and had all of the proposed and backport repos, you may run into problems.  Post your 

cat /etc/apt/sources.list

---

### Post by infin?ty on 2007-11-14
My /etc/apt/sources.list
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe

```

---

### Post by infin?ty on 2007-11-15
I am still unable to figure wat the problem is :( can someone plz help me out.

---

