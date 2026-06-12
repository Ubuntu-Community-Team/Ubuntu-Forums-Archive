---
title: "Upgrade wows 7.04 to 7.10"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by P&amp;P on 2007-11-10
[COLOR="Indigo"]Hello all. I am a very new newbie.  Last week I cut my Linux teeth with 7.04 , apart from hiccups with connecting to the net via router all else seems on the face of to work.  I have now been hitting a brick wall with the update manager and when trying to UPGRADE to 7.10.
The errors I am getting are:
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2]("http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2")
Sub-process bzip2 returned an error code (2) 
I cannot figure out : "....... Check your network connection and the correct writing of the repository address in the preferences...." that accompanies a failed update or upgrade attempt. What and where Is "repository address in the preferences"?
I have scoured the forums, one guy appears to have had  the same problem but I just couldn't grasp what worked for him  it was  beyond my limited comprehension.

Many thx in eager anticipation to resolve this one.
P.S.
Downloaded and burnt a copy 7.10  but  that will not offer just the Upgrade  option.
Did update 4 days ago OS 7.04. without a problem.
Did have a Nvidia driver problem and had to reboot from hand coding to get back to desktop
(could any of this have caused the problem?)
bye for now
russ


[/COLOR]

---

### Post by staticvoid on 2007-11-10
it would be "real quick" to just back up your home directory and reinstall a fresh OS...
simpler too :) I had the same update options... I was travelling around and found that in Spain Ubuntu could not get the files, but in Ireland it downloaded the update just fine. so... hmm... if you are really as new as you say you are, it probably would'nt hurt just to take 20 minutes and reinstall ubuntu, right? How much customizations have you made?

sv

---

### Post by Maestro23 on 2007-11-10
> **P&P said:**
> [COLOR="Indigo"]Hello all. I am a very new newbie.  Last week I cut my Linux teeth with 7.04 , apart from hiccups with connecting to the net via router all else seems on the face of to work.  I have now been hitting a brick wall with the update manager and when trying to UPGRADE to 7.10.
The errors I am getting are:
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2]("http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2")
Sub-process bzip2 returned an error code (2) 
I cannot figure out : "....... Check your network connection and the correct writing of the repository address in the preferences...." that accompanies a failed update or upgrade attempt. What and where Is "repository address in the preferences"?
I have scoured the forums, one guy appears to have had  the same problem but I just couldn't grasp what worked for him  it was  beyond my limited comprehension.

Many thx in eager anticipation to resolve this one.
P.S.
Downloaded and burnt a copy 7.10  but  that will not offer just the Upgrade  option.
Did update 4 days ago OS 7.04. without a problem.
Did have a Nvidia driver problem and had to reboot from hand coding to get back to desktop
(could any of this have caused the problem?)
bye for now
russ


[/COLOR]

Can you post your /etc/apt/sources.list

Open a terminal (Apps>> Accessories>> Terminal)

> cat /etc/apt/sources.list

---

### Post by P&amp;P on 2007-11-11
[B]Many thx for replies. Below is what you asked for  Maestro23. Are barking up the right tree?
I think you might be [/B]


russ@desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END


**Look forward to the advice and help many thx russ**

---

### Post by PmDematagoda on 2007-11-11
Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/source.list
```

then comment out the Automatix repos and those with security.ubuntu.com in them by typing # in front of them.

Then do:-

```
sudo apt-get update 
```

and then try the upgrade again.

---

### Post by P&amp;P on 2007-11-11
**THX PmDematagoda **
[COLOR="Black"]How do I move the cursor UP Down & left &right in the terminal window to comment out the offending  lines? I'm stuck at the bottom. I can copy the who thing and edit. When I paste it back into the terminal it comes out with "russ@desktop:~$" on each line.  And the code you gave me to follow after editing does'nt work.  Many thx russ[/COLOR]

---

### Post by Maestro23 on 2007-11-11
> **P&P said:**
> **THX PmDematagoda **
[COLOR="Black"]How do I move the cursor UP Down & left &right in the terminal window to comment out the offending  lines? I'm stuck at the bottom. I can copy the who thing and edit. When I paste it back into the terminal it comes out with "russ@desktop:~$" on each line.  And the code you gave me to follow after editing does'nt work.  Many thx russ[/COLOR]

gedit is not that hard to use.

> gksudo gedit /etc/apt/sources.list

---

