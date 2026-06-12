---
title: "Upgrade from 5.04 to 6.10"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-04-01
Just took the plunge and installed unbuntu on my desktop. I installed from a cd I had requested a while back, ver 5.04. I'm running into a lot of problems and think upgrading may solve a few of them. I downloaded the ISO from unbuntu.com (actually I've downloaded it twice now) and it keeps getting stuck, after I select install and before it really does anything. I've checked he md5s and everything seems okay with the disk/download. Any sugestions? Also is there a way to upgrade through my current distro?

---

### Post by mikeyphi on 2007-04-01
Shame you can't reinstall with the new iso.
You should be able to upgrade from 5.4 but you will have to do it via 5.10 then 6.4 then 6.10 - a somewhat long process.
What happens when you run the update manager (or equivalent in 5.4)?

---

### Post by woodsonoversoul on 2007-04-01
when I run:

apt-get dist-upgrade

terminal says:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  dpkg-dev libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by jvc26 on 2007-04-01
To upgrade to the next ubuntu version up you have to update your sources.list with a new one so it knows where to find the new packages - else it will just be trying to update your stuff from your current version's repos. To do this you need to do something like:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
The thing is, 5.04 is very old, and so you have to upgrade successively:
5.04 -> 5.10 -> 6.04 -> 6.10 and soon if you want to ->7.04
All the upgrades can cause problems and so to do all the way up may be an issue. Although it is possible - see the link, it may well be that the problem is something like RAM (I'm presuming you're using the desktop version) I'd try before you start the long road of upgrading one to the next to the next to try the alternate install cd (available from the same place you downloaded the other) This may well offer you a faster solution with a fresh install of a new version.
Il

---

### Post by Maestro23 on 2007-04-01
Some more logs on the fire.

Upgrade Guides:

Upgrade to Dapper: [https://help.ubuntu.com/community/DapperUpgrades?highlight=%28dapper%29%7C%28upgrade%29](https://help.ubuntu.com/community/DapperUpgrades?highlight=%28dapper%29%7C%28upgrade%29)

Upgrade to Edgy: [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29%7C%28edgy%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29%7C%28edgy%29)

Upgrade to Feisty: [https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrade%29%7C%28feisty%29](https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrade%29%7C%28feisty%29)

---

### Post by woodsonoversoul on 2007-04-01
I downloaded and an attempting to install, I believe it's version 6.4? the LTS version. I figured maybe I could install that and it would be easier to upgrade from there. However as the install begins I keep getting stuck at "Loading hardware invers" it says it completes that ok, but then freezes. Any ideas?

---

### Post by woodsonoversoul on 2007-04-01
bump

anyone know what's going on?

---

### Post by NeoLithium on 2007-04-01
Depending on the specs of your computer; you might want to try to use the alternate install CD; it's a non-graphical install; but usually works well when compared to problems encountered with the live CD.

---

### Post by woodsonoversoul on 2007-04-01
I don't see an option on ubuntu's page to download the alternate version...

---

### Post by jvc26 on 2007-04-01
Presuming you're in the UK 6.06:
[http://www.mirrorservice.org/sites/releases.ubuntu.com/dapper/](http://www.mirrorservice.org/sites/releases.ubuntu.com/dapper/)
and select the alternate install for the architecture you have,
If elsewhere:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
Select where and then go through to find the Ubuntu 6.06 mirror page.
Il

---

