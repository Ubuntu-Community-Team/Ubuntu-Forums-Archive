---
title: "upgrading ubuntu"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by simon_is_learning on 2006-02-20
I just have a thought.

If you have an computer that is tweaked to the limit - with desktop-themes, graphic card settings, and so on.

When you do an upgrade to the next ubuntu-version.
Is it possible to keep all settings.


Just curious, and also:

can this be done by using apt-get?

---

### Post by baldy1324 on 2006-02-20
im not sure if it will keep all of your settings-i havnt done a dist-upgrade on a debian based distro. it probably will keep all of your wallpapers, graphics card settings, and basically everything. it will probably keep about 99% of the settings-basically get everything. but the next ubuntu release-dapper drake-is far from completed-its an alpha-not EVEN IN BETA TESTING. so dist-upgrading to dapper would be LOTS RISKIER than upgrading when it is a stable release

to upgrade using apt-do the following
-change everything in your sources.list from breezy to dapper
-next run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

hope it works-dont be mad if it dosent

---

### Post by paxmaster on 2006-02-20
right now i have drapper on my laptop, it have many bugs 

it is always good idea to backup your hidden file in your home directory, when you upgrade

---

