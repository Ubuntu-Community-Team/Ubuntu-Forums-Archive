---
title: "[SOLVED] Strange Pbuilder Error"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-12-07
Im getting a weird error in Pbuilder trying to build a package. It might be the packages fault (Im just learning) but im not sure.

This is what i get from Pbuilder:

```
bobbo@tiger:~/ckkern-0.1.3-1$ sudo pbuilder build ../*.dsc
W: /home/bobbo/.pbuilderrc does not exist
I: using fakeroot in build.
Current time: Fri Dec  7 15:40:31 GMT 2007
pbuilder-time-stamp: 1197042031
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
 -> Attempting to parse the build-deps 
 -> Installing 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 -> Finished parsing the build-deps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives.
After unpacking 442kB of additional disk space will be used.
Selecting previously deselected package fakeroot.
(Reading database ... 12297 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Setting up fakeroot (1.7.1ubuntu1) ...

Copying back the cached apt archive contents
Copying source file
    -> copying [../ckkern_0.1.3-1.dsc]
    -> copying [../ckkern_0.1.3-1.tar.gz]
Extracting source
dpkg-source: warning: extracting unsigned source package (./ckkern_0.1.3-1.dsc)
dpkg-source: extracting ckkern in ckkern-0.1.3
dpkg-source: unpacking ckkern_0.1.3-1.tar.gz
 -> Building the package
dpkg-buildpackage: source package is ckkern
dpkg-buildpackage: source version is 0.1.3-1
dpkg-buildpackage: source changed by David Futcher <bobbocanfly@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.1.3-1
 fakeroot debian/rules clean
make: Nothing to be done for `clean'.
 dpkg-source -b ckkern-0.1.3
dpkg-source: building ckkern in ckkern_0.1.3-1.tar.gz
dpkg-source: building ckkern in ckkern_0.1.3-1.dsc
 debian/rules build
make: Nothing to be done for `build'.
 fakeroot debian/rules binary
sh install.sh
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
[sudo] password for pbuilder:

```

I havent specified a password for Pbuilder and my (and therefore roots) password doesnt work.

What do i do?

---

### Post by bobbocanfly on 2007-12-07
Sorry, was a problem with my package. Fixed now.

---

