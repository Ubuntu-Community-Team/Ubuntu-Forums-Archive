---
title: "install Tightvnc"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by shanky1972 on 2007-06-13
Hey folks, 
new to linux. 
trying to install tightvnc and getting this. how do I get these dependencies installed.

rpm -ivh tightvnc-1.3.9-1.i386.rpm
error: Failed dependencies:
        libICE.so.6 is needed by tightvnc-1.3.9-1.i386
        libSM.so.6 is needed by tightvnc-1.3.9-1.i386
        libX11.so.6 is needed by tightvnc-1.3.9-1.i386
        libXaw.so.7 is needed by tightvnc-1.3.9-1.i386
        libXext.so.6 is needed by tightvnc-1.3.9-1.i386
        libXmu.so.6 is needed by tightvnc-1.3.9-1.i386
        libXpm.so.4 is needed by tightvnc-1.3.9-1.i386
        libXt.so.6 is needed by tightvnc-1.3.9-1.i386
        libc.so.6 is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.0) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.1) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.2) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.3.4) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.4) is needed by tightvnc-1.3.9-1.i386
        libjpeg.so.62 is needed by tightvnc-1.3.9-1.i386
        libz.so.1 is needed by tightvnc-1.3.9-1.i386
        rtld(GNU_HASH) is needed by tightvnc-1.3.9-1.i386

---

### Post by lazyart on 2007-06-13
what linux are you running... doesnt look like ubuntu because it doesn't use the rpm system.

---

### Post by shanky1972 on 2007-06-14
hi Lazyart
I'm runnnig Ubuntu and I was able to download and install rpm. these are teh commands I did

 rpm
The program 'rpm' is currently not installed.  You can install it by typing:
apt-get install rpm
-su: rpm: command not found
root@sxv-computer:~# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libbeecrypt6 librpm4
Suggested packages:
  alien
The following NEW packages will be installed:
  libbeecrypt6 librpm4 rpm
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 1701kB of archives.
After unpacking 5972kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libbeecrypt6 4.1.2-6build1 [108kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main librpm4 4.4.1-14build1 [990kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main rpm 4.4.1-14build1 [603kB]      
Fetched 1701kB in 8s (209kB/s)                                                 
Selecting previously deselected package libbeecrypt6.
(Reading database ... 110074 files and directories currently installed.)
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-6build1_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-14build1_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-14build1_i386.deb) ...
Setting up libbeecrypt6 (4.1.2-6build1) ...

Setting up librpm4 (4.4.1-14build1) ...

Setting up rpm (4.4.1-14build1) ...

root@sxv-computer:~# rpm
RPM version 4.4.1
Copyright (C) 1998-2002 - Red Hat, Inc.
This program may be freely redistributed under the terms of the GNU GPL

Usage: rpm [-aKfgpWHqV] [-aKfgpWHqVcdils] [-aKfgpWHqVcdilsaKfgpWHqV] [-aKfgpWHqVcdilsaKfgpWHqV] [-aKfgpWHqVcdilsaKfgpWHqV] [-aKfgpWHqVcdilsaKfgpWHqVK] [-aKfgpWHqVcdilsaKfgpWHqVK] [-aKfgpWHqVcdilsaKfgpWHqVKi] [-aKfgpWHqVcdilsaKfgpWHqVKiv] [-aKfgpWHqVcdilsaKfgpWHqVKiv] [-aKfgpWHqVcdilsaKfgpWHqVKiv?] [-a|--all] [-f|--file] [-g|--group]
        [-p|--package] [-W|--ftswalk] [--pkgid] [--hdrid] [--fileid]
        [--specfile] [--triggeredby] [--whatrequires] [--whatprovides]
        [--nomanifest] [-c|--configfiles] [-d|--docfiles] [--dump] [-l|--list]
        [--queryformat=QUERYFORMAT] [-s|--state] [--nomd5] [--nofiles]
        [--nodeps] [--noscript] [--comfollow] [--logical] [--nochdir]
        [--nostat] [--physical] [--seedot] [--xdev] [--whiteout]
        [--addsign] [-K|--checksig] [--delsign] [--import] [--resign]
        [--nodigest] [--nosignature] [--initdb] [--rebuilddb] [--aid]
        [--allfiles] [--allmatches] [--badreloc] [-e|--erase <package>+]
        [--excludedocs] [--excludepath=<path>] [--fileconflicts] [--force]
        [-F|--freshen <packagefile>+] [-h|--hash] [--ignorearch] [--ignoreos]
        [--ignoresize] [-i|--install] [--justdb] [--nodeps] [--nomd5]
        [--nocontexts] [--noorder] [--nosuggest] [--noscripts]
        [--notriggers] [--oldpackage] [--percent] [--prefix=<dir>]
        [--relocate=<old>=<new>] [--repackage] [--replacefiles]
        [--replacepkgs] [--test] [-U|--upgrade <packagefile>+]
        [-D|--define 'MACRO EXPR'] [-E|--eval 'EXPR'] [--macros=<FILE:...>]
        [--nodigest] [--nosignature] [--rcfile=<FILE:...>] [-r|--root ROOT]
        [--querytags] [--showrc] [--quiet] [-v|--verbose] [--version]
        [-?|--help] [--usage] [--scripts] [--setperms] [--setugids]
        [--conflicts] [--obsoletes] [--provides] [--requires] [--info]
        [--changelog] [--triggers] [--last] [--filesbypkg] [--fileclass]
        [--filecolor] [--filecontext] [--fscontext] [--recontext]
        [--fileprovide] [--filerequire] [--redhatprovides]
        [--redhatrequires] [--buildpolicy=<policy>] [--with=<option>]
        [--without=<option>]

then the commands I mentioned earlier where I tried to install the tightvnc. So should I get the tar pkg from tightvnc?


root@sxv-computer:/home/sxv/Desktop# rpm -ivh tightvnc-1.3.9-1.i386.rpm
error: Failed dependencies:
        libICE.so.6 is needed by tightvnc-1.3.9-1.i386
        libSM.so.6 is needed by tightvnc-1.3.9-1.i386
        libX11.so.6 is needed by tightvnc-1.3.9-1.i386
        libXaw.so.7 is needed by tightvnc-1.3.9-1.i386
        libXext.so.6 is needed by tightvnc-1.3.9-1.i386
        libXmu.so.6 is needed by tightvnc-1.3.9-1.i386
        libXpm.so.4 is needed by tightvnc-1.3.9-1.i386
        libXt.so.6 is needed by tightvnc-1.3.9-1.i386
        libc.so.6 is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.0) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.1) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.2) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.3.4) is needed by tightvnc-1.3.9-1.i386
        libc.so.6(GLIBC_2.4) is needed by tightvnc-1.3.9-1.i386
        libjpeg.so.62 is needed by tightvnc-1.3.9-1.i386
        libz.so.1 is needed by tightvnc-1.3.9-1.i386
        rtld(GNU_HASH) is needed by tightvnc-1.3.9-1.i386
root@sxv-computer:/home/sxv/Desktop#

---

### Post by michael37 on 2007-10-24
Simplest solution for viewer.

Download tightvnc viewer rpm.
rpm2cpio tightvnc-1.3.9-1.i386.rpm | cpio -id
cp usr/bin/vncviewer /usr/local/bin
rm /etc/alternatives/vncviewer
ln -s /usr/local/bin/vncviewer /etc/alternatives/vncviewer

Start vncviewer

Enjoy.

---

