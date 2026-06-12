---
title: "Help with my errors"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by alleykat on 2006-09-29
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 1s (5B/s)
Reading package lists... Done
Merging available information
Replacing available packages info, using /var/cache/apt/available.
Information about 18874 package(s) was updated.
running dpkg --pending --configure ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster

dpkg --configure returned error exit status 1.
Press <enter> to continue.




What does all this mean about the clvm, redhat-cluster and system-config and how do I fix it? I have been looking around and still no luck getting it fixed. Thanks

---

### Post by dmizer on 2006-09-29
try using aptitude instead, it will offer solutions.

what are you trying to install?
did you do an update before trying to install software?

if you reboot your machine regularly, you'll need to update your package lists before installing software like so:
```
sudo aptitude update
```
that might correct all of your problems.

---

### Post by RU-In? on 2006-10-03
After several tries (on/off for 4 days) at fixing this problem that I too, HAD...I finally figured a fix...I am new to linux so you will have to forgive me, I searched, and searched until I finally came up with this combo...this will solve your problem...double check me first with a few searches on your part.

first back up your source file...just in case, then find the link,

[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

in this forum for a clean sources.list file, and use it. then do the...

    $ sudo apt-get update

then...

1.  $ sudo apt-get remove redhat-cluster-suite -f --purge

this will prompt to you that it is going to remove (maybe not in this order), 

  '*clvm* *redhat-cluster-suite* *system-config-suite*'

go ahead and do that...the result will be that clvm is left over... then do these...

2. $sudo rm /etc/init.d/clvm
3. $sudo apt-get remove clvm -f --purge

this will finally remove clvm :D

I'm probably going to update what installs and what not now, trying to keep my system clean and healthy too...

still lovin ubuntu, way better than those old leaky windows!

---

### Post by alleykat on 2006-10-06
Thank you for the replies and help. I ended up re-installing Ubuntu since I did not have anything to lose by doing it that way.:)

---

### Post by siucdude on 2007-01-05
Works like a charm 

Thank You

---

