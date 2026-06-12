---
title: "Can no longer install new packages!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Ins0mau on 2007-08-05
Hi. The Synaptic Package Manager failed in trying to remove ltmodem-2.6.8-l-686 Install version 8.31a8

Now I can't seem to install anything at all!!!

Synaptic Package Manager says:

> E: ltmodem-2.6.8-1-686: subprocess post-removal script returned error exit status 1

I tried to copy the details here but for some reason I can't copy and paste from the window.



The help file said it was a known bug and suggested I try:

> apt-get install -f

But it didn't work. Here's what happened:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-1-686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1327kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 89819 files and directories currently installed.)
Removing ltmodem-2.6.8-1-686 ...
[: 12: 0: unexpected operator
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


ERROR: Module lt_serial does not exist in /proc/modules
ERROR: Module ltserial does not exist in /proc/modules
ERROR: Module ltmodem does not exist in /proc/modules
ERROR: Module lt_modem does not exist in /proc/modules
Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-1-686 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-1-686
E: Sub-process /usr/bin/dpkg returned an error code (1)



I'm a long time Windows user and newbie to Linux and I really have high hopes for it. I don't mind getting my hands dirty in the command line shell or working a bit harder for a good O.S but I'm quite disheartened by the huge lack of modem support (even for allegedly supported modems). And now one corrupt uninstall has totally messed up the WHOLE installation proccess for ANY OTHER INSTALLS!!! And Ubuntu is supposed to be among the EASIEST Linux distros for installations!! Not looking good.

Apart from these two problems (which I find pretty damn big) I'm finding Linux and Ubuntu in particular to be really good. I hope such problems as these aren't an every day occurrence.

---

### Post by Alexander2007 on 2007-08-05
Try ```
sudo dpkg -P contacts
```

Then ```
apt-get install -f
```
Then ```
sudo apt-get update
```
Then ```
sudo apt-get dist-upgrade
```

---

### Post by Ins0mau on 2007-08-05
Nope. Didn't work.

Of course, not having a modem driver to connect to the internet when I'm booted into Ubuntu would probably have something to do with it.

sudo dpkg -P contacts

> dpkg - warning: ignoring request to remove contacts which isn't installed.

sudo apt-get install -f

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-1-686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1327kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 89819 files and directories currently installed.)
Removing ltmodem-2.6.8-1-686 ...
[: 12: 0: unexpected operator
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


ERROR: Module lt_serial does not exist in /proc/modules
ERROR: Module ltserial does not exist in /proc/modules
ERROR: Module ltmodem does not exist in /proc/modules
ERROR: Module lt_modem does not exist in /proc/modules
Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-1-686 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-1-686
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get update

> Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_AU
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_AU
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_AU
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_AU
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_AU
  Could not resolve 'security.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_AU
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_AU
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Translation-en_AU
  Could not resolve 'au.archive.ubuntu.com'
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates/universe Packages
  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  Could not resolve 'au.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

sudo apt-get dist-upgrade

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-1-686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1327kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 89819 files and directories currently installed.)
Removing ltmodem-2.6.8-1-686 ...
[: 12: 0: unexpected operator
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


ERROR: Module lt_serial does not exist in /proc/modules
ERROR: Module ltserial does not exist in /proc/modules
ERROR: Module ltmodem does not exist in /proc/modules
ERROR: Module lt_modem does not exist in /proc/modules
Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-1-686 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-1-686
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

