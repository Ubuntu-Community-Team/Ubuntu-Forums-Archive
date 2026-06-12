---
title: "[SOLVED] Too new to know what my problem is?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Greenskycity on 2007-12-17
ok, Ubuntu has been a breeze up to now and this forum has pulled me out of the fire many times.  but now I'm stuck and thought I'd post for some help.  The problem is, that I don't know what my problem is.  Let me explain......
I can't install anything, whether it be Wine, CCSM or clock.  when the repositories list refreshes I get an error saying that there are repositories indexes that can not be found.
so I only download 39 of 41 indexes and they are:
archive.ubuntu.com/ubuntu/dists/gutsy/release: unable to find expected entry web/binary-1386/packages in meta-index file (malformed release file?)
the next one says:
archive.ubuntu.com/ubuntu/dists/gutsy-updates/release: unable to find expected entry web/binary-1386/packages in meta-index file (malformed release file?)
and the third one says:
archive.ubuntu.com/ubuntu/dists/gutsy-security/release:unable to find expected entry web/binary-1386/packages in meta-index file (malformed release file?)

The warning than says that an older version will be used or the whole thing will be ignored, or something along those lines.  So after that I say ok and it tries to install an application and then I get a text box that says that e.g. "clock can not be installed on your computer type (i386)"  "either the application requires special hardware features or the vendor decided not to support your hardware type"

It kinda sounds like something thinks im running 64 bit version but Im running 32 bit.

output of get upgrade is this:
```
jason@gutsy-710:~$ sudo apt-get upgrade
[sudo] password for jason:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@gutsy-710:~$ 

```

and update is this:
```
jason@gutsy-710:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                     
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                   
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/web Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US
Get:3 http://packages.medibuntu.org gutsy Release.gpg [189B]
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/web Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Get:4 http://archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/web Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release    
Ign http://packages.medibuntu.org gutsy/free Packages
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://archive.ubuntu.com gutsy-security Release                
Ign http://packages.medibuntu.org gutsy/non-free Packages           
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://archive.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy-security/restricted Packages
Fetched 4B in 1s (3B/s)  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jason@gutsy-710:~$ 


```

notice the errors on the end of that one.  Of all the problems I am having, I think this is the catalyst of them.  and for good measure, heres my sources.lst

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted web

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted web

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted web
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
```

Sorry for the long post and probable uneeded info, I'm a newb so any help would be great.
Green

---

### Post by Anicka on 2007-12-17
The problem is that there is no ubuntu-repo that have the "option" web. In a few places in you source list you have the word "web" after the URL, I have never seen it before, and apt-get is complaining about it, so you should edit it out. To do so you need to be root:```
gksudo gedit /etc/apt/sources.list
```

---

### Post by lswest on 2007-12-17
also, try going to system--->preferences--->software sources (or something along those lines) and disable the cdrom repository, as it has a higher precedence over net-based installs, and could be causing some problems with installs.

---

### Post by Anicka on 2007-12-17
After some googling I might have found a solution.
1) Go to software sources, untick the CD and choose a mirror of your choice (not the one you have now).
2) Reload your sources "sudo apt-get update".
3) Try to install what you wanted.

---

### Post by Greenskycity on 2007-12-17
Anicka- You are my hero, that worked!  I got to install CCSM finally.  thanks.
One question because I want to know why and not just how.... was the "web" part of the filename that was being looked for and thats why it wasn't found?  just by looking to me, it seems that this out of my sources:
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
and this out of my update:
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)

These dont look to me to be pointing to the same place.  or was it something else that caught your eye, I only ask becasue even knowing the answer, I don't know how it was gotten to.  Thanks.
Green

---

### Post by Anicka on 2007-12-17
Well, I'm not quite sure, but the line you put in your source list "http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted" points to the URL "http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/". In there you have the Release-file with the name of all available files in the folder gutsy-updates. The "main restricted" means that you only look in the sub-folders main and restricted. There are also universe and multiverse.

For the solution of your problem, I think that disabling the CD as Iswest suggested was the key, but somewhere (I don't remember where) I saw that changing the mirror helped instead, so why not do both?

I have used Ubuntu for little over one year, and I have learned a lot by reading the forums, but maybe even more by googling on the error-messages, reading maybe ten different versions of the problem and trying to connect the dots. A bit too often people get an error-message and they write a post, screaming "bug". Most guys in the forums are nice and answer, but the original poster would have learned more by trying to find the problem himself. But we are all of us more or less beginners so when I post with problems, more advanced users would think I'm lazy not finding the solution.

I hope you have learned something new today, I have by trying to help you.

---

### Post by fiik on 2007-12-17
Anicka
I have similar problems,  How do I 'untick cd-rom' or disable cd-rom repositories? Add/Remove/Preferences gets me to Software Sources.  to install from cd-rom insert the medium into the drive

---

### Post by Anicka on 2007-12-17
fiik: If you have the message "to install from cd-rom insert the medium into the drive", the CD is not enabled for installation. As I wrote before, you might want to try to change the mirror for your download, reload and see what happens. If you want any further help, you will need to post something informative: error-messages, source-list and so on.

---

### Post by total_absolute_n00b on 2008-02-12
raaa really sorry to post such a stupid message i must seem like such a well...have an identical setup to described above, (the exact same error message and again not running a 64 bit processor

This is after un-checking the cdrom tick box thing-y and changing the mirror (to several different ones) it is still looking in the /web thing the things that come up are below when typing those commands in:

Really sorry but if anyone can put me out of my misery I can be happy without this thing bugging the life out of me..,:KS


geoff@geoff-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
geoff@geoff-laptop:~$ 

geoff@geoff-laptop:~$ sudo apt-get update
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Get: 2 [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy Release.gpg [191B]
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/main Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/restricted Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/web Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/universe Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/multiverse Translation-en_GB
Get: 3 [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates Release.gpg [191B]
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/main Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/restricted Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/web Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/universe Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/multiverse Translation-en_GB
Get: 4 [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security Release.gpg [191B]
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/main Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/restricted Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/web Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/universe Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/multiverse Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates Release
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security Release
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-updates/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy-security/restricted Packages
Fetched 4B in 0s (7B/s)
Failed to fetch [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
geoff@geoff-laptop:~$

---

### Post by Anicka on 2008-02-20
You still have problems "total"? If yes, try changing the mirror to something else.

---

