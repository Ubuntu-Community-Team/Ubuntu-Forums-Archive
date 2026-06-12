---
title: "Updating apt-get - Synaptic - Update Manager"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-22
When trying to update sources in apt-get, synaptic, update manager, I keep getting the following error codes:


[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Are these links no longer good?  Does anyone have updated links?
TIAFAI

---

### Post by Sef on 2006-12-22
Could you post your sources list?  After opening the Terminal, type this, then copy and paste the resulsts here:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by BarfBag on 2006-12-22
Those should work.  Do what Sef said.

---

### Post by randiroo76073 on 2006-12-22
Here you go:

## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by nickburns on 2006-12-22
Is it because the last few lines are repeats of what you already have?

---

### Post by randiroo76073 on 2006-12-22
I don't think so, those lines were added by Automatix, but I'm not sure.

---

### Post by macogw on 2006-12-22
Delete all the lines for PLF Repositories (the freecontrib ones), and do apt-get update again.  Those repos went down a few days ago and aren't coming back.

---

### Post by randiroo76073 on 2006-12-22
Thanks macogw will do.  What happened to them, or should I ask?
What about these 5?
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Sub-process gzip returned an error code (1)

[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Sub-process gzip returned an error code (1)

[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Sub-process gzip returned an error code (1)

[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Sub-process gzip returned an error code (1)

[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Sub-process gzip returned an error code (1)

---

