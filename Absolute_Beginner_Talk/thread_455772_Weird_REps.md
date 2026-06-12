---
title: "Weird REps"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-26
Hey, I'm trying to add universal and multiverse reps and as it updates i get this error:

"W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991"

I also get this when I run sudo apt-get update:
"craig@craig-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
craig@craig-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]
Hit [http://dl.google.com](http://dl.google.com) stable Release
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Ign [http://flomertens.free.fr](http://flomertens.free.fr) dapper Release.gpg
Err [http://dl.google.com](http://dl.google.com) stable Release

Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1026B]
Ign [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://flomertens.keo.in](http://flomertens.keo.in) dapper Release.gpg
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:11 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg [191B]
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [189B]
Get:13 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://flomertens.free.fr](http://flomertens.free.fr) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://flomertens.keo.in](http://flomertens.keo.in) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Ign [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://flomertens.free.fr](http://flomertens.free.fr) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Ign [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main-all Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main Packages
Ign [http://flomertens.free.fr](http://flomertens.free.fr) dapper/main-all Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages
Hit [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main-all Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages
Hit [http://flomertens.free.fr](http://flomertens.free.fr) dapper/main Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://flomertens.free.fr](http://flomertens.free.fr) dapper/main-all Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources
Fetched 1229B in 4s (280B/s)
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems"


Why is this coming up??

---

### Post by Tumpster on 2007-07-26
Bump!

---

### Post by skymera on 2007-07-26
you only dan apt-get update, ont with sudo.

and the gpg key you need to add, i think its to verify source? but i know it makes it works :P

---

### Post by Tumpster on 2007-09-01
I'm not understanding, how can I fix this error?

---

