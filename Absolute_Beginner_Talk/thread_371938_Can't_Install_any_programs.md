---
title: "Can't Install any programs"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Cre-ve on 2007-02-27
Hey all I just install ubuntu yesturday. I'm trying to get programs to download though apt-get however none of them seem to be working.

I tried sudo apt-get install opera: and i get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplay
soumak@soumak-linux:~$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

i tried sudo apt-get install realplay: and i get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplay

i also tried sudo aptitude update && sudo aptitude install firefox: and i get:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 3B in 6s (0B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done



is there something i'm doing wrong? or do those 2 things just not work?

---

### Post by taurus on 2007-02-27
You need to enable both universe and multiverse in /etc/apt/sources.list before you can install opera.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines with deb at the beginning.  Save it and run

```
sudo aptitude update
sudo aptitude install opera
```

---

### Post by annda on 2007-02-27
check you repositories (system > administration > software sources) you mighgt need to check universe and multiverse for those programs/packages. and then do:
```
sudo apt-get update
```
before trying to install.

---

### Post by Cre-ve on 2007-02-27
NM. i'm still getting the same thing. although it did update. do i need to restart it after the update?

---

### Post by oilchangeguy on 2007-02-27
these programs can easily be installed via automatix.

---

### Post by igknighted on 2007-02-27
I think opera and realplayer are in the commercial repo on Cannonical servers, not the Ubuntu repos.  The firefox message you are getting is because firefox is already installed.

EDIT: You can add this repo, but I don't know the address... a quick search should turn it up tho.

---

### Post by picpak on 2007-02-27
If you install RealPlayer and Opera through Applications > Add/Remove, it will automatically add that repo.

---

### Post by Cre-ve on 2007-02-27
i THINK i got it its installing opera now..i think:


Solution:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) -- Enabling Extra Repositories

---

