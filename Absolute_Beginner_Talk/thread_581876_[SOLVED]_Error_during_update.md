---
title: "[SOLVED] Error during update"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-10-19
I got the following error when trying to update to Gusty.  My internet connection is fine.  Is this just a problem because too many people are updating right now?

> A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found

---

### Post by Daveth on 2007-10-19
this

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

is sitting in your APT repositories, along with the key

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

right?  

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I guess it will be red hot from all the downloads as you note.

---

### Post by linuxwizard on 2007-10-19
Try removing or disable any extra repos you added to your source list than try again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by wormser on 2007-10-19
> **linuxwizard said:**
> Try removing or disable any extra repos you added to your source list than try again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

This got me past the error.  I will update if it successfully updates.  Thanks.

Update:

That resolved my upgrading issue.  Too bad the upgrade totally messed up my system.

---

