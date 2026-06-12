---
title: "[SOLVED] partial upgrade problems"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2008-03-31
When I go to upgrade manager, it says I need to do a partial upgrade.  I click partial upgrade, and during the preparing the upgrade step, it simply closes.  Any ideas how to do this upgrade?

---

### Post by Oldsoldier2003 on 2008-03-31
> **Specter043 said:**
> When I go to upgrade manager, it says I need to do a partial upgrade.  I click partial upgrade, and during the preparing the upgrade step, it simply closes.  Any ideas how to do this upgrade?

run
```
sudo apt-get update 
sudo apt-get update
```

then post any errors you may receive

---

### Post by Specter043 on 2008-03-31
Fetched 7B in 1s (5B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I had tried to do an upgrade to 8.04, but it wouldn't complete, since I was wireless at the time (dumb, I know)  I have a feeling it has to do with that.  These are the errors above though.

---

### Post by Tatty on 2008-03-31
Yes it sounds like your broken distro-upgrade might be the problem, I assume you are using Gutsy now?

can you posts your sources.list file?

```
cat /etc/apt/sources.list
```

---

### Post by Specter043 on 2008-03-31
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted web
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main universe multiverse restricted

---

### Post by Specter043 on 2008-04-01
Is that the right command?

also, bump.

---

### Post by Specter043 on 2008-04-01
Never mind, solved it with apt-get update, followed by apt-get dist-upgrade.

---

