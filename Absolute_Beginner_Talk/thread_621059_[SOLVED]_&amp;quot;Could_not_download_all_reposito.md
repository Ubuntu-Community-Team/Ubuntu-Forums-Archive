---
title: "[SOLVED] &amp;quot;Could not download all repository indexes&amp;quot;"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-23
When I try Add/Remove... or Update Manager, I get this error message saying "**Could not download all repository indexes**". It goes on to say > The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
The links listed are: > [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

Things were fine till yesterday.

What does this mean and how do I fix it?

Thanks.

---

### Post by taurus on 2007-11-23
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
If you still get the same warning message, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by kleo skywalker on 2007-11-23
When I do ```
sudo apt-get update
``` I get > Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN       
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IN               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/web Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IN                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/web Translation-en_IN
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/web Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Fetched 5B in 2s (2B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
When I do ```
sudo apt-get upgrade
``` I get > Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When I do ```
cat /etc/apt/sources.list
``` I get > deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


I don't what it means though.

---

### Post by kleo skywalker on 2007-11-24
bump

---

### Post by stinger30au on 2007-11-24
i had the exact same problem with 7.10 a few days ago.

i turned the pc off before i caught some shut eye.

tried it in the morning and it worked fine.

i can only assume they may have been doing some maintenance on the server.

its all good now and i never touched a thing

---

### Post by Partyboi2 on 2007-11-24
In your 
/etc/apt/sources.list you need to uncomment all the lines that start with
deb and deb-src
eg.      # deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
will become:
          deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
          #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
will become:
          deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
Remove #
then Save. Then type:
```
sudo apt-get update
```

---

### Post by kleo skywalker on 2007-11-24
> **stinger30au said:**
> i had the exact same problem with 7.10 a few days ago.

i turned the pc off before i caught some shut eye.

tried it in the morning and it worked fine.

i can only assume they may have been doing some maintenance on the server.

its all good now and i never touched a thing

I already did that - I mean I tried the next day and the problem was still there.

---

### Post by kleo skywalker on 2007-11-24
> **Partyboi2 said:**
> In your 
/etc/apt/sources.list you need to uncomment all the lines that start with
deb and deb-src
eg.      # deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
will become:
          deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
          #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
will become:
          deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
Remove #
then:
```
sudo apt-get update
```

I'll try this, but I have a question - I never touched this file, and hadn't faced any problems till yesterday. If the "#" things are causing the problem, then how come this didn't happen before? 
Also, why does it say > Line commented out by installer because it failed to verify: before all the lines where deb and deb-src are preceded by #? What does that mean?
Thanks.

---

### Post by Partyboi2 on 2007-11-24
Anything with a # in front of it means that it is ignored by the apt-get, when there is no # in front of something apt-get will read it.
As you can see by looking through the source list there are some that are uncommented. Which are the ones that you get a hit on when you
sudo apt-get update
the ones that are commented out on your source list is the ones that apt-get ignore.
That is my understanding of it, someone else might be able to explain it better.

---

### Post by danbrownlow on 2007-11-24
Hey, I had this problem, I went to to:
 File System/etc/apt/ then click the sources.list file. Check all the boxers and try again. Hopefully it should work then.

---

### Post by kleo skywalker on 2007-11-26
> **Partyboi2 said:**
> In your 
/etc/apt/sources.list you need to uncomment all the lines that start with
deb and deb-src
eg.      # deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
will become:
          deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
          #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
will become:
          deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
Remove #
then Save. Then type:
```
sudo apt-get update
```

I don't know the right way to edit this file, so I used ```
gksudo nautilus
```
I uncommented all lines beginning with deb or deb-anything, and saved it. But when I ran Update Manager, I got a similar error message, and this time the list was longer. so I checked Software Sources, and it turns out that editing made an unintended change - the "Unsupported updates (gutsy-backports)" box which was unchecked before was not unchecked anymore.
So I unchecked it, and it reloaded the repository list, and gave me the same error message as before.
I don't know what it means or how to fix it.

---

### Post by Partyboi2 on 2007-11-26
This is what it I meant, I have changed the sources.list that you posted: 

 ```
gksudo gedit /etc/apt/sources.list
``````
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
  deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
  deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 # deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
```If you want you can copy and paste this into your source.list 
Backup your old one if you like:
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak 

```then delete the contents of /etc/apt/sources then copy and paste this one that I have changed.
then
```
sudo apt-get update
```Or you can generate a new source list from here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by kleo skywalker on 2007-11-27
Partyboi2, I did exactly as you posted (actually with the exception of uncommenting the backport lines, I had done the same thing before!) but I get the same error:
> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Partyboi2 on 2007-11-27
>  W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis  ts_gutsy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dis ts_gutsy-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problemsrunning
```
sudo apt-get update
```Should get rid of the Duplicate.
As for the
 > Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)I had a google on the error and didn't get much. But there were a few that fixed the error by re generating there source.list
Here are their threads:
[http://ubuntuforums.org/showthread.php?p=3780232](http://ubuntuforums.org/showthread.php?p=3780232)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3671415](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3671415)
You could try regenerating your source.list and see if that works
you can get a new one from here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
otherwise I am out of ideas. Sorry.

---

### Post by plucky on 2007-11-28
Don't know if this helps , but looking through your sources.list

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse **web**
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted **web**
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted **web**
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

the words in bold should not be there, comment them out and retry 
```
sudo apt-get update
```

cheers

---

### Post by saracen on 2007-12-01
I had this same problem.  Commented out the "web" as suggested and it was fixed.  I'd like to know how they got into my sources.list - I certainly didn't put them there myself...

---

### Post by kleo skywalker on 2007-12-21
I regenerated the source list from here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) as Partyboi2 suggested, and the problem is fixed. Thanks everyone!

---

