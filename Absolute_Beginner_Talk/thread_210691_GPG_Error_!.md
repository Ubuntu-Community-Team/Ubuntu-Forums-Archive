---
title: "GPG Error !"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-07
Ok,I'm getting this:

I think I did all the steps right on [http://www.getautomatix.com/](http://www.getautomatix.com/) ,but here we go

drakkor@drakkor:~$ wget [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
--04:21:22-- [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
=> `key.gpg.asc.2'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.97.133.175
Connecting to www.beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730 --.--K/s

04:21:22 (11.70 MB/s) - `key.gpg.asc.2' saved [1730/1730]

drakkor@drakkor:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg: unchanged: 1
drakkor@drakkor:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
drakkor@drakkor:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [2743B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:10 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get:11 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:12 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [2743B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:13 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [335B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Fetched 6207B in 5s (1142B/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>
W: You may want to run apt-get update to correct these problems
drakkor@drakkor:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
automatix
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.2kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main automatix 6.2-9-6.06dapper1 [30.2kB]
Fetched 30.2kB in 0s (121kB/s)
(Reading database ... 90472 files and directories currently installed.)
Preparing to replace automatix 6.2-4-6.06dapper1 (using .../automatix_6.2-9-6.06dapper1_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (6.2-9-6.06dapper1) ...
drakkor@drakkor:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:3 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get:4 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release

Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:8 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [2743B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 2941B in 1s (1696B/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>
W: You may want to run apt-get update to correct these problems
drakkor@drakkor:~$  ](*,)

---

### Post by arnieboy on 2006-07-07
delete the line from your sources.list which says:
> deb [http://www.getautomatix.com/dapper](http://www.getautomatix.com/dapper)......
save and exit and do a 
```
sudo apt-get update
```
now install automatix.

---

### Post by Drakkor on 2006-07-07
OK,arnieboy, did remove deb [http://www.getautomatix.com/dapper](http://www.getautomatix.com/dapper)......
Went into Synaptic and automatix was still there so I ininstaled it and reinstalled it,Did sudo apt-get update and got this: I assume it's ok now ?

drakkor@drakkor:~$ sudo apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get:2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 9B in 1s (5B/s)
Reading package lists... Done
drakkor@drakkor:~$

---

### Post by greggh on 2006-07-07
Just reinstall by following the directions exactly in the first post of the following thread

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by arnieboy on 2006-07-07
> **Drakkor said:**
> OK,arnieboy, did remove deb [http://www.getautomatix.com/dapper](http://www.getautomatix.com/dapper)......
Went into Synaptic and automatix was still there so I ininstaled it and reinstalled it,Did sudo apt-get update and got this: I assume it's ok now ?

drakkor@drakkor:~$ sudo apt-get update
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get:2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 9B in 1s (5B/s)
Reading package lists... Done
drakkor@drakkor:~$

yes.

---

### Post by Drakkor on 2006-07-07
YAY !! :p  Thanks, arnieboy !

---

