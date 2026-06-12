---
title: "apt-get update returns error :("
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by VictorGavrish on 2006-08-27
Can't istall some packages because a repository can't be downloaded.

```
victor@desktop:~$ sudo apt-get update
Password:
Ign http://packages.freecontrib.org dapper Release.gpg
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get: 2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://packages.freecontrib.org dapper Release
Get: 3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get: 4 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Ign http://packages.freecontrib.org dapper/free Packages
Get: 5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper Release
Ign http://packages.freecontrib.org dapper/non-free Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Ign http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Get: 6 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Errhttp://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 5s (1B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

My sources.list:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by Bachstelze on 2006-08-27
Weird error, seems like some file is corrupted in the repos... Anyway, try a local mirror of archive.ubuntu.com, I have no problem with fr.archive.ubuntu.com

---

### Post by VictorGavrish on 2006-08-27
Tried, same mistake :(
```
victor@desktop:~$ sudo apt-get update
Password:
Ign http://packages.freecontrib.org dapper Release.gpg
Get: 1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://packages.freecontrib.org dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Get: 2 http://fr.archive.ubuntu.com dapper Release.gpg [189B]
Get: 3 http://fr.archive.ubuntu.com dapper-updates Release.gpg [189B]
Ign http://packages.freecontrib.org dapper/free Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Get: 4 http://fr.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://fr.archive.ubuntu.com dapper Release
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://fr.archive.ubuntu.com dapper-updates Release
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://fr.archive.ubuntu.com dapper-backports Release
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://fr.archive.ubuntu.com dapper/main Packages
Hit http://packages.freecontrib.org dapper/non-free Sources
Hit http://fr.archive.ubuntu.com dapper/restricted Packages
Hit http://fr.archive.ubuntu.com dapper/universe Packages
Hit http://fr.archive.ubuntu.com dapper/multiverse Packages
Hit http://fr.archive.ubuntu.com dapper/main Sources
Hit http://fr.archive.ubuntu.com dapper/restricted Sources
Hit http://fr.archive.ubuntu.com dapper/universe Sources
Get: 5 http://fr.archive.ubuntu.com dapper/multiverse Sources [46.6kB]
Get: 6 http://fr.archive.ubuntu.com dapper-updates/main Packages [71.4kB]
Get: 7 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Get: 8 http://fr.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get: 9 http://fr.archive.ubuntu.com dapper-updates/universe Packages [15.4kB]
Get: 10 http://fr.archive.ubuntu.com dapper-updates/multiverse Packages [866B]
Ign http://fr.archive.ubuntu.com dapper-updates/multiverse Packages
Get: 11 http://fr.archive.ubuntu.com dapper-updates/main Sources [46.3kB]
Get: 12 http://fr.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get: 13 http://fr.archive.ubuntu.com dapper-updates/universe Sources [3129B]
Get: 14 http://fr.archive.ubuntu.com dapper-updates/multiverse Sources [427B]
Get: 15 http://fr.archive.ubuntu.com dapper-backports/main Packages [2446B]
Get: 16 http://fr.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get: 17 http://fr.archive.ubuntu.com dapper-backports/universe Packages [5451B]
Get: 18 http://fr.archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get: 19 http://fr.archive.ubuntu.com dapper-backports/main Sources [1449B]
Get: 20 http://fr.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get: 21 http://fr.archive.ubuntu.com dapper-backports/universe Sources [2002B]
Get: 22 http://fr.archive.ubuntu.com dapper-backports/multiverse Sources [435B]
Get: 23 http://fr.archive.ubuntu.com dapper-updates/multiverse Packages [773B]
99% [23 Packages gzip 0]                                             5134B/s 0s
gzip: stdin: not in gzip format
Errhttp://fr.archive.ubuntu.com dapper-updates/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 149kB in 39s (3760B/s)
Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Bachstelze on 2006-08-27
Very weird, they definitely work here... I guess you could just comment the multivers line out until it's fixed.

---

### Post by VictorGavrish on 2006-08-27
Well, I tried to wget the file and then unpack it manually, and it worked okay. Except it all happened in my home directory and obviously didn't affect apt-get's packages cache... So I think it's me that has a problem, not the repository.

---

### Post by Bachstelze on 2006-08-27
Try this :

backup your sources.list :

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

open the old one in gedit with 

```
gksudo gedit /etc/apt/sources.list
```

and delete everything so it's blank, then save it, close gedit and run

```
sudo apt-get update
```

then copy back your old sources.list

```
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
```

run *sudo apt-get update* again and see how it goes

---

### Post by linux major on 2006-08-27
Hi  i have been following this thred because i have the same problems see below. So i followed all the steps to the end andthis is the terminal replys when i run  sudo apt-get update

root@linux:/home/linux# sudo apt-get update
Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)]
:(

---

### Post by Bachstelze on 2006-08-27
This is not the same problem. Your problem is that you cannot connect to the repositories servers, maybe a proxy/firewall ?

---

### Post by VictorGavrish on 2006-08-27
Thanks a lot! It worked with no errors. :)

---

### Post by linux major on 2006-08-27
I am routed to the web via a router that uses nat/firewall. if i disable this function i can't get any connection to the web from linux?
regards

---

### Post by Bachstelze on 2006-08-27
Then you'll have to configure your router to let your Ubuntu box acces the web.

---

### Post by secretlondon on 2006-09-04
> **HymnToLife said:**
> Try this :


That worked! I'd read elsewhere that it was a problem with the repositories or something and had tried changing the country codes etc but to no avail..

---

### Post by michaelcarr on 2007-11-01
Your solution given quoted below worked great for my:
packages.gz gzip error (1)
when doing a system update for ubuntu 7.04

I read several discussions, but your solution seemed to be the most straight forward and least risky -- and it worked!!!

(Being really new to ubuntu, I would never have found this site if a Linux-Buddy hadn't sent me the link. Using the ubuntu provided help links and tools I got nowhere -- things like being referred to: search.ubuntu.com and it never being online are frustrating to say the least. But that is the way all things in the world are at times.)

Thanks to you, HymnToLife, and my good friend Mark Ahlstrom at the KTC Meditation Center.


Yours in Life,

Michael Carr

...

> **HymnToLife said:**
> Try this :

backup your sources.list :

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

open the old one in gedit with 

```
gksudo gedit /etc/apt/sources.list
```

and delete everything so it's blank, then save it, close gedit and run

```
sudo apt-get update
```

then copy back your old sources.list

```
sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list
```

run *sudo apt-get update* again and see how it goes

---

