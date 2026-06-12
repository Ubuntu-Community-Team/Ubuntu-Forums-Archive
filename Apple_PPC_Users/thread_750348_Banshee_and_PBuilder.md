---
title: "Banshee and PBuilder"
date: 2008-04-09
forum: Apple PPC Users
---

### Post by ceagan on 2008-04-09
I'm excited about the new version of Banshee and would like to try it out on my PowerPC. Unfortunately, PPA's do not currently provide packages for PPC so I figured I would build it myself using pbuilder.

The PPA is at [https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive)

So I set up the environment for PBuilder and everything seems cool there.  (I followed the instructions at [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)) However, when I run the build command I get this:

```
ceagan@platinum:~/Projects/PBuilder$ sudo pbuilder --build banshee_0.98.2+svn3648-0ubuntu1~hardy1.dsc 
I: using fakeroot in build.
Current time: Wed Apr  9 12:21:54 EDT 2008
pbuilder-time-stamp: 1207758114
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
This package is uninstallable
Dependency is not satisfiable: libmono-zeroconf1.0-cil
E: pbuilder-satisfydepends failed.
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//7325 and its subdirectories
ceagan@platinum:~/Projects/PBuilder$ 

```

This happens to be using the pbuilder-satisfydepends-gdebi, but a similar error occurs using the other satisfydepends options. My ~/.pbuilderrc looks like this:

```
COMPONENTS="main restricted universe multiverse"

PBUILDERSATISFYDEPENDSCMD="/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi"

```

Has anyone else been able to build these debs or know why they won't build on my machine?

---

