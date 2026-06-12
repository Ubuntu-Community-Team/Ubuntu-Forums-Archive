---
title: "trouble"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by dmm1983 on 2007-02-11
i am having problems with updating here it is  my sources list
deb [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper main restricted multiverse universe
deb-src [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper main restricted multiverse universe
deb [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-updates main restricted multiverse universe
deb-src [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-updates main restricted multiverse universe
deb [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-security main restricted multiverse universe
deb-src [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-security main restricted multiverse universe
deb [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-backports main restricted multiverse universe
deb-src [http://mirror.optusnet.com.au/ubuntu/](http://mirror.optusnet.com.au/ubuntu/) dapper-backports main restricted multiverse universe
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

and here is the message i get after updating 

Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper Release.gpg
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates Release.gpg
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security Release.gpg
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports Release.gpg
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper Release
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates Release
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security Release
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports Release
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/main Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/restricted Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/multiverse Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/universe Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/main Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/restricted Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/multiverse Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/universe Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/main Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/restricted Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/multiverse Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/universe Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/main Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/restricted Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/multiverse Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/universe Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/main Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/restricted Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/multiverse Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/universe Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/main Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/restricted Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/multiverse Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/universe Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/main Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/restricted Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/multiverse Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/universe Packages
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/main Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/restricted Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/multiverse Sources
Ign [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/universe Sources
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/main Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/restricted Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/multiverse Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/universe Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/main Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/restricted Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/multiverse Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper/universe Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/main Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/restricted Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/multiverse Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/universe Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/main Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/restricted Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/multiverse Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-updates/universe Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/main Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/restricted Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/multiverse Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/universe Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/main Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/restricted Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/multiverse Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-security/universe Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/main Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/restricted Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/multiverse Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/universe Packages
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/main Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/restricted Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/multiverse Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://mirror.optusnet.com.au](http://mirror.optusnet.com.au) dapper-backports/universe Sources
  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/Release.gpg](http://mirror.optusnet.com.au/ubuntu/dists/dapper/Release.gpg)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/Release.gpg](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/Release.gpg](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/Release.gpg](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/main/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/main/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/restricted/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/restricted/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper/universe/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper/universe/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/main/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/main/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://mirror.optusnet.com.au/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Could not connect to mirror.optusnet.com.au:80 (211.29.132.173). - connect (113 No route to host)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (88.191.33.6). - connect (113 No route to host)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Kateikyoushi on 2007-02-11
Something might be wrong with that mirror.
Try the main server. Can change to it in System > Administration > Software sources and change the download server in the drop down box.

---

### Post by dmm1983 on 2007-02-11
did not work

---

### Post by dmm1983 on 2007-02-15
i reloaded it and it works

---

