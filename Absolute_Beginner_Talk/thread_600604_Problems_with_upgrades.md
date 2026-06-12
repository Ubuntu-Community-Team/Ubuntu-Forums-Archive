---
title: "Problems with upgrades"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by vvule on 2007-11-02
Hi everyone! 
For some time I have problems when I force the check for upgrades! When the process is finished, the Update Manager comes with the announcement

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

I`ve checked all sources in Software sources (main, universe, restricted, multiverse) and unchecked the installation CD as a source!

Also when I try to Update my Ubuntu to 7.10 via an Update Manager it comes out with:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

It seems to me that this two thing are somehow interconnected! Does anyone know how can I fix these  problems and finally upgrade to Gutsy!

Thanks  in advance

---

### Post by taurus on 2007-11-02
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by vvule on 2007-11-03
Here it is:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe #Added by software-properties

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

### Post by PmDematagoda on 2007-11-03
Try changing the location of the servers in Software Sources and see if that solves your problem.

---

### Post by vvule on 2007-11-03
I`ve just tried to change the location of server, but again it came out with similar announcement! What I have noticed is that during the download of packages information he "failed"  almost exclusivly on the package named "Translation_en_US" or something very similar to  this. And at the very end he jammed at one package (at 57% of it) waited for a while and than threw the announcement!

---

### Post by Maestro23 on 2007-11-03
Might try generating a new sources list and go from there.  Can be done with the link below.
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by vvule on 2007-11-03
Thanks Maestro23, I`ve change my sources list in a way recomended after following few steps on URL you gave!  There were no problems in Update Manager and right now I`am upgrading to 7.10 also via Update Manager, also apparently with no problem (so far)! 
But Update Manager still throw "failed" when it dowloads package information for a package Translate_en_US (or something like that),  does anyone know what the problem is?

---

### Post by Clickbg on 2007-11-03
What is the error message you get?

---

### Post by vvule on 2007-11-03
Acctually I don`t get error message, but when I look at the detalis during the download of the package information for all packages the status is "Done" or "Hit", but for this one (Translate_en_us - or something simillar) the status is "Failed"

---

