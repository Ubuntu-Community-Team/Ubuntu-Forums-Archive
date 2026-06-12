---
title: "Respository problem"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-26
I ran a general update/upgrade/install command and I got the following error. I bolded it for ease on our eyes ;) 

This connection timeout has happened every time I run the update/upgrade/install command. How can I fix this problem? 

Thanks :)

> matt@matt-laptop:~$  sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
Get: 1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get: 2 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get: 7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
[b]Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 195B in 2m10s (1B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release](http://packages.freecontrib.org/plf/dists/dapper/Release)  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/b]
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Edit:

Also in Synaptics I get the following error, which is more than likely linked to this problem.

[http://packages.freecontrib.org/plf/dists/dapper/Release:](http://packages.freecontrib.org/plf/dists/dapper/Release:) Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by LookTJ on 2006-10-26
the server is unresponsive at the moment

---

### Post by spamzilla on 2006-10-26
Is it me or is the freecontrib server always down or unresponsive?

---

### Post by LookTJ on 2006-10-26
> **spamzilla said:**
> Is it me or is the freecontrib server always down or unresponsive?

Today everyone is downloading edgy, upgrading to edgy. adding repos. so unresponsive for me

---

