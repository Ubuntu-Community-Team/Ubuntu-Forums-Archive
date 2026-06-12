---
title: "Output from Apt-get update."
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Jjohn on 2006-04-18
I am a bit concerned about the error messages in Apt-get update.
This is the output:


john@itchy:~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Err [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
  404 Not Found
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Get:4 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages
Get:5 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages
  404 Not Found [IP: 203.16.234.90 80]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages
  404 Not Found [IP: 203.16.234.90 80]
Get:6 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
99% [Packages gzip 0] [Query]                                       14.9kB/s 0s
gzip: stdin: unexpected end of file
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
  Sub-process gzip returned an error code (1)
99% [Working]                                                       14.9kB/s 0s
gzip: stdin: unexpected end of file
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
  Sub-process gzip returned an error code (1)
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Fetched 3B in 7s (0B/s)
Failed to fetch [http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found [IP: 203.16.234.90 80]
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 203.16.234.90 80]
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
I will include my sources list which is:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

## created by arnieopera



If any one can help me with this I would appreciatte.:-?

---

### Post by trent dillman on 2006-04-18
Looks to me like some of your repos are down. If this persists, try commenting out the offending repos from your sources.list

---

### Post by uteck on 2006-04-18
Try running it again and see if it connects to them all this time.  Depending on the server, they may refuse a conenction becaues it may have too many at the moment.

---

### Post by Jjohn on 2006-04-18
Many thanks folks,
                            I will try that to see what happens...:D

---

