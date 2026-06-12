---
title: "upgrade from 5.10"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by arg on 2007-11-08
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz) 404 Not Found

just trying to use the upgrade tool which i have checked is upto date...
upgrading from Ubuntu 5.10, Breezy Badger

---

### Post by AlexenderReez on 2007-11-08
as far as i know...there is no support for breezy version because its support term already end...please use newer version....

---

### Post by arg on 2007-11-08
thats what im trying to do.. but i cant upgrade.. cause i get that error?

---

### Post by AlexenderReez on 2007-11-08
well...i would recommend fresh install latest version rather than upgrade it....even devs said just try and report the error....but due to there would be high risk that you will break your system...it is better to choose clean install....

but it is up to you....


[PHP]$ gksu "update-manager -c"[/PHP]

---

### Post by ruibernardo on 2007-11-08
Breezy isn't maintained since [April 13th 2007]("http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life") (it was a Friday...). You have to upgrade to Dapper: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades).

EDIT:

Breezy packages were removed from the archives.ubuntu.com servers! For those who still have old releases of Ubuntu (Warty, Hoary, Breezy) and can't find their repositories, I think they can use the old-releases archive by updating their sources.list (not tested but the info is here: [https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2007-May/000010.html](https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2007-May/000010.html)).

Still, an upgrade to Dapper is the best choice, or a fresh install, as AlexenderReez said.

---

### Post by mcduck on 2007-11-08
You'll have to just download the cd and make a fresh new install. You can't jump over any version when upgrading, so you'd need to first upgrade to 6.06, then 6.10, then 7.04 and finally to 7.10. It's a lot easier to just make a fresh install with the 7.10 disk.

---

