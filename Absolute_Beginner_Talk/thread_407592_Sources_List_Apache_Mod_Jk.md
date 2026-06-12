---
title: "Sources List? Apache Mod Jk"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by dueces on 2007-04-12
I am trying to install 
apt-get install libapache2-mod-jk

but I cant seem to download it, I uncommented out all the sources in the list but I still dont get anything? 

Sorry a newbie? Am I missing something?

---

### Post by compmodder26 on 2007-04-12
Post your sources.list for us.  I'm running dapper server and I have libapache2-mod-jk.

---

### Post by NICU on 2007-04-12
You may need to try to update your repositories first using ```
sudo apt-get update
``` I'm not around to see where this package is located, but if it doesn't work after updating your repositories, you can try using Synaptic to install it.

---

### Post by compmodder26 on 2007-04-12
By the way, It should be in the universe repository.

---

### Post by dueces on 2007-04-12
I ran the update and then tried to do 
sudo apt-get install libapache2-mod-jk but no luck it says cant find package?

---

### Post by compmodder26 on 2007-04-12
You have to have the universe repository enabled.  Please post your sources.list.

---

### Post by dueces on 2007-04-12
#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ d
apper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dap
per main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ
erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
universe multiverse


"sources.list" [readonly] 39L, 1992C                          1,1           Top

---

### Post by compmodder26 on 2007-04-12
You haven't uncommented the universe repositories.  They are in the middle of the file

---

### Post by dueces on 2007-04-12
I tried that new list is: says it cant find it?
#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ d
apper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dap
per main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer
se multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un
iverse multiverse

---

### Post by dueces on 2007-04-12
possibly I am trying to download the wrong file?

---

### Post by dante on 2007-04-12
Try commenting the line that refers to your cdrom drive.  Even if that
doesn't fix your current problem, it'll ensure you are getting the latest
packages from the repositorys, rather than your CD...and you won't be
prompted to put your CD in when you go do to an 'apt-get upgrade'

---

### Post by dueces on 2007-04-12
Thanks Dante. I did that but it still cannot find it. Sucks been at this for 3 days and all I need it this package!

---

### Post by dante on 2007-04-12
What do you get if you run this command:

apt-cache search mod-jk

---

### Post by compmodder26 on 2007-04-12
After uncommenting those lines, did you do "sudo apt-get update" before doing "sudo apt-get install libapache2-mod-jk"?

---

