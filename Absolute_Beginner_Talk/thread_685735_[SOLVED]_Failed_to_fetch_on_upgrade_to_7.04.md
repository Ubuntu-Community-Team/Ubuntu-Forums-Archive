---
title: "[SOLVED] Failed to fetch on upgrade to 7.04"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-02
K. Update Manager>"New distro '7.04'">Upgrade>"Error during update"

> Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found

Also 

```
sudo gedit /etc/apt/sources.list
```

isn't opening anything.

instead I just type ```
gedit /etc/apt/sources.list
```

it opens the sources.list in notepad form.

here's what that says though. 

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
deb http://mirror.ubuntulinux.nl edgy-seveas all
```

(Keep in mind my original question is that I'm failing to fetch. The other problem is secondary.)

Any ideas why it's failing to fetch?

---

### Post by ssharps711 on 2008-02-02
I'm guessing the server is down? IDK man.:confused:

---

### Post by ssharps711 on 2008-02-02
K nm. I put # before.

```
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
```

and

```
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
```

---

