---
title: "Upgrading to Feisty"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-05-18
Is there a way to upgrade from 6.10 to 7.04 without using the install CD.  I mean by direct downloading from the internet

---

### Post by mikewhatever on 2007-05-18
I believe there is [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Najand on 2007-05-18
Well... It is easier to do it by using internet than the installation CD.

---

### Post by Pollywoggy on 2007-05-18
You should never need to upgrade by reinstalling.  I believe I used Adept to upgrade from Edgy to Feisty, but one could use apt-get instead (I believe it is not recommended in Ubuntu).

There are some Linux distributions that do not yet have an easy upgrade path, such as Linspire, Freespire and possibly Xandros but for most Linuxes, a reinstall with the newer install CD is not required.  For Ubuntu it's easy to upgrade.

See the link posted above in this thread.

---

### Post by gamer91 on 2007-05-18
would that carry over installed applications? and update/edit them accordingly.

---

### Post by Seisen on 2007-05-18
Only if you installed them through synaptic or apt-get/aptitude.

---

### Post by SteelCore on 2007-05-18
I've been trying to upgrade to 7.04 (from 6.10) for the past 6 hours but keep getting this message: "Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2) MD5Sum mismatch
Failed to fetch [http://jo.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2](http://jo.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2) MD5Sum mismatch"

---

### Post by Najand on 2007-05-19
Close synaptic, if it is open and try to run:
```

sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update

```
and try again.

---

### Post by engine on 2007-05-19
Hm.

Checked the wiki page for EdgyUpdatesEnabled, and read the advice about needing update-manager 0.45.2

Followed all steps given in wiki page to update/refresh/populate my package list for Synaptic, and _still_ all I get offered is 0.42.2

Hints and tips (or, even better, patient and explicit explanations) of how to complete this first step of acquiring/installing update-manager 0.45.2 will be gratefully received!

---

