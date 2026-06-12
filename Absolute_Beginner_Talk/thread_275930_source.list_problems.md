---
title: "source.list problems"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-10-12
I have spent about 3 hours on this problem, but don't seem to be getting anywhere.  I have read through several posts on this and have used 3 different suggested source lists, but still receive error messages.  Now I am wondering if the problem is something else.

Here is the error message.
```

gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Fetched 1288kB in 40s (31.5kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

The latest 3 source lists that I have used starting from the latest are.

1. found [here]("http://www.ubuntuforums.org/showthread.php?t=169088&highlight=sources.list+breezy")
```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```
2. found [here ]("http://www.ubuntulinux.nl/source-o-matic")
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt breezy main

# Bleeding edge wine packages (sources)
# deb-src http://wine.budgetdedicated.com/apt breezy main

# OpenOffice.org 2 final packages (packages)
deb http://people.ubuntu.com/~doko/OOo2/ ./

```
and three from my home computer.  (For some reason it works there.)
```

##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

I was getting W: error codes and E: error codes when ever I tried to update or upgrade.  

Any help is appreciated.

---

### Post by bountonw on 2006-10-12
I found a 4th list [here]("http://www.psychocats.net/ubuntu/sources")

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

Still receive the same error message.
```
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Fetched 1576kB in 1m12s (21.8kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
](*,)

---

### Post by Fully216 on 2006-10-12
The problem is not with the repo, because I was able to browse it fine right now using firefox.  

user utab reported similar errors way back in March.

I would try to remove and replace gzip + dependencies via synaptic package manager (reinstall option).

---

### Post by bountonw on 2006-10-12
I uninstalled and re-installed gzip and still get the following error message when updating.

```
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Fetched 76.3kB in 52s (1466B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Archmage on 2006-10-26
Change the http entry in the source.list to ftp and retry.

---

