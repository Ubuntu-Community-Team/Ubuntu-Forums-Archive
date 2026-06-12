---
title: "all repositories in sources.list....FAIL?!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by pkarza on 2006-09-01
Unbuntu is great - I've tried different flavours, but I finally wanted to get some other programs that were in multiverse and universe (one example is for restricted format) and guess what - can't find it.

apt-get update .... all fail
synaptic package manager... same thing.

I installed from the DVD - so I am now REALLY confused - why would my original sources.list be no good?  I'm using Dapper dvd 6.06.1 (I believe) and did a fresh install..

any help would be appreciated - and YES I did search the forums.

Thanks

Phil:D

---

### Post by taurus on 2006-09-01
What does your /etc/apt/sources.list look like then?

```
more /etc/apt/sources.list
```

---

### Post by slimdog360 on 2006-09-01
are you saying you enabled the extra repositories, or did you already do that and they failed?
If you havent enabled them already go to [here]("http://www.psychocats.net/ubuntu/sources")

---

### Post by GuitarHero on 2006-09-01
ignore

---

### Post by catlett on 2006-09-01
enter this in the terminal and then copy/paste the output in a reply
```
sudo apt-get update
```
Then put this is the terminal and copy/paste it in the reply as well
```
cat /etc/apt/sources.list
```

---

### Post by pkarza on 2006-09-02
Here it is:

my sources.list...



## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
 
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted

---

### Post by bikeboy on 2006-09-02
Is your internet connection itself working on Ubuntu?

---

### Post by eternalis on 2006-09-02
Use the sources.list from here:
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by pkarza on 2006-09-02
and.... here is the display when I apt-get update... fail fail fail away...


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  Connection failed
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by pkarza on 2006-09-02
Yes  my internet is working... that's what I'm using now!

---

### Post by bikeboy on 2006-09-02
Cool, thought you might have been using another computer to post. Have you specified the DNS servers in the network config gui? Although if you hadn't you probably wouldn't be getting to the forum.

---

### Post by ormandj on 2006-09-02
I have the exact same problem, and I JUST installed Ubuntu 6.06.1 server. Network works fine, I can even telnet to archive.ubuntu.com on port 80 and GET returns data. I get connection failed errors on everything regardless!

What's going on?

---

### Post by johnficca on 2006-09-02
I'm having the same problem! can someone help?

---

### Post by bikeboy on 2006-09-02
Hmmm starting to sound like a bug.

Have any of you tried different mirrors for the repo's? Try appending "au." without the quotes to the start of each line.

eg```
deb http://au.archive.ubuntu.com/ubuntu dapper main restricted
``` It's not a local mirror for you guys but at least it might work. If it still doesn't work, try an ftp mirror such as```
deb ftp://mirror.pacific.net.au/linux/ubuntu dapper main restricted
```

---

### Post by pkarza on 2006-09-04
anyone??

---

### Post by bikeboy on 2006-09-05
Do you know how to edit the repositories (to try my suggestion) or do you need some guideance on that?

---

### Post by pkarza on 2006-09-11
Yes - I nano'd the sources.list - but it STILL does NOT work.

ANYONE??

---

### Post by pkarza on 2006-09-11
ok... an update... NOW I'm getting ign before each line... what does that mean?

---

### Post by Najand on 2006-09-11
You are probably behind a proxy server... Do you have the information of the proxy server?

---

