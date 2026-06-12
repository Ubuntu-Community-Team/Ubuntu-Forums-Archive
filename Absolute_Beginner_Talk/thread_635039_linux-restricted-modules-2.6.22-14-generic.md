---
title: "linux-restricted-modules-2.6.22-14-generic"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-12-08
Hey everyone,

When I try to install any package I get an error that looks something like this:

```
Errors were encountered while processing:
 linux-restricted-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any one  know a fix for this? It happens on virtually any package I install. I have all of the repositories enabled but nothing seems to be working.

---

### Post by meborc on 2007-12-08
there is something wrong with your restricted-modules pack, you might try "sudo apt-get -f install" or "sudo dpkg-reconfugure linux-restricted-modules-2.6.22-14-generic"

---

### Post by AngryMallard on 2007-12-08
```
$ sudo dpkg-reconfigure linux-restricted-modules-2.6.22-14-generic
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-2.6.22-14-generic is broken or not fully installed

```

---

### Post by meborc on 2007-12-08
what about ```
sudo apt-get update
sudo apt-get -f install
```?

---

### Post by AngryMallard on 2007-12-08
```
:~$ sudo apt-get update
[sudo] password for bryan:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US          
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US    
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com gutsy-proposed Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/universe Packages     
Hit http://security.ubuntu.com gutsy-security/universe Sources      
Hit http://security.ubuntu.com gutsy-security/multiverse Packages   
Hit http://security.ubuntu.com gutsy-security/multiverse Sources    
Get:6 http://us.archive.ubuntu.com gutsy-backports Release [44.0kB] 
Hit http://us.archive.ubuntu.com gutsy-proposed Release
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Get:7 http://us.archive.ubuntu.com gutsy-backports/main Packages [13.5kB]
Get:8 http://us.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:9 http://us.archive.ubuntu.com gutsy-backports/universe Packages [51.3kB]
Get:10 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages [2599B]
Hit http://us.archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/main Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-proposed/universe Packages
Fetched 112kB in 2s (53.1kB/s)                     
Reading package lists... Done

:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
 linux-restricted-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
bryan@DELL-UBUNTU:~$ 

```

---

### Post by AngryMallard on 2007-12-08
Actually it seems that sometimes I can install some programs and other times I can't. I just installed xchat with synaptic and I got the same flavor error message, but I'm trying to install another program and it won't make it all the way through the installation before it quits because of that error. Any ideas?

---

### Post by AngryMallard on 2007-12-08
Oh and it's a Dell Dimension 2350, 2.00 gHz Pentium 4 with 512 mb RAM, Intel i810 integrated graphics with Ubuntu 7.10. Basically, it's been a huge pain in the neck since I got it.

---

### Post by zvacet on 2007-12-09
```
sudo dpkg --configure -a
```

---

### Post by AngryMallard on 2007-12-09
```
$ sudo dpkg --configure -a
[sudo] password for bryan:
Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
 linux-restricted-modules-2.6.22-14-generic

```

---

