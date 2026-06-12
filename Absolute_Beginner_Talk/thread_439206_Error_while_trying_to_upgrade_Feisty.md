---
title: "Error while trying to upgrade Feisty"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-05-10
I get this error when I tried to upgrade to Feisty via Update Manager
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz Podproces gzip je vrnil kodo napake (1)

```

Is there maybe something wrong with my sources.list?

---

### Post by ltk5 on 2007-05-10
bump

---

### Post by Najand on 2007-05-10
Close your Update manager.
Open a terminal and update your apt:
```

sudo apt-get update && sudo apt-get upgrade 

```
and then try to upgrade it again.

---

### Post by ltk5 on 2007-05-10
yup, it looks as it's the sources.list again. I'll check for a list here on the forums. thanks
```
lotko@lotko-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Dobi:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Prz http://security.ubuntu.com edgy-security/main Translation-sl               
Dobi:2 http://wine.lowvoice.nl edgy Release.gpg [191B]                         
Prz http://wine.lowvoice.nl edgy/main Translation-sl                           
Dobi:3 http://archive.canonical.com edgy-commercial Release.gpg [191B]         
Prz http://archive.canonical.com edgy-commercial/main Translation-sl           
Dobi:4 http://archive.ubuntu.com edgy Release.gpg [191B]                       
Prz http://archive.ubuntu.com edgy/main Translation-sl                         
Prz http://security.ubuntu.com edgy-security/restricted Translation-sl         
Prz http://security.ubuntu.com edgy-security/multiverse Translation-sl         
Prz http://security.ubuntu.com edgy-security/universe Translation-sl           
Zadetek http://wine.lowvoice.nl edgy Release                                   
Zadetek http://archive.canonical.com edgy-commercial Release                   
Prz http://archive.ubuntu.com edgy/restricted Translation-sl                   
Prz http://archive.ubuntu.com edgy/universe Translation-sl                     
Prz http://archive.ubuntu.com edgy/universe Translation-sl                     
Prz http://archive.ubuntu.com edgy/multiverse Translation-sl                   
Prz http://archive.ubuntu.com edgy/multiverse Translation-sl                   
Prz http://archive.ubuntu.com edgy/universe Translation-sl                     
Zadetek http://security.ubuntu.com edgy-security Release                       
Dobi:5 http://www.getautomatix.com edgy Release.gpg [189B]                     
Prz http://www.getautomatix.com edgy/main Translation-sl                       
Prz http://wine.lowvoice.nl edgy/main Packages                                 
Zadetek http://archive.canonical.com edgy-commercial/main Packages
Dobi:6 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Prz http://archive.ubuntu.com edgy-updates/main Translation-sl                 
Prz http://archive.ubuntu.com edgy-updates/restricted Translation-sl           
Prz http://archive.ubuntu.com edgy-updates/universe Translation-sl             
Zadetek http://security.ubuntu.com edgy-security/main Packages 
Zadetek http://wine.lowvoice.nl edgy/main Packages             
Prz http://archive.ubuntu.com edgy-updates/multiverse Translation-sl
Prz http://archive.ubuntu.com edgy-updates/multiverse Translation-sl
Prz http://archive.ubuntu.com edgy-updates/universe Translation-sl
Zadetek http://security.ubuntu.com edgy-security/restricted Packages
Zadetek http://security.ubuntu.com edgy-security/main Sources
Zadetek http://security.ubuntu.com edgy-security/restricted Sources
Dobi:7 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Prz http://archive.ubuntu.com edgy-backports/main Translation-sl         
Prz http://archive.ubuntu.com edgy-backports/restricted Translation-sl
Zadetek http://www.getautomatix.com edgy Release               
Prz http://archive.ubuntu.com edgy-backports/universe Translation-sl
Prz http://archive.ubuntu.com edgy-backports/multiverse Translation-sl
Dobi:8 http://archive.ubuntu.com edgy-security Release.gpg [191B]
Prz http://archive.ubuntu.com edgy-security/main Translation-sl
Zadetek http://security.ubuntu.com edgy-security/multiverse Packages
Zadetek http://security.ubuntu.com edgy-security/universe Packages
Prz http://archive.ubuntu.com edgy-security/restricted Translation-sl
Prz http://archive.ubuntu.com edgy-security/universe Translation-sl
Prz http://archive.ubuntu.com edgy-security/multiverse Translation-sl
Dobi:9 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]
Prz http://archive.ubuntu.com edgy-proposed/restricted Translation-sl
Prz http://archive.ubuntu.com edgy-proposed/main Translation-sl
Zadetek http://www.getautomatix.com edgy/main Packages
Prz http://archive.ubuntu.com edgy-proposed/multiverse Translation-sl
Prz http://archive.ubuntu.com edgy-proposed/universe Translation-sl
Zadetek http://archive.ubuntu.com edgy Release
Zadetek http://archive.ubuntu.com edgy-updates Release
Zadetek http://archive.ubuntu.com edgy-backports Release
Zadetek http://archive.ubuntu.com edgy-security Release
Zadetek http://archive.ubuntu.com edgy-proposed Release
Zadetek http://archive.ubuntu.com edgy/main Packages
Zadetek http://archive.ubuntu.com edgy/restricted Packages
Zadetek http://archive.ubuntu.com edgy/main Sources
Zadetek http://archive.ubuntu.com edgy/restricted Sources
Zadetek http://archive.ubuntu.com edgy/universe Packages
Zadetek http://archive.ubuntu.com edgy/universe Sources
Zadetek http://archive.ubuntu.com edgy/universe Packages
Zadetek http://archive.ubuntu.com edgy/multiverse Packages
Zadetek http://archive.ubuntu.com edgy/multiverse Packages
Zadetek http://archive.ubuntu.com edgy/universe Packages
Prz http://archive.ubuntu.com edgy-updates/main Packages
Zadetek http://archive.ubuntu.com edgy-updates/restricted Packages
Zadetek http://archive.ubuntu.com edgy-updates/main Sources
Zadetek http://archive.ubuntu.com edgy-updates/restricted Sources
Zadetek http://archive.ubuntu.com edgy-updates/universe Packages
Zadetek http://archive.ubuntu.com edgy-updates/multiverse Packages
Zadetek http://archive.ubuntu.com edgy-updates/multiverse Packages
Zadetek http://archive.ubuntu.com edgy-updates/universe Packages
Zadetek http://archive.ubuntu.com edgy-backports/main Packages
Zadetek http://archive.ubuntu.com edgy-backports/restricted Packages
Zadetek http://archive.ubuntu.com edgy-backports/universe Packages
Zadetek http://archive.ubuntu.com edgy-backports/multiverse Packages
Zadetek http://archive.ubuntu.com edgy-security/main Packages
Zadetek http://archive.ubuntu.com edgy-security/restricted Packages
Zadetek http://archive.ubuntu.com edgy-security/universe Packages
Zadetek http://archive.ubuntu.com edgy-security/multiverse Packages
Zadetek http://archive.ubuntu.com edgy-proposed/restricted Packages
Zadetek http://archive.ubuntu.com edgy-proposed/main Packages
Zadetek http://archive.ubuntu.com edgy-proposed/multiverse Packages
Zadetek http://archive.ubuntu.com edgy-proposed/universe Packages
Dobi:10 http://archive.ubuntu.com edgy-updates/main Packages [103kB]
99% [10 Packages gzip 0]           
gzip: stdin: not in gzip format
Nap http://archive.ubuntu.com edgy-updates/main Packages
  Podproces gzip je vrnil kodo napake (1)
