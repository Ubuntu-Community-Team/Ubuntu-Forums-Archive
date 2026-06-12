---
title: "Sources List Problems"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-08-08
Hey all! I'm trying to download some programs (firefox, thunderbird, synaptic package manager) but they aren't coming up when I search for them in Adept.... Here is my sources list:
```

## Uncomment the following two lines to fetch updated software from the network
 deb http://archive.ubuntu.com/ubuntu dapper main restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper main restricted 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://archive.ubuntu.com/ubuntu dapper universe
 deb-src http://archive.ubuntu.com/ubuntu dapper universe 
 deb http://security.ubuntu.com/ubuntu dapper-security main restricted
 deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe 
 deb http://archive.ubuntu.com/ubuntu dapper multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper multiverse 
 deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
 deb http://archive.canonical.com/ubuntu dapper-commercial main 
 deb http://packages.freecontrib.org/plf/ dapper free non-free
 deb-src http://packages.freecontrib.org/plf/ dapper free non-free
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

```

It's probably a really obvious problem, but I really can't see it....

---

### Post by OU812 on 2006-08-08
It looks ok.

1. Compare your sources.list with

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

if you haven't already.

2. Do an update either in your package manager or using the command line

```
sudo apt-get update
```

or

```
sudo aptitude update
```

This will force your package manager to update its available list of packages.

john

---

### Post by tartarian on 2006-08-08
Yay! thanks! they all show up now! (took a couple of hours to update tho!)

---

