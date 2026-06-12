---
title: "Wine Help"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-20
i know how u have to do apt-get update
 to get wine
this is error i get
root@sergey-desktop:/home/sergey# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release [34.8kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 137kB in 2s (52.3kB/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
root@sergey-desktop:/home/sergey#

HELP?

---

### Post by Tootles on 2007-09-20
?

---

### Post by AlexenderReez on 2007-09-20
1. there is no error except you don't have authorization key.....
2.i suggest you to use feisty instead of dapper .....
3.you can get wine for dapper version from here -->

> [http://www.getdeb.net/release.php?id=589](http://www.getdeb.net/release.php?id=589)

---

### Post by Tootles on 2007-09-20
do u know how to update to fiesty?

---

### Post by Maestro23 on 2007-09-20
> **Tootles said:**
> do u know how to update to fiesty?

Upgrading to Feisty: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

*In the link, it says you have to update in steps:  Dapper >> Edgy >> Feisty.  (Safe route).

---

### Post by AlexenderReez on 2007-09-20
hm..actually it is quite dangerous straight away to upgrade to feisty without upgrade tp edgy first ..but one of dev suggest to try and mention in forum if you counter any problem....

to upgrade to edgy 

> sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
sudo apt-get update
sudo aptitude upgrade
sudo apt-get upgrade

to upgrade straight away to feisty ....
> sudo sed -e 's/\sdapper/ feisty/g' -i /etc/apt/sources.list
sudo apt-get update
sudo aptitude upgrade
sudo apt-get upgrade 

---

