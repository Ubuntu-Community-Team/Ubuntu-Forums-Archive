---
title: "Lots of updates lately?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Nathan Otis on 2006-07-14
I'm very new around here, but in the past week I've gotten three alerts for updates... Is that comman? I dig on the continuing development thing, but... really?

n.

---

### Post by echo $USER on 2006-07-14
Yeah I have noticed that too.  But today I started getting this error

> Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [42.8kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [9372B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [24.9kB]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [2224B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [36.8kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6951B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [1680B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9118B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [521B]
Fetched 224kB in 2s (77.5kB/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Anyone else experiencing this?

Well i commented out

> ##deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

and the updates work.  What happened to these repos?

---

### Post by crispy_420 on 2006-07-14
Try using this instead:

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

If you are using dapper

---

### Post by echo $USER on 2006-07-14
Ohhhh, thank you.

---

### Post by NeoGreen on 2006-07-14
I get the same alert, just yesterday I received an alert and I had 102 updates.:confused:

---

