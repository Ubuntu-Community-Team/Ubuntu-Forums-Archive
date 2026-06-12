---
title: "Installing Tovid"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-31
Cheers,

I am trying to install tovid by following the instructions given at 
[http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu](http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu)

Although I have installed tovid without problems I have encountered a problem 
installing the dependencies:```
$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

$ sudo apt-get install mjpegtools
Reading package lists... Done
Building dependency tree... Done
Package mjpegtools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mjpegtools has no installation candidate

$ sudo apt-get install mencoder
Reading package lists... Done
Building dependency tree... Done
Package mencoder is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mencoder has no installation candidate
```I have tried enabling the multiverse in Synaptic however when I click on the Refresh button I get this error```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
```Any ideas on what I should do next?

TIA

---

### Post by xyz on 2006-10-31
I've got all the dependencies you stated in Synaptic.
Did you enable universe and multiverse repositories?

---

### Post by delphiguy on 2006-10-31
I did... I even deleted all of the contents of my repository and then added them in synaptic.  Heres the contents of my sources.list now.

```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
```however if I run sudo apt-get update I get this error at the bottom```
$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
99% [7 Sources gzip 0]                                                                                                                            21.0kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
99% [8 Packages gzip 0]                                                                                                                           21.0kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 8B in 7s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by delphiguy on 2006-10-31
Something weird happend here.  I was running Automatix Bleeder and then when I closed it, it asked me whether I want to restore my orignal sources.list and when I did the packages seems to be there now and I am now able to install those packages and now am using/learnig tovid.

---

