---
title: "[SOLVED] KDE4 problem after automatix install"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-09-13
I installed KDE4 the other day. I didn't see a difference much but I ussume it was working fine and I had no problems. Last night i decided to try Automatix to see what it has and now I can't update and upgrade my PC. I get the followg errors when i try to:

[INDENT]Fetched 4608B in 59s (78B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
lunamystry@michelle:~$    [/INDENT]

and 

[INDENT]lunamystry@michelle:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kde4base: Depends: kdepimlibs5 but it is not installed
            Depends: kdepimlibs5 (>= 3.93.0-0ubuntu1~feisty1) but it is not installed
            Depends: kde4base-data (= 3.93.0-0ubuntu1~feisty2) but 3.80.3-0ubuntu5 is installed
  kde4base-dev: Depends: kdepimlibs5-dev but it is not installed
  kdelibs5: Depends: kdelibs5-data (= 3.93.0-0ubuntu1~feisty1) but it is not installed
E: Unmet dependencies. Try using -f.
lunamystry@michelle:~$  [/INDENT]

and 

[INDENT]lunamystry@michelle:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  graphicsmagick sun-java6-plugin python-pymad libgraphicsmagick1-dev
  kde4libs-data python-mutagen python-pysqlite2 libgraphics-magick-perl
  libgraphicsmagick++1 kdepimlibs4 kdepimlibs4-dev libgraphicsmagick++1-dev
  libgraphicsmagick1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde4base-data kdelibs5-data kdepimlibs5 kdepimlibs5-dev
The following NEW packages will be installed:
  kdelibs5-data kdepimlibs5 kdepimlibs5-dev
The following packages will be upgraded:
  kde4base-data
1 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
5 not fully installed or removed.
Need to get 0B/84.2MB of archives.
After unpacking 130MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208468 files and directories currently installed.)
Unpacking kdelibs5-data (from .../kdelibs5-data_3.93.0-0ubuntu1~feisty1_all.deb) ...
Replacing files in old package kde4libs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_3.93.0-0ubuntu1~feisty1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/apps/cmake/modules/FindGObject.cmake', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdepimlibs5 (from .../kdepimlibs5_3.93.0-0ubuntu1~feisty2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdepimlibs5_3.93.0-0ubuntu1~feisty2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/kde4/kabcformat_binary.so', which is also in package kdepimlibs4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace kde4base-data 3.80.3-0ubuntu5 (using .../kde4base-data_3.93.0-0ubuntu1~feisty2_all.deb) ...
Unpacking replacement kde4base-data ...
dpkg: error processing /var/cache/apt/archives/kde4base-data_3.93.0-0ubuntu1~feisty2_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/apps/kdeprint/filters/enscript.desktop', which is also in package kde4libs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdepimlibs5-dev (from .../kdepimlibs5-dev_3.93.0-0ubuntu1~feisty2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdepimlibs5-dev_3.93.0-0ubuntu1~feisty2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/include/kabc/address.h', which is also in package kdepimlibs4-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_3.93.0-0ubuntu1~feisty1_all.deb
 /var/cache/apt/archives/kdepimlibs5_3.93.0-0ubuntu1~feisty2_i386.deb
 /var/cache/apt/archives/kde4base-data_3.93.0-0ubuntu1~feisty2_all.deb
 /var/cache/apt/archives/kdepimlibs5-dev_3.93.0-0ubuntu1~feisty2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lunamystry@michelle:~$    [/INDENT]

What is the problem? How do I solve it?

---

### Post by Jussi01 on 2007-09-13
Quite simply:

 "Automatix2 is a block of code which attempts to install some software.  When it fails and breaks systems, we don't provide support for it.  A creditable analysis from a debian/ubuntu developer is here - [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html) "

Hope you dont have to reinstall....

---

### Post by wieman01 on 2007-09-13
I second that... I wouldn't touch Automatix with a 10-foot pole. I have heard so many bad things about it as it can seriously screw up your system. Sorry I cannot help you here but frustration is part of the learning curve.

---

### Post by ravenwere on 2007-09-13
I take it you realise that KDE4 is still in development and isn't due for stable release until December this year.

and secondly, automatix is not recommended for use in ubuntu see following:

[http://en.wikipedia.org/wiki/Automatix_(software](http://en.wikipedia.org/wiki/Automatix_(software))

Did you have a version of KDE 3 installed previously? because it looks like this is causing some of the dpkg confusion. ie some of the development modules from KDE3 appear to be clashing with the modules from KDE4.

Your options are:
Remove Automatix2, and either
Remove the KDE4 packages and return to KDE3.5 or,
Remove KDE3 and do a clean install of KDE4

If you must use Automatix2 then only use it with KDE3

all the best,

PS It goes without saying that you wouldn't want to use KDE4 on a production PC

---

### Post by lunamystry on 2007-09-13
OOPS!! I think I'll have to do a complete reinstall. well thank you anyway. 

:oops:

---

### Post by lunamystry on 2007-09-13
I don't need to re-install after all. Removing automatix worked. It also remove kde4base-dev though but I can just install it again. I like trying new things and having them blow up and then trying to fix them. 

If it wasn't for that I wouldn't be using Ubuntu right now.

---

### Post by hyper_ch on 2007-09-13
While automatix was surely great on older releases of Ubuntu where the codecs and proprietary drivers and ntfs-3g and some other stuff posed serious problems to new users, I tend to think that since Edgy and Feisty there have been many improvements on getting those things to install.

What is still necessary is to add the additional repos to the sources list, like Medibuntu, Seveas', Canoncial Commerical and some more. They aren't there by default.

Those repos will NOT break your system and provide a simple install through apt-get, aptitude, synaptic, adept, ... for most the software contained in Automatix.

---

### Post by lunamystry on 2007-09-13
I've heard of MEDIUBUNTU but I don't think I know the others two though.

---

### Post by hyper_ch on 2007-09-13
Seveas is a guy that runs the dutch ubuntu site and he also created "ubotu" - the friendly helper bot in the *buntu channels on IRC.

And Canonical is the actual company that "develops" Ubuntu... well, they are more selling professional support for it... in the canoncial repos is also some non-free software that is nice like RealPlayer and VmWare Server.

---

### Post by lunamystry on 2007-09-13
Mark 'first african in space' Shuttleworth's company. I know it and  I added the canonical repo thank you and I guess I will not be using the other one as i am not much for chatting and i am in South Africa.

---

