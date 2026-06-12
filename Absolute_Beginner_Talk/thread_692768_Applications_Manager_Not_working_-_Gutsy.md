---
title: "Applications Manager Not working - Gutsy"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by onlyonesock on 2008-02-10
If I try to download any software, a message window tells me 'The List of applications is not available' - click 'Reload' you need a working internet connection.

. I do this, I enter my password, I get a brief window that moves to quickly for me to read, then everything repeats. Any patient, kindly advice is very welcome. I have just received my computer back from having the motherboard replaced. Thanks

---

### Post by Bubba64 on 2008-02-10
You could open up the terminal and run  sudo apt-get update let see if it accesses the repositories and look to see if your missing anything then run  sudo apt-get install. I probably wouldn't do anything until I talked to whoever changed the mother board if it is possible. Or better advice from somebody more knowledgeable.

---

### Post by Paqman on 2008-02-10
Do you have internet in general? Or is it just reloading the repos that isn't working?

---

### Post by onlyonesock on 2008-02-10
Thanks Bubba
Yes, have tried; it doesn't register my password.

---

### Post by onlyonesock on 2008-02-10
Thanks Bubba
Yes, have tried; it doesn't register my password.

---

### Post by onlyonesock on 2008-02-10
Hi Paqman
Yes, have internet

---

### Post by erfahren on 2008-02-10
> **onlyonesock said:**
> Thanks Bubba
Yes, have tried; it doesn't register my password.when you type your password into the terminal the cursor won't move

what exactly happens when you typr in:
```

sudo apt-get update

```
did you also recently reinstall Gutsy (are you using Gutsy?)

---

### Post by onlyonesock on 2008-02-10
Hi Erfahren

Have just tried again - and I got this after two attempts:

*****@******l-desktop:~$ sudo apt-get update
[sudo] password for ******:
Sorry, try again.
[sudo] password for ******l:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Reading package lists... Done
******@******-desktop:~$

---

### Post by erfahren on 2008-02-10
ok - enter the following into the terminal and post the output of it here (between "code" tags if you could):
```

cat /etc/apt/sources.list

```

---

### Post by jan quark on 2008-02-10
erfahren is right

probably your sources are commented out you can also check, if the sources are enabled by going to system > administration > software sources

---

### Post by onlyonesock on 2008-02-10
Erfahren

Regret, I don't know what code tags are, but I got the following:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
*****@*****-desktop:~$

---

### Post by erfahren on 2008-02-10
ok - let me clean it up for you - I'll post back in a few minutes

---

### Post by onlyonesock on 2008-02-10
Thanks Jan Quark
Does that mean I should tick the boxes in the Ubuntu section of the software sources? If so, while i'm at it, would that apply to all the tabs? Currently, no boxes are ticked at all

---

### Post by PmDematagoda on 2008-02-10
If you find it hard to do it manually, then you can do it using Software Sources in System>Administration>Software Sources, enabling all the choices and disabling the one for the CD-ROM in the Ubuntu Software tab,  selecting the appropriate choices in the Updates tab and reloading the sources list when you close Software Sources.

---

### Post by onlyonesock on 2008-02-10
Thanks Erfahren,

I'll go with that but I might need idiot-proof instructions on what to do

---

### Post by onlyonesock on 2008-02-10
Thanks PmDematagoda,

Beginning to get it. Will wait for Erfahren's way - it will be a useful learning experience

---

### Post by PmDematagoda on 2008-02-10
> **onlyonesock said:**
> Will wait for Erfahren's way - it will be a useful learning experience
But of course:), I would recommended it to people who want to really understand the Linux OS since commands are one of the most fail-safe ways of getting things done on the system(If you get them right;)).

---

### Post by erfahren on 2008-02-10
ok - I'll explain basically what each step does above each command so you know what's happening

first back up your current sources.list (always a good idea before editing system files)
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_back

```
open your current sources.list in the text editor (Gedit) with root permissions
```

gksudo gedit /etc/apt/sources.list

```
now - press Ctrl+A to highlight *all* the contents and copy and paste what is below into the file (overwriting all the contents)
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
#deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## MEDIBUNTU REPOSITORY
deb http://packages.medibuntu.org/ gutsy free non-free

```
now - save the file and close it

I added the Medibuntu repository in there - it contains some proprietary packages that aren't available in the Ubuntu ones (you'd probably want it eventually) - you need to add the key for it - so in the terminal enter the following:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
now update the available repositories on your computer
```

sudo apt-get update

```
if you don't get any errors - get the software updates (upgrades)
```

sudo apt-get upgrade

```
there should be a bunch of them!

---

### Post by onlyonesock on 2008-02-10
Up and running now. Sincere thanks to all =D>

---

### Post by Amander on 2008-02-10
> **jan quark said:**
> 

probably your sources are commented out you can also check, if the sources are enabled by going to system > administration > software sources

Jan Quark, I followed this suggestion and it worked PERFECTLY. I was able to access the repositories and then make the updates to get the package manager up and running. **Thank you.**

I knew this was the perfect place to come searching for help when things went wonky.

---

