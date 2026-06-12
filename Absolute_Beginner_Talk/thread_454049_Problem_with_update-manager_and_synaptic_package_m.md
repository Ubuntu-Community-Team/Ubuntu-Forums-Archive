---
title: "Problem with update-manager and synaptic package manager"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by isionous on 2007-05-25
Just recently update-manager and synaptic package manager started acting up.  The message "Could not download all repository indexes" pops up when I try to check for updates in update-manager or reload the list in synaptic package manage.  I'm unable to upgrade to edgy(and then onto feisty) because of this. I haven't messed with repositories or anything related to those two programs recently...that I explicitly recall, but obviously something happened - computers are deterministic machines, after all.

Thanks for the help.

---

### Post by Kobalt on 2007-05-25
Can you please post here your sources.list file ?```
cat /etc/apt/sources.list
```

---

### Post by isionous on 2007-05-25
```

deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://wine.budgetdedicated.com/apt dapper main

```

---

### Post by isionous on 2007-05-29
These seem to be the exact conditions that get the error:

[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found

---

### Post by zvacet on 2007-05-29
You can try this source list 

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by isionous on 2007-05-30
Trying that worked.  Thanks so much!

---

### Post by Bochiechio on 2007-05-31
Thank you, I've been trolling these forums for 2 days trying to find a solution to that one.

---

