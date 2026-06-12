---
title: "Program ADD/REMOVE error"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by niraj1972 on 2007-09-25
Hi friends,

I have try update from breezy to drapper.. some body in some forum asked me to do it by changing all letter in sources.list file of breezy to drapper.. it worked well and update took almost 600 mb download and 4hours around.. but now when I try to add or remove program.. i get below error

[COLOR="Red"]
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]



Also I am copying my sources.list.. below.. any help would be greatly appreciated..


[[COLOR="Sienna"]COLOR="Red"]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) dapper free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-extras main restricted universe multiverse

## created by arnieplanetremoved
[/COLOR]


Also i tried to do as told in "'sudo apt-get update'." with below result..


[COLOR="DarkRed"]gtech@ubuntu:~$ sudo apt-get update
Password:
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
  The server refused the connection and said: There are too many connected users, please try later.
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/main Packages
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/multiverse Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/main Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/restricted Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/universe Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) dapper-extras/multiverse Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:5 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch Release
Err [http://deb.opera.com](http://deb.opera.com) etch Release

Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Get:6 [http://deb.opera.com](http://deb.opera.com) etch Release [866B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 1059B in 2m11s (8B/s)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/Release.gpg](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/Release.gpg) The server refused the connection and said: There are too many connected users, please try later.
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/dapper-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/dapper-extras/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/dapper-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/dapper-extras/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/dapper-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/dapper-extras/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/dapper-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/dapper-extras/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR][/COLOR]

---

### Post by LaRoza on 2007-09-25
Use what it suggested,
```

sudo apt-get update

```

Hope it helps!

---

### Post by overdrank on 2007-09-25
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
### extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ dapper free non-free

[COLOR="Red"]#deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ dapper free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ dapper free non-free[/COLOR]

[COLOR="Red"]#deb http://deb.opera.com/opera/ etch non-free[/COLOR]
## deb http://seveas.ubuntulinux.nl/ dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
[COLOR="Red"]#deb http://ubuntu-backports.mirrormax.net/ dapper-extras main restricted universe [/COLOR]multiverse
```
Hi you may try and comment out the ones I have highlighted and try again to update.
As you can see the op did run the update suggested.

---

