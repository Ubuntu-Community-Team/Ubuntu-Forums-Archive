---
title: "No updates Dapper 6.06LT"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-23
Hi,

I felt that I needed to add this. I have seen a few other threads concerning this and was not sure that it applied and that is why I started a new one.

I have read several threads on updating problems and have been unable to solve the problem so I will give as much information as I can>

1. Unable to do software updates, error message as follows:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb)
  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb)
  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb)
  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb)
  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb)
](*,) 
2. When I open add/remove I do not get the updating dialog.
3. When I go to synaptic and hit reload I get:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)
[http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
](*,) 

I then went to this web site and followed directions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

When I follow directions I can never get to finish the trouble shooting portion because I get:

blank@tux:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
blank@tux:~$ gksudo gedit /etc/apt/sources.list

(gedit:8057): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
blank@tux:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
99% [Connecting to packages.freecontrib.org (1.0.0.0)] [Connecting to us.archive

I always end up with 1 of whatever files (1-of whatever) and it always hangs on the last file.

My sources list is:

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
](*,) 

One last comment that may help to solve this. When I was having internet problems and came here I was told that my hardware could be in conflict and I went here: ([https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4))
and it solved my connection problem, not sure if this is applicable or not but I am trying to give as much info as I can.
](*,) 

Thanking You in advance for your help
Carolyn

---

### Post by helmeteye on 2006-11-23
I am having the exact same problem.

---

### Post by Carolyn62 on 2006-11-23
Hi,

> I am having the exact same problem.

Wellllllll, If your having the same problem then it is a sure bet others are having the same problem especially with some 25 views which may be telling us that we could have a unique problem and there may be no answer at this time, so maybe we need to rephrase our question to:

Does anyone have a copy of a **[COLOR="Red"]working[/COLOR]**[COLOR="Black"][/COLOR] source list or know where to get one for Ubuntu 6.06LT, using IPv4 that you would be willing to post here or anywhere else????:mrgreen: 

Thank You,
Carolyn

---

### Post by confused57 on 2006-11-23
Maybe you can get a sources.list here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

