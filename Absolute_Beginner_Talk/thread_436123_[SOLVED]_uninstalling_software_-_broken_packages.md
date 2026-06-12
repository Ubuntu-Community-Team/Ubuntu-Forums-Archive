---
title: "[SOLVED] uninstalling software - broken packages?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by cincinnatus on 2007-05-07
I'm trying to uninstall openoffice.org because I have a small hard drive and i want to free up space for other things. (i've installed abiword already, so i do have a word processor)

I've gone into synaptic package manager and tried to remove the packages with the word "openoffice.org" in the name, at first I did a few of them one at a time, and then I highlighted all of them at once and told it to remove them, and it asked me to fix broken packages, so i tried reinstalling what i uninstalled, and then tried removing everything at once again, and it still says it wants me to fix broken packages.

I tried removing openoffice.org-core and its dependencies, and i got this error message:

> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

I just don't know what I'm doing here. Any help would be greatly appreciated.

If you could even give me something to put into the terminal, that would be great.

---

### Post by taurus on 2007-05-07
Post the output of 

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by cincinnatus on 2007-05-07
> $ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 1s (3B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
E: Couldn't rebuild package cache



Hmm, I also earlier uninstalled the meta-package "ubuntu-desktop", because on [this thread]("http://ubuntuforums.org/showthread.php?t=342490"), it looked like that's what i was supposed to do to be able to uninstall openoffice. Could that be the problem?

---

### Post by cincinnatus on 2007-05-07
here's the other one:

> $ sudo aptitude upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by ayoli on 2007-05-07
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
means you have differents package manager tools opened (update manager, synaptic, apt-get in console, ...)
cloase all and re-run suggested commands

---

### Post by cincinnatus on 2007-05-07
$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 2s (2B/s)
Reading package lists... Done
[/CODE]

```

$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following packages will be upgraded:
  evolution-data-server openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
13 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.8MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?]

```

---

### Post by ayoli on 2007-05-07
to remove open office:
```
sudo aptitude remove penoffice.org-base openoffice.org-calc openoffice.org-common \
openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome \
openoffice.org-gtk openoffice.org-impress openoffice.org-java-common \
openoffice.org-l10n-en-us openoffice.org-math
```
then : 
```
sudo aptitude upgrade
```

---

### Post by Nythain on 2007-05-07
could have possibly been locked due to an incomplete install or uninstall... if something similar ever happens again, try:
sudo dpkg --configure -a
sudo aptitude clean
that will usually free up any messed up install/uninstall and open up that apt lock

---

### Post by cincinnatus on 2007-05-07
yay! it worked!

thank you.

---

