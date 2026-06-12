---
title: "Synaptic Package Manager Error"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Shyno31 on 2007-11-21
Hi everyone... im really new in this OS,
The first problem was the configuration of the wireless, trying and reading in others forum i was capable to install it.
Now im trying to install the mp3 codec, but when i go to the synaptic package manager, it sends me a error code like this...
> 
E: Type 'wget' is not known on line 75 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

im affraid that i made a damage on the system when i was trying to install the wireless, 
someone in a past forum said me to write 

> cat /etc/apt/sources.list
 
on a terminal,,,, and this is what it shows


> estefano@Delia:~$ cat /etc/apt/sources.list
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

ill appreciate if some one can help me...

---

### Post by Inxsible on 2007-11-21
in a terminal type in ```
gksudo gedit /etc/apt/sources.list
```Then remove the entire part from wget all the way to the bottom except the last line which says " deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" . Save the file and close it.

Back in the terminal, type in ```
sudo apt-get update && sudo apt-get upgrade
```
The wget command and the following part is supposed to be entered in the terminal AFTER you have added the repository to the sources. You do not have to put those commands in the sources.list

---

### Post by Shyno31 on 2007-11-21
thank you it just work!!!
thank you very much...
but... may i know what i have just done?
i want to know for future problems....

---

### Post by Inxsible on 2007-11-21
> **Shyno31 said:**
> thank you it just work!!!
thank you very much...
but... may i know what i have just done?
i want to know for future problems....
Adding the line that starts with "deb" in the sources.list means that you are adding an additional location from where you can get programs/software

wget is a terminal command to download something from a given website. the add-key adds a key so that you know it is authorized software and also the next time you download anything from that same source, they can use that key to authenticate. the last command of update, simply updates your sources.list to include the new source location.

---

### Post by kleo skywalker on 2007-11-21
In Synaptic, search for > ubuntu-restricted-extras package and install it. That gives you many of the codecs needed.

---

### Post by WhiteSlash on 2007-11-24
I get this error from synaptic :S 
E: The package mercury-messenger needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
And I don't know how to fix it...

---

### Post by WhiteSlash on 2007-11-25
I finally fixed it!
I used this command
sudo dpkg --force all -r mercury-messenger
sudo dpkg --force all -r <theconflictingpackage goes here>
Thanks anyway :D

---

