---
title: "Update error"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by stupidkid on 2007-06-05
I always get this error whenever i sync

```
Get:17 http://us.archive.ubuntu.com feisty/universe Packages [4912kB]     
99% [17 Packages gzip 0] [16 Release 11213/32.4kB 34%]               40.6kB/s 0s
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/universe Packages                       
  Sub-process gzip returned an error code (1)
```

Here's my sources.lst

```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

## BERYL!!!!
deb http://ubuntu.beryl-project.org feisty main

```

Any help is appreciated, thanks.

---

### Post by esavato on 2007-06-06
Apparently, other people have had the same or similar issues due to problems with mirrors in say Austria, England etc...  some people switched to ftp instead of http, others changed the mirrors they were using.  This seems to be a debian / apt thing rather than specific to ubuntu...

Here is one place I found comment...
[http://ubuntuforums.org/archive/index.php/t-9944.html](http://ubuntuforums.org/archive/index.php/t-9944.html)

---

