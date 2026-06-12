---
title: "Update Manager Crash Causing Big Bugs, Dead Synaptic Package Manager"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by TBayCrusher on 2006-12-07
While Running The Update Manager After A ReStart, There Were 11 Updates, It Froze During The 2nd Install. Total LockUp For Hours, No Movement. So I OverRode & Manually Restarted. Upon Returning I Tried To Continue The Updates, But Now It Told Me "Only One Software Management Tool Is Allowed To Opperate At The Same Time." & "Please Close Other Applications First" 
Then, When Opening The Synaptic Package Manager, I Got The Message That I Had To "Manually Run dpkg to Fix A Problem" & "There's Problems Found With The System" & "W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages)"
I've Searched The Forums Here To Find The Answer, Have Seen These Things Discussed, But No Direct Answers. 
If This Was Win](*,)doze I'd Normally Be Ripping My Skin Off By Now 
But Since It's Ubuntu I'm Hoping There's A Simple Solution? 
Overly Optimistic  Ascertion? 
Any Ideas About How to Fix This?

---

### Post by bapoumba on 2006-12-07
> **TBayCrusher said:**
>  "W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages

One good idea is to paste the complete error messages ;)

This one tells you that a repository shows up twice in your source.list file. So please paste the complete output of **cat /etc/apt/sources.list** and **sudo apt-get update**.

---

### Post by TBayCrusher on 2006-12-07
This Is The Update Manager Message 

Only one software management tool is allowed to run at the same time
Please close the other application e.g. 'aptitude' or 'Synaptic' first.


& The Original Error Message With The Links Doesn't Seem To Be Coming Up Now  
Instead It's Coming Up As This One When I Click The SynapticPkgMngr

The following problems were found on your system:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

& Can't Seem To Find The cat /etc/apt/sources.list and sudo apt-get update Outputs You Spoke Of :???:

---

### Post by bapoumba on 2006-12-07
Okay, first close synaptic and update-manager, then open a terminal (in GNOME > Accessories > Terminal), paste the first command, hit return, and paste the output in here. Same thing for the second command.

Your first error message tells you were probably running update-manager and synaptic (they use the same lock, only one package manager can run at a time).

The second error message indicates to run **sudo dpkg --configure -a** to correct install problems. Please forget about this one for the moment.

---

### Post by TBayCrusher on 2006-12-07
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by TBayCrusher on 2006-12-07
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Fetched 10B in 2s (4B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by bapoumba on 2006-12-07
You actually have multiple entries in you sources.list file.  

1- backup this file :
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

2- edit the file :
```
gksudo gedit /etc/apt/souces.list
```

3- **replace** the content of the file with :

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main 
```

4- Save the file.

5- run :
```
sudo apt-get update
```

6- If you get the same error as before, run :
```
sudo dpkg --configure -a
```

---

### Post by TBayCrusher on 2006-12-11
I Think It's Now Working More Correctly
Hopefully I Didn't Do Some Unforseen Damage While "Fixing" This 
Thanks For The Tips Here

---

### Post by bapoumba on 2006-12-11
hello,

as far as your new dapper sources.list, you can have a look [here]("http://psychocats.net/ubuntu/sources"). I just left out the freecontrib repositories, and pasted what was relevant to your situation ;)

The **sudo dpkg --configure -a** fix was recommended in one of your error messages. Please run **man dpkg** in a terminal for further informations.
[quote=man dpkg] dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a or -pending is given instead of package, all unpacked but unconfigured packages are configured.
[/quote]

---

