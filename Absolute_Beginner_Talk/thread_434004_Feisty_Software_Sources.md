---
title: "Feisty Software Sources"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by The Godfather on 2007-05-05
Hi everyone:

Maybe someone can explain this to me. I get the following error when I do an apt-get update (throught the update manager):

[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)

Then when I do it manually I get a little more info, such as:

Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources [63.5kB]                                                                                          
99% [8 Sources gzip 0]                                                                                                                           32.0kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                                                                                                     
  Sub-process gzip returned an error code (1)
Fetched 8B in 6s (1B/s)                                                                                                                                     
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?:confused:

---

### Post by taurus on 2007-05-05
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Bachstelze on 2007-05-05
Try this :

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-get update
sudo cp /etc/apt/sources.list.old /etc/apt/sources.list
sudo apt-get update
```

same error ?

---

### Post by nixclusive on 2007-05-05
Nope.. fixed mine. Thanks. This was my sources.list:
```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://packages.freecontrib.org/plf dapper free non-free
#deb-src http://packages.freecontrib.org/plf dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
#deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by Bachstelze on 2007-05-05
To everyone else, when APT complains about a file not being in the correct format, running *apt-get update* with an empty sources.list can help, that's what the commands I posted above do.

---

### Post by nixclusive on 2007-05-05
By the way.. I'd certainly like to know what caused that error? ```
gzip: stdin: not in gzip format
``` The command```
apt-get --print-uris --no-download update
``` shows that there's no file that is gzipped. Everything was in bz2...

---

### Post by Bachstelze on 2007-05-05
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/)

There are gzipped indexes too.

---

### Post by The Godfather on 2007-05-05
Many thanks everyone! I will try it now. Btw, here is my sources list:

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## MEDIBUNTU REPOSITORY (Multimedia, Entertainment & Distractions In Ubuntu)
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by The Godfather on 2007-05-05
Sorry, it didn't work out, I got the same error again.

---

