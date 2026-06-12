---
title: "is this a bug?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by rav on 2006-08-10
i have changed many sources.list but get the same error every time i even reinstalled my system 4 times till now but get the same error.

[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

i am not able to get any packages from multiverse binary. I also tried removing gzip and again installing it but same error occurs.

now i took sources.list from [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

My sources.list is

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## only uncomment it if you need it
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
 deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

is this a bug is there a fix how do i check if it is a bug. Is there any solution. Please provide any help.

---

### Post by editrix on 2006-08-10
I just searched the forums using:

Sub-process gzip returned an error code

and got 149 hits. It seems to be a repository problem. You should, perhaps, be using a different one, or wait till the one you're using resolves itself.

---

