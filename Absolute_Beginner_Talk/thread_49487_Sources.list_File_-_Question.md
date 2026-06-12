---
title: "Sources.list File - Question"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-07-16
Greetings,

Receiving the following errors:  

root@Tardis:/home/tom # apt-get update
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Fetched 4B in 1s (2B/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Is this something I should be worried about?  This is a direct post from my SOURCES.LIST file and it matches the sources file provided in the beginners set-up guide.

My question is, should it be different?

---

### Post by poofyhairguy on 2005-07-16
[QUOTE=garnertr]Greetings,

Receiving the following errors:  

root@Tardis:/home/tom # apt-get update
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Fetched 4B in 1s (2B/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz)  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Is this something I should be worried about?  This is a direct post from my SOURCES.LIST file and it matches the sources file provided in the beginners set-up guide.

My question is, should it be different?[/QUOTE]


The backport mirror goes down sometimes. Try it again later

---

### Post by maruchan on 2005-07-16
Here, try this one, I saw it on the forum and it works great for me. There are some problems with yours, like ubuntuguide.org should tell people that us.archive.org isn't working...it should be archive.org instead:

> ## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
#deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backup Security Mirrors
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

##Backports
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main


---

### Post by garnertr on 2005-07-16
Ok, secondary question:

With all of the repositories going online/offline, is it a good idea to have a huge "source.list" file?

I'm finding it RATHER difficult to install software b/c i"m getting those error messages.  Having to wait until later is really not a good option b/c i'm impatient and I shouldn't have to wait...

Well, just curious I want to install programs, many of which are suggested via the forums here and I can't, makes it rather frustrating to find games and such...

So, just wanted to ensure that everything on my side is good to go...

thanks everyone!

---

### Post by poofyhairguy on 2005-07-16
[QUOTE=garnertr]Ok, secondary question:

With all of the repositories going online/offline, is it a good idea to have a huge "source.list" file?

I'm finding it RATHER difficult to install software b/c i"m getting those error messages.  Having to wait until later is really not a good option b/c i'm impatient and I shouldn't have to wait...
[/QUOTE]

If you want it to be down less, donate some money for bandwidth please.

If you really can't wait, comment out (aka put two # signs before each line) the backport repos. You only need those lines sometimes.

---

