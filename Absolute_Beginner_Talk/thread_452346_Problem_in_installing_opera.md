---
title: "Problem in installing opera"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by SaitoSan on 2007-05-23
I installed opera once by downloading the .deb file from opera website. But, I found it to be sluggish and thus, I removed it. 

At that time, it wasn't available from the repository (i had updated the repository list) since I got nothing when I did apt search / show. But, it is now available, got a result when i did apt search / show. When i tried to install it (apt-get install), i got the following msg:

 > Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate


Any idea why?

---

### Post by taurus on 2007-05-23
Which release are you running and did you remember to update your list before you tried to install it?

```
sudo apt-get update
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by SaitoSan on 2007-05-23
I did run 
```
apt-get update
```
before i tried to install opera. I'm running Feisty bty. Here is my source list:

> 
## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


---

### Post by SaitoSan on 2007-05-23
Just to add, i got the following when i run ```
apt-cache show opera
```

> 
Package: opera
Status: deinstall ok config-files
Priority: optional
Section: non-free/web
Installed-Size: 12768
Maintainer: Opera Packaging Team <packager@opera.com>
Architecture: i386
Version: 9.20-20070409.6
Config-Version: 9.20-20070409.6
Replaces: opera-static
Provides: opera-static, www-browser
Depends: libc6 (>= 2.1.3), xlib6g (>= 3.3.6) | xlibs | libxmu6, libqt3-mt (>= 3.3.4), libstdc++6
Recommends: libaspell15
Suggests: flashplugin-nonfree | libflash-mozplugin
Conflicts: opera-static
Conffiles:
 /etc/opera6rc 097927636dbe6041119261b67b148879
 /etc/opera6rc.fixed 9025d2d3e4549b0bf2c3ee3a65c3749a
Description: The Opera Web Browser
 Welcome to the Opera Web browser. It is smaller, faster,
 customizable, powerful, yet user-friendly. Opera eliminates
 sluggish performance, HTML standard violations, desktop
 domination, and instability. This robust Web browser lets you
 navigate the Web at incredible speed and offers you the best
 Internet experience.
 The binaries were built on Debian using gcc-4.0.0.


---

### Post by Colonel Kilkenny on 2007-05-23
Just download from Opera.com or add Opera's own repo (check deb.opera.com) to your sources.list.
Canonical repo doesn't even have the latest version of Opera (9.21).

It should install it though. I've got no clue what's wrong but I wouldn't use commercial repo because personally I've had my problems with it in the past.

---

