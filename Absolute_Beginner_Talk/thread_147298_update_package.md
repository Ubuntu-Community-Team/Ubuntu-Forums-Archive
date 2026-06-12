---
title: "update package"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by rishi.lalseta on 2006-03-19
Hello

i am a newbei with linux systems.Could someone please guide me through..PLEASE PLEASE.

I have installed Ubuntu linux,then did the configuration settings to connect to the internet----which works perfectly.

when i click on to update SYSTEM -> ADMINISTRATION - >SYNAPTIC PACKAGE MANAGER,it produces these error:
Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


ERROR 2

Fair enough i still click on RELOAD and these errors appears

ttp://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz: 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) 407 Proxy Authentication Required [IP: 10.6.2.61 8080]





ERROR 3

i thought of anothre way was using the command line
when i typed
sudo apt-get update(Below it shows the error)
0% [Connecting to archive.ubuntu.com (82.211.81.182)]



i checked several website for the source.list (/etc/apt/source.list),belowis the source.list which i got from the website,which doesn't work



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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricteddeb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe




i also have the previous source.list which also doesn't work




deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


Thanks

---

### Post by rishi.lalseta on 2006-03-19
I also tried pinging the address and it all works too well..

I can also conect to the internet without any hesitation.

Is there any network settings i need to do or anything else,

THanks

RIshi

---

