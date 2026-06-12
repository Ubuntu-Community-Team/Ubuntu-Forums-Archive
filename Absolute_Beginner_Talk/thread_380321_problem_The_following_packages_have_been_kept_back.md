---
title: "problem: The following packages have been kept back"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-03-09
Hi,
I have been  using edgy for two days.
I was notified about a software updates.
Updates were in three groups:
security
recommended
distribution

it was impossible to select distribution updates. The rest were installed weel.
then I tried

sudo apt-get dist-upgrade
 then I got the following message

"The following packages have been kept back"

what does this mean and how can I fix this?
Thanks

---

### Post by Kobalt on 2007-03-09
It means that some packages were not installed because of some dependencies or conflict problems. What you can do is try to run these commands : 
```
sudo aptitude update -f
sudo aptitude upgrade
```
Then copy/paste us the complete result from the Terminal, if the problem is not solved.

---

### Post by mozkaynak on 2007-03-09
well I still have problem with that. here is the outcome:

> 
mozkaynak@ubuntu:~$ sudo aptitude update -f
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [38.4kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14.5kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [46.0kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [7576B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [4678B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [11.9kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [2463B]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 126kB in 2m0s (1044B/s)
Reading package lists... Done
mozkaynak@ubuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  dvd+rw-tools
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



why has dvd+rw-tools been kept back?

---

### Post by Stu_B on 2007-03-09
I'm getting possibly the same error on two dapper machines.


the following updates will be skipped
dvd+rw-tools

in the terminal I get

stu@stu-desktop:~$ sudo aptitude update -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:10 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
  Could not resolve ‘ubuntu.compiz.net’
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
  Could not resolve ‘ubuntu.compiz.net’
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Fetched 10B in 6s (1B/s)
Reading package lists... Done
stu@stu-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  dvd+rw-tools
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
stu@stu-desktop:~$


Many thanks for any help and your patience.

Stu

---

### Post by lamalex on 2007-03-09
that's usually not a problem. it's intentional by the devs. just wait and theyll be downloadable. nothing on your end.

---

### Post by Bachstelze on 2007-03-09
That's the risk that comes with using third party repos. Nothing you can do about is besides waiting for them to be up again or removing them.

---

### Post by Atreus12 on 2007-03-10
I am having the same problem with dvd+rw-tools

When I try to update it manually, here is what I get:
```
andrew@ubuntu:~$ sudo aptitude install dvd+rw-tools
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  dvd+rw-tools
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 138kB of archives. After unpacking 77.8kB will be used.
The following packages have unmet dependencies:
  dvd+rw-tools: Depends: genisoimage which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
dvd+rw-tools
ubuntu-desktop

Leave the following dependencies unresolved:
nautilus-cd-burner recommends dvd+rw-tools
gnomebaker recommends dvd+rw-tools
Score is -1052

Accept this solution? [Y/n/q/?]

```

Why would I have to remove 'ubuntu-desktop'?

---

