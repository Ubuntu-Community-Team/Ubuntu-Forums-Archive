---
title: "[SOLVED] umm...guys...I did sumthin wrong...I started copy+pasting all the codes in t"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-20
I tried to install avant.

Btw how do I install it, corectly

also when I open synaptic 

an error occured
E: Type 'echo' is not known on line 88 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by philinux on 2008-03-20
Use the terminal and post the output of

cat  /etc/apt/sources.list

---

### Post by billgoldberg on 2008-03-20
Remove the line in cat /etc/apt/sources.list

Save it and try again.

---

### Post by munch3 on 2008-03-20
bash: cat/etc/apt/sources.list: No such file or directory

---

### Post by Linux_Man on 2008-03-20
Put a space between cat and the file, cat is the program that displays the contents of the file, then it requires the file.

---

### Post by aysiu on 2008-03-20
> **munch3 said:**
> bash: cat/etc/apt/sources.list: No such file or directory
Apparently, you're not copying and pasting (as your subject title would indicate). You are missing a space.

Copy and paste this code: ```
cat /etc/apt/sources.list
```

*cat/etc/apt/sources.list* - you
*cat /etc/apt/sources.list* - philinux

---

### Post by forestpixie on 2008-03-20
theres a space between cat and /etc

---

### Post by forestpixie on 2008-03-20
wow three buses at the same time :)

---

### Post by munch3 on 2008-03-20
jovan@jovan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'



echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'
sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

---

### Post by aysiu on 2008-03-20
It looks as if you copied these lines into the /etc/apt/sources.list file instead of copying them into the terminal: ```
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'



echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'
sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

---

### Post by billgoldberg on 2008-03-20
> **munch3 said:**
> jovan@jovan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'



echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'
sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

Remove everything under #AUTOMATIX REPOS END

Save the file and 

sudo apt-get update

Try[ this]("http://www.kabatology.com/03/11/getting-awn-dock-on-ubuntu-gutsy-gibbon/") how-to, it seems easier.

---

### Post by munch3 on 2008-03-20
so...

---

### Post by munch3 on 2008-03-20
how?
pls consider n00b here

---

### Post by billgoldberg on 2008-03-20
Open up a terminal, past this:

```
sudo gedit /etc/apt/sources.list
```

This will open in a text editor.

---

### Post by munch3 on 2008-03-20
and also...my internet connection seems bit slower:confused:

---

### Post by aysiu on 2008-03-20
> **munch3 said:**
> how?
pls consider n00b here
Close everything you have open now (except whatever web browser you're viewing the forums with).

Press Alt-F2. A Run dialogue box will appear.

In that box, paste the command ```
gksudo nautilus
``` You will be prompted for your user password. Enter it.

Then a file browser will appear that allows you to edit system files. Navigate to /etc/apt and double-click the sources.list file to edit it.

Delete all this stuff at the bottom of the file: ```
#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'



echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'
sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
``` Then press Control-S to save the file. Then close the text editor and the file browser.

---

### Post by forestpixie on 2008-03-20
better to use gksudo with gui apps 

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by aysiu on 2008-03-20
> **billgoldberg said:**
> Open up a terminal, past this:

```
sudo gedit /etc/apt/sources.list
```

This will open in a text editor.
Or ```
gksudo gedit /etc/apt/sources.list
``` Probably makes no difference in this particular case, but it's a good idea to associate *gksudo* with graphical apps and *sudo* with terminal apps.

---

### Post by Jadd on 2008-03-20
Open a terminal, type
sudo gedit /etc/apt/sources.list
(if you're not using Kubuntu or Xubuntu)
follow billgoldberg's instructions.

---

### Post by billgoldberg on 2008-03-20
It seems hard but it really isn't ones you know what everything does.

in /etc/apt/sources.list file are all the servers from where the applications are downloaded from (either apt-get or from synaptic or add/remove)

Since awn isn't in those official lists yet, you have to add a server.

Then the apt-get install xxxxx means: download and install the xxx program.

sudo means you are working as root (this can be dangerous, so don't go messing with system files)

gedit is text editor installed by default in ubuntu.

---

### Post by munch3 on 2008-03-20
Tyvm 2 all!
Problem solved

---

### Post by billgoldberg on 2008-03-20
> **munch3 said:**
> Tyvm 2 all!
Problem solved

If I may ask, what exactly did you do wrong in the first place when you were following the guide?

---

### Post by munch3 on 2008-03-20
and now i succesfully installed AVANT!It rox
ty 2 all again

---

