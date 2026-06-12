---
title: "sources.lst help"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-02
Fetched 54.8kB in 1m28s (619B/s)
Failed to fetch [http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/binary-i386/Packages.gz](http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.compiz.net/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.compiz.net/dists/edgy/main-edgy/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A947CF51609B551
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@r00t-server:~# 


please help . what i do now :(

---

### Post by taurus on 2006-12-02
I assume the first two sites are down and somehow you have a bunch of duplicate entries in /etc/apt/sources.list!!!  So, comment out by placing a # in front of those two lines, [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) & [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/), and run it again or post your /etc/apt/sources.list here...

```
cat /etc/apt/sources.list
```

---

### Post by pavel_kbc on 2006-12-02
here is my scources.list 


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties
deb [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://na.archive.ubuntu.com/ubuntu/](http://na.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

#Beryl
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free

---

### Post by taurus on 2006-12-02
Put a # in front of these two lines in your /etc/apt/sources.list...

```

#deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy
#deb http://ubuntu.compiz.net/ edgy main-edgy

```

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by pavel_kbc on 2006-12-02
thank you i fixed it.

---

