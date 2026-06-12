---
title: "Couldn't find package"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-11
> mike@mike-laptop:~$ sudo gedit /etc/apt/sources.list
mike@mike-laptop:~$ wget [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg) -O - | sudo apt-key add -
--00:16:25-- [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg)
=> `-'
Resolving easyubuntu.cafuego.net... 209.59.209.80
Connecting to easyubuntu.cafuego.net|209.59.209.80|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [text/plain]

100%[====================================>] 2,415 --.--K/s

00:16:46 (32.57 KB/s) - `-' saved [2415/2415]

gpg: no ultimately trusted keys found
OK
mike@mike-laptop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:3 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Get:6 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release [5753B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:7 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Fetched 15.6kB in 0s (17.2kB/s)
Failed to fetch [http://easyubuntu.cafuego.net/dists/main/Release](http://easyubuntu.cafuego.net/dists/main/Release) Unable to find expected entry easyunbuntu/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
mike@mike-laptop:~$ sudo apt-get install easyubuntu
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package easyubuntu


this is the message I get when I tried to installed easyubuntu... and I also got that same kind of error when trying to install Automatix.  Can anyone tell me what I'm doing wrong?

---

### Post by mark_g on 2006-10-11
You could try to install it from source. Might be easier.

(from [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html))
> 
wget ttp://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz
tar -zxf easyubuntu-3.023.tar.gz
cd easyubuntu
sudo python easyubuntu.in

---

