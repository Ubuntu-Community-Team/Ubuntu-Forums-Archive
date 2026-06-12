---
title: "Problem updating Edgy --&gt; Fiesty."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-10-17
```
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://soulmachine.net/breezy/unstable/Packages.gz 404 Not Found

```

I'm doing this so I can use the UpdateManager to update to Gutsy when it comes out tomorrow -  help :confused:

---

### Post by Seisen on 2007-10-17
Post your source list

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by auraithx on 2007-10-17
```

deb http://im.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://im.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://im.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://im.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://im.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://im.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://im.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://im.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
deb http://soulmachine.net/breezy/ unstable/
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

```

---

### Post by Seisen on 2007-10-17
Delete these repositories since you wont' need them any more

```
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://soulmachine.net/breezy/ unstable/
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
``` and I would comment out these two lines so they dont' get messed up.

```
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
``` just add "#" in front of the line.

Then reload your source list and the dist-upgrade should work fine.

---

### Post by auraithx on 2007-10-17
Thanks, that fixed it.

---

