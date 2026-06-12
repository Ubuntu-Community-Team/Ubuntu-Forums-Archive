---
title: "[SOLVED] apt-get woes

I can't seem to find the solution to this problem, I"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-02-12
Greetings all...

I am new to Ubuntu as of this morning, After a day of working on my Dell Vostro 1500 I have my broadcom BCM4312 wifi card and NVIDIA 8400 video card working and now I *believe* the last piece I need is my sound card. It appears that my solution is most likely:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

However I can not seem to pull the module-assistant with apt-get

Here are the results I am getting:
user@laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Fetched 1B in 1s (1B/s)
Reading package lists... Done

user@laptop:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package module-assistant is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package module-assistant has no installation candidate

Could someone elucidate me please?
Thanks!

---

### Post by jan quark on 2008-02-12
can you please post your sources.list

run this and post the output


```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2008-02-12
Go to System, Administration, Software Sources, and enable the universe repository.

---

### Post by DamonChyld on 2008-02-12
Thanks oldos2er, enabling the universe repository did it. 

My sources.list is as follows... is it usual to have so many '# Line commented out by installer because it failed to verify:' lines?

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

---

### Post by DamonChyld on 2008-02-12
Hmm.. also when I ran sudo m-a a-i alsa I received the output 

module-assistant, error message
     &#9474;                                                                 
     &#9474; Installation of the alsa-source source failed.                     
     &#9474;                                         
     &#9474; Ignoring this package. Maybe you need to add something to         
     &#9474; sources.list, maybe the contrib and non-free archives.

---

### Post by DamonChyld on 2008-02-12
Sorry, full output after passing blue screen was:

Updated infos about 1 packages
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
download 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alsa-source: Depends: debhelper (>= 5.0.37) but it is not installable
               Depends: debconf-utils but it is not installable
E: Broken packages

---

### Post by JoshuaRL on 2008-02-12
Go back into Software Sources and make sure you have everything enabled except the CD and source code.  Then try Update Mangager, and your module-assistant again.

---

### Post by DamonChyld on 2008-02-12
Thanks yall, I have now heard the drum rolls of Ununtu for the first time ;)

---

