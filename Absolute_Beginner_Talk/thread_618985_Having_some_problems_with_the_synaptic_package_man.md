---
title: "Having some problems with the synaptic package manager"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Shyno31 on 2007-11-21
Hi everyone... im really new in this OS, 
The first problem was the configuration of the wireless, trying and reading in others forum i was capable to install it.
Now im trying to install the mp3 codec, but when i go to the synaptic package manager, it sends me a error code like this...

E: Type 'wget' is not known on line 75 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

im affraid that i made a damage on the system when i was trying to install the wireless, ill appreciate if some one can help me...

---

### Post by Paul820 on 2007-11-21
Can you post the contents of your sources.list? In the terminal copy and paste or type this
> cat /etc/apt/sources.list
And copy and paste it here on the forums.

---

### Post by Shyno31 on 2007-11-21
ok. done, ist quite long but here it goes...

estefano@Delia:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
gpg --export --armor E23C5FC3
sudo apt-key add -
sudo apt-get update
exit

cd
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

---

### Post by mrglimm on 2008-01-17
I think you may have tried to install another apt manager incorrectly.  You'll need to remove the last lines of this file.
Go to terminal and:

#  gksu gedit /etc/apt/sources.list

remove this from the end of your list:

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
gpg --export --armor E23C5FC3
sudo apt-key add -
sudo apt-get update

make sure to leave the "exit" entry at the end then save file

hope this helps


Also I didn't see this at the end of your list file...

cd
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

remove this too as the "exit" should be the last line

---

### Post by erginemr on 2008-01-17
Hello,

For a one-to-one comparison, my "/etc/apt/sources.list" file is as follows:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

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
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://tr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
```

As you see, all your repositories have been commented out with "#". This is a common behavior of synaptic, where there is no active network/internet during the installation.

So, you should start first by removing the following lines:
```
wget http://www.getautomatix.com/keys/automatix2.key
gpg --export --armor E23C5FC3
sudo apt-key add -
sudo apt-get update
exit

cd
deb http://www.getautomatix.com/apt gutsy main
```
from your sources.list file. You may edit it with:
```
gksudo gedit /etc/apt/sources.list
```

Then, save and close it, open Synaptic from Main Menu->System-> Administration and make sure that the relevant sections in Synaptic are like the ones shown in the attached images.

---

