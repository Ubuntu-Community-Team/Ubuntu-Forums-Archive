---
title: "upgradng from edgy to feisty"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by eheitner on 2007-05-07
I posted a problem I had earlier about update manager failing to fetch packages for the upgrade, and was told to try ftping.
So I enabled the ftp 3rd party sources. But I am still failing to fetch the following packages:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/edgy/non-free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '

---

### Post by fakie_flip on 2007-05-07
How are you upgrading? Have you tried this way?

gksu update-manager -c

---

### Post by eheitner on 2007-05-07
I'm using update manager graphically. Starting update manager using with gksu doesn't seem to change anything. Using gksu update-manager -c returns
gksu: invalid option -- c

---

### Post by eheitner on 2007-05-07
And apt-get update doesn't work either, same problem--files not found.

Any other ideas?

---

### Post by fakie_flip on 2007-05-07
Sorry, do this instead.

gksu "update-manager -c"

---

### Post by eheitner on 2007-05-07
Nope, doesn't help at all.

---

### Post by zvacet on 2007-05-07
Comment that lines(put #sign in front of them)and 

```
sudo aptitude update
```

to be sure that your Edgy is up-to-date and after that do the upgrade


[http://packages.freecontrib.org/ubun](http://packages.freecontrib.org/ubun). doesn´exist anymore.it is replaced with medibuntu.You can use this source list
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by eheitner on 2007-05-07
Sorry, which file do I need to edit to put those comments in?

---

### Post by fakie_flip on 2007-05-07
/etc/apt/sources.list

---

### Post by nyvalbanat on 2007-06-08
"Sub-process bzip2 returned an error code (2)" means there are duplicate repositories in sources.list. The http 404 errors mean that the repository is not reachable (down?).

---

