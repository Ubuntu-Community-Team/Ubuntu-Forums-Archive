---
title: "Gutsy Update error"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by aabento on 2007-10-27
Hello
When I try to make update through the Update Manager  I always have the same error. :( I followed some posts in this subject but none solved this problem.
See below.
Some help?

Arnaldo




[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/B]
root@aabento001:/home/aabento# sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
root@aabento001:/home/aabento# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-gnome-support ghostscript ghostscript-x gnome-screensaver libgs8 libpng12-0 libssl0.9.8
  openssl
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/B]
root@aabento001:/home/aabento# sudo apt-get clean
[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download director[/B]y

---

### Post by nelson.bolanos on 2007-10-27
Are you using Feisty? the only version supported to upgrate from, is Feisty :D,

---

### Post by rosswmcgee on 2007-10-27
I had something similar, go to system/software sources and uncheck every thing. Then try it. Worked for me.

---

### Post by aabento on 2007-10-27
Hello 
I am saying update not upgrade Nelson Bolanos.

Rosswmcgee this does not solve the problem. :(

In any way thanks for the answers. 

Other solutions? :confused: :confused: :confused:

Arnaldo

---

### Post by aabento on 2007-10-28
Good morning!

It will be possible #-o that nobody knows how to eliminate this error?????:( 
Solution?:confused:
Clean installation?:confused:](*,)](*,)](*,)

Arnaldo

---

### Post by nyvalbanat on 2007-10-29
Hey guys,

It seems like your lock file was left behind after a crash or something. Open a terminal and type
sudo rm /var/cache/apt/archives/lock

This will remove the lock file. Worked for me.

Val

---

### Post by dantienn on 2007-11-10
I had the same problem, but with another program. 
It worked. Thanx nyvalbanat :)

---

### Post by aabento on 2007-11-24
Hello

Thanks nyvalbanat

For various reasons I had to reinstall this Gutsy again :confused: . And by second time I got the same error.
Using your help I solved this error twice.. :)

Arnaldo

---

### Post by Harry789 on 2007-11-30
I get this error


Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 193B in 1s (141B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
laan97ac@laan97ac-laptop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
laan97ac@laan97ac-laptop:~$ sudo rm /var/cache/apt/archives/lock
laan97ac@laan97ac-laptop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 5B in 4s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
laan97ac@laan97ac-laptop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
laan97ac@laan97ac-laptop:~$

---

### Post by PmDematagoda on 2007-11-30
Do:-
```

sudo dpkg --configure -a
```

To try and fix the problem.

---

### Post by Harry789 on 2007-12-01
that fixed it!

---

