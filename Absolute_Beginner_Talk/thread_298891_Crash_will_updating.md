---
title: "Crash will updating"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by goldenatom on 2006-11-13
I was doing an update the other day and the computer crashed half way through, any ideas on how I fix this? 

```
joe@joe-desktop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libavahi-common3 libavahi-core4
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/134kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptordpkg-deb: `/var/cache/apt/archives/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `/var/cache/apt/archives/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb
 /var/cache/apt/archives/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by taurus on 2006-11-13
What happens if you run these two commands again?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by goldenatom on 2006-11-13
Same thing.

---

### Post by taurus on 2006-11-13
Let's have a look at your /etc/apt/sources.list (Applications -> Accessories -> Terminal).

```
less /etc/apt/sources.list
```

---

### Post by goldenatom on 2006-11-13
```
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.compiz.net/ edgy main-edgy

deb http://amaranth.selfip.com edgy lrm

```

---

### Post by Bachstelze on 2006-11-13
try

*sudo apt-get -f install*

---

### Post by goldenatom on 2006-11-13
I tried that and got this 

```
joe@joe-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
joe@joe-desktop:~$ 


```

---

### Post by arnieboy on 2006-11-13
what are you using Amaranth's repository for?
you can try deleting the following files because they are broken:
```
sudo rm -f /var/cache/apt/archives/libavahi-common3_0.6.13-2ubuntu2.2_i386.deb
 /var/cache/apt/archives/libavahi-core4_0.6.13-2ubuntu2.2_i386.deb
```
then try doing a 
```
sudo apt-get update
```
If you still get the error, try commenting out Amaranth's repo. However I am not sure where the avahi packages are coming from.

---

### Post by goldenatom on 2006-11-13
That worked...and I should have thought of that, duh. Thanks. I used the repo to get the nvidia driver.

---