Dobljenih 10B v 1s (7B/s)
Ni mogo&#269;e dobiti http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  Podproces gzip je vrnil kodo napake (1)
Branje seznama paketov... Narejeno
E: Nekaterih kazal ni mogo&#269;e prenesti, zato so preklicana, ali pa so uporabljena starejša.

```

---

### Post by Najand on 2007-05-10
OK, I see you need to do the following command before updating it.
```

sudo apt-get clean && sudo apt-get autoclean

```
Then try:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by ltk5 on 2007-05-10
it helped a bit, but it still gives me some errors
```
99% [10 Packages gzip 0]           
gzip: stdin: not in gzip format
Nap http://archive.ubuntu.com edgy-updates/main Packages
  Podproces gzip je vrnil kodo napake (1)
Dobljenih 10B v 4s (2B/s)
Ni mogo&#269;e dobiti http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  Podproces gzip je vrnil kodo napake (1)
Branje seznama paketov... Narejeno
E: Nekaterih kazal ni mogo&#269;e prenesti, zato so preklicana, ali pa so uporabljena starej&#353;a.

```

my source.list is:
```
lotko@lotko-desktop:~$ cat /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt edgy main

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

```

do you think it would upgrade if I ran the 'update manager'?

---

### Post by Najand on 2007-05-10
For upgrading you just need:
```

deb http://si.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://si.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

deb http://si.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse

```
So disable others and try again. (I think using si mirrors which is in Slovenia is faster in your case.)

---

### Post by ltk5 on 2007-05-10
Ok. apt-get update/upgrade didn't show any errors. I'll try upgrading now:)


edit: ok, upgrading works now. Atm it's 'modifying the software channels' :D. I'm just curious about something; 
I've had so many sources in my sources.list and yet there weren't enought/they were missing. 
Are the ones you supplied the general ones and I can keep them, or should I later un-comment the previous lines?

---

### Post by ltk5 on 2007-05-10
Damn!
After finishing with the software channels, it gave me an error:

Failed to fetch [http://si.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://si.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) Podproces gzip je vrnil kodo napake (1)

which looks allot like the first one I got; it also says this error could happen because of the problems with the networking.

---

### Post by Najand on 2007-05-10
Hmm, It seems you are behind a proxy server or have an unstable internet connection. That is why it happens.

---

### Post by ltk5 on 2007-05-10
Ok thanks. I'll try again in few days. Yesterday and the day before's been raining and 
thundering a lot. Maybe their repairing it..

I just hope that's the reason:)

---

### Post by Najand on 2007-05-10
I hope so.... Just remember everytime it happens you need to clean the apt library (sudo apt-get clean && sudo apt-get autoclean) and then update it again.

---

### Post by ltk5 on 2007-05-12
Ok.
I've upgraded my system. Thanks for your help.

---

