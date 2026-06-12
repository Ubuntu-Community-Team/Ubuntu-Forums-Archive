---
title: "cant download any repositorys"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by YearZirO on 2008-01-03
anyone else have this problem?? seems very odd did a fresh install of 7.10 updated it to get it up to date change from GNOME to KDE 3.5.8 now when i try to use the Add/Remove Applications i get these errors that not one single mirror is up so ive posted everything i know hopefully someone can tell me what if anything i did wrong and yes my connection is working fine  



[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


this is the config of my /etc/apt/sources.list 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by spiderbatdad on 2008-01-03
ive seen this error when connected through a proxy. try googling "localhost:4001" and "anon-proxy"

---

### Post by YearZirO on 2008-01-03
thanks but i still get the error

---

