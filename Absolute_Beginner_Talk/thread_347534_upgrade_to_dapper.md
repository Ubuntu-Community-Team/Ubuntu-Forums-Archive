---
title: "upgrade to dapper"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2007-01-27
Okay, so i have breezy badger and i want to upgrade to dapper drake.... I have thoose live Cd's from which you can install too but they are very slow while installing. So is there a method through which i upgrade to dapper without downloading the dapper drake cd's.

---

### Post by Duppy on 2007-01-27
nope.

---

### Post by taurus on 2007-01-27
Do you have network connection on that machine?

---

### Post by xopher on 2007-01-27
Well you don't have to download any cd's at all. Just do a dist-upgrade.

Short version: Make backups, edit all breezy entries in /etc/apt/sources.list to dapper, run sudo apt-get update && sudo apt-get dist-upgrade.

And voilà.

Edit: If this is the path you choose, check this out: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
It explains the upgrade process really thoroughly.

Good Luck :)

---

### Post by Pobega on 2007-01-27
If you have an internet connection you can upgrade, but that's not to say it will be buggless. You're probably better off burning the CDs and upgrading to Edgy or Dapper, and adding all of your settings back in.

---

