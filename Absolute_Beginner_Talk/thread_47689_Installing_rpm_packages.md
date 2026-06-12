---
title: "Installing rpm packages"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by jkarnacki on 2005-07-09
Hi, this might be similiar to the other thread, but I figured I'd start my own as my problems is a little different.  I am trying to run Steam on Ubuntu.  I am following this tutorial:

[http://www.pro-networks.org/forum/post-450601.html](http://www.pro-networks.org/forum/post-450601.html)

I have downloaded and installed Wine.  Then the tut. says 

"
	
 
WineX Install Guide
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
Warning: This HOWTO comes with no explicit or implicit warranty
whatsoever. Use at you own risk!

1) Preface
2) Preparations
3) Compilation
4) Installation
5) Configuration
6) Testing
7) GUI's
8) Links
9) Troubleshooting





1. Preface

This Wine HOWTO should make it possibly for anybody to use Wine. I
refert to wine version 20030408 and Linux Mandrake 9.0, yet it should
work fine with other distributions as well.
This HOWTO describes the manual installation and we'll use a Fake-Windows.


Please follow every step just as it is described here.

2. Preparations

2.1 Cleanse the system

Before starting it would be a good idea to remove all old wine files,
if present. Yet first try to deinstall everything properly using the
rpm package manager.
Find out via "whereis wine" in a terminal where these are located, e.g.:
[stefan@ultratiger stefan]$ whereis wine
wine: /usr/local/bin/wine /usr/local/lib/wine
[stefan@ultratiger stefan]$

Now delete everything that is named wine in /usr/local/bin/ (not the
directory itself) and the directory /usr/local/lib/wine . There might
also be a directory named ".wine" (mind the dot) in the homedirectory
of users - rename these, the old "config" could be usefull lateron.

2.2 Install developement packages

Find out via "rpm -qa" if the following packages are installed:

bison-1.35-3mdk
compat-libstdc++-7.3-2.96.110
libstdc++5-devel-3.2-1mdk
libncurses5-devel-5.2-27mdk
zlib1-devel-1.1.4-3mdk
libjpeg62-devel-6b-25mdk
glibc-devel-2.2.5-16mdk
XFree86-devel-4.2.1-3mdk
libpng3-devel-1.2.4-3mdk
libglib2.0_0-devel-2.0.6-2mdk
libSDL_net1.2-devel-1.2.4-5mdk
libMesaglut3-devel-4.0.3-6mdk
glibc-static-devel-2.2.5-16mdk
libSDL_image1.2-devel-1.2.2-3mdk
libMesaGLU1-devel-4.0.3-6mdk
libSDL_ttf2.0-devel-2.0.5-3mdk
libSDL1.2-devel-1.2.4-11mdk
libSDL_mixer1.2-devel-1.2.4-5mdk
libbzip2_1-devel-1.0.2-10mdk

If one is missing please install it! "

I type "rpm -qa bison-1.35-3mdk"

That gives me the error 

"rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
jeff@Ubuntu:~$"

I then try the command "sudo alien bison-1.35-3mdk"

That generates the error 

"File "bison-1.35-3mdk" not found."

Where do I get these files?  Where do I put them after?  Remembe, I like to call myself a "super-noob" at linux.   :-P 

Thanks.

---

### Post by jkarnacki on 2005-07-09
Okay, I think my googling skills finally paid off.   :razz:   I download one of the packages and used the commands:

sudo alien bison-1.35-3mdk.i586.rpm
bison_1.35-4_i386.deb generated
sudo dpkg -i bison_1.35-4_i386.deb
Selecting previously deselected package bison.
(Reading database ... 58000 files and directories currently installed.)
Unpacking bison (from bison_1.35-4_i386.deb) ...
Setting up bison (1.35-4) ...

Okay so thts what my screen looks like in Terminal.  I posted it incase anyone else needs this info.

Now one last thing, can I deleted the .rpm file that i downloaded?  Can I deleted the .deb file that was generated?

---

