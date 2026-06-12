---
title: "Problem with my sources.list file"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-02-01
Hi, recently when I have been trying to update my system, I have been getting some errors.

Here is the message I get.

Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 4B in 0s (5B/s)
Reading package lists...


Is my sources.list file incorrect?  What is the correct file?  Can anyone help me?

---

### Post by Adrian on 2006-02-01
Your problem is that the mirrormax repository does not work anymore.

You can find up-to-date repositories here:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by ShaneAu on 2006-02-04
I put the files back there, but keep in mind it's still no longer used by the backports team. But it's always going to be there if they need it. :)

So no more 404's and scaring the beginners. :)

---

