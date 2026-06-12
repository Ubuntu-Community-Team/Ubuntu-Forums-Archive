---
title: "unauthenticated software"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-02-04
Hi,

when updating with Update manager, I got the message that "You are about to install unauthenticated updates" - how shall I proceed?
[B]
ben@ben-desktop:~$ cat /etc/apt/sources.list[/B]
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by PmDematagoda on 2008-02-04
Post what you get using:-
```
sudo apt-get update
```

---

### Post by ben22 on 2008-02-04
ben@ben-desktop:~$ sudo apt-get update
[sudo] password for ben:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy Release 
Get:4 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates Release [58.5kB]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [66.7kB]
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Packages 
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Sources   
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Sources
Get:7 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Packages [127kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [12.1kB]      
Get:10 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Packages [4031B]
Get:11 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Sources [30.7kB]
Get:12 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]    
Get:13 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Packages [50.7kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [41.6kB]
Get:16 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Sources [8939B]     
Get:17 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Packages [9220B]  
Get:18 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Sources [1702B]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [5718B]      
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2901B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]
Fetched 473kB in 5s (85.9kB/s)                             
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Seisen on 2008-02-04
The error you have now is because you probably have synaptic or add/remove programs open so close whichever one you have and then rerun ```
sudo apt-get update
```

---

### Post by ben22 on 2008-02-04
now I get>

ben@ben-desktop:~$ sudo apt-get update
[sudo] password for ben:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Translation-en_US         
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Translation-en_US           
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Translation-en_US         
Get:2 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates Release.gpg [191B]         
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Translation-en_US       
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US 
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Translation-en_US   
Ign [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy Release 
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates Release              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Packages                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/main Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/universe Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done


what now?

---

### Post by jan quark on 2008-02-04
try to install the software again
and post any error messages

besides what software do you want to install?

---

### Post by emarkd on 2008-02-04
That last output you listed from apt-get update is correct.  The command just rereads the contents of the repositories you're set up to use so that you've got an updated local list for searching in Synaptic or whatever.  You should work properly now.

If you're getting a "installing unauthenticated software" message, it's because you don't have the gpg key for one of the repositories you've added to Synaptic.  You can go back to whereever you got the repository address and try to find the address to the key if you want to fix it.

---

### Post by Seisen on 2008-02-04
There are some repositories that do not have GPG keys so that apt can authenticate them, So when you install software from that repository it will give you that error.

---

