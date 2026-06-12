---
title: "Please Read!!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-09
Ok, so I was trying to get Compiz Fusion and like I went to this one site and it said if you've already tried other ways of getting Compiz Fusion then go to synaptic package manage search 'Compiz' and delete everything that showed up so that we could start over fresh. And yeah. That didn't work. So now I don't have Compiz on my computer at all and i can't even go to appearance and select the extra effects button i can only select normal. How do I get Compiz back on my computer and after you tell me that can you also leave me with the information of how to get Compiz Fusion for all the nifty effects??

---

### Post by Teknyk on 2007-12-09
What kind of video card do you have?

---

### Post by bsell on 2007-12-09
Reinstall it from Synaptic. You will have to install Advanced Desktop Effects Settings to get all the bells and whistles.

---

### Post by overdrank on 2007-12-09
> **RadiationHazard said:**
> Ok, so I was trying to get Compiz Fusion and like I went to this one site and it said if you've already tried other ways of getting Compiz Fusion then go to synaptic package manage search 'Compiz' and delete everything that showed up so that we could start over fresh. And yeah. That didn't work. So now I don't have Compiz on my computer at all and i can't even go to appearance and select the extra effects button i can only select normal. How do I get Compiz back on my computer and after you tell me that can you also leave me with the information of how to get Compiz Fusion for all the nifty effects??

Hi and why start a new thread on the same issue
[http://ubuntuforums.org/showthread.php?t=635706](http://ubuntuforums.org/showthread.php?t=635706)

---

### Post by CaptainInsaneO on 2007-12-09
You're running gutsy... it already comes with Compiz Fusion... why are you trying to re-install it?

---

### Post by RadiationHazard on 2007-12-09
because i couldn't get it to run...and idk what my graphics card is? how do you find out on linux ubuntu gusty gibbon 7.10? and i'd reinstall it but the packages don't even show up anymore in synaptic and the couple that still do show up it shows this error when i try to install...

---

### Post by Ub1476 on 2007-12-09
To reinstall Compiz:

```
sudo apt-get install ubuntu-desktop --reinstall
```

To show graphic card:

```
lspci | grep VGA
```

The guide you followed were for Feisty Fawn...

---

### Post by rsambuca on 2007-12-09
I think you have to fix your repositories first.

---

### Post by RadiationHazard on 2007-12-09
here is my card```
jordan@jordan-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
jordan@jordan-laptop:~$
```
and when i put ```
sudo apt-get install ubuntu-desktop --reinstall
```
it says this...```
jordan@jordan-laptop:~$ sudo apt-get install ubuntu-desktop --reinstall
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of ubuntu-desktop is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jordan@jordan-laptop:~$ 
```

---

### Post by rsambuca on 2007-12-09
Post the output of

cat /etc/apt/sources.list

---

### Post by RadiationHazard on 2007-12-09
```
jordan@jordan-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
jordan@jordan-laptop:~$ 

```

---

### Post by thelatinist on 2007-12-09
You need to do

```
gksudo gedit /etc/apt/sources.list
```

And remove the text I've colored red below:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
[COLOR="Red"]
# Line commented out by installer because it failed to verify:[/COLOR]
[COLOR="Red"]#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
[COLOR="Red"]# Line commented out by installer because it failed to verify:[/COLOR]
[COLOR="Red"]#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Red"]# Line commented out by installer because it failed to verify:[/COLOR]
[COLOR="Red"]#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
[COLOR="Red"]# Line commented out by installer because it failed to verify:[/COLOR]
[COLOR="Red"]#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://security.ubuntu.com/ubuntu gutsy-security universe
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
[COLOR="Red"]# Line commented out by installer because it failed to verify:
#[/COLOR]deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

---

### Post by RadiationHazard on 2007-12-09
ok so i deleted all that and this is what it looks like

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

ok so now i save it and do what? =\

---

### Post by rsambuca on 2007-12-09
Look at his instructions again.  You need to remove the indicated number signs as well.

---

### Post by RadiationHazard on 2007-12-09
Ok so before i save it is this right?

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

If so I will save it and then what do I do?

---

### Post by rsambuca on 2007-12-09
I would put a number sign in front of the top line so you don't keep getting prompted to put your CD in.  The save it.  Then run

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by thelatinist on 2007-12-09
Yes, save and then run synaptic and search for and install compiz-fusion following instructions from one of the many tutorials.

Oh, and thanks for catching my oversight rsambuca.  I would definitely commend out that first line, too.

---

### Post by RadiationHazard on 2007-12-09
can you please just copy my code and then do what you were talking about? so i don't have to keep posting the code on here? and then i'll just copy and paste the code you give me in there...

---

### Post by rsambuca on 2007-12-09
You are good, just put a number sign in front of the first line so it looks like this:

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

The rest is OK.

Save, update, and upgrade as per my previous post.

---

### Post by RadiationHazard on 2007-12-09
ok so i did it. now what do i do?? =\

---

### Post by thelatinist on 2007-12-09
Weren't you trying to install compiz-fusion?  Now you should be able to do so using synaptic or the command line.  Follow one of the many tutorials.  If, after install, you still can't figure out how to get it working, please start a new thread with your question and give it a title related to your question.

---

### Post by CaptainInsaneO on 2007-12-09
Once you get compiz fusion installed, you can run it by pressing Alt+F2 and typing

```
compiz --replace
```

You can run the configuration manager by using```
ccsm
```

---

### Post by oldos2er on 2007-12-09
> **RadiationHazard said:**
> ok so i did it. now what do i do?? =\

 Type "sudo aptitude update" in a terminal, then "sudo aptitude install compiz compizconfig-settings-manager" . Or you can do it in Synaptic if you prefer, just do "Reload" first.

 You didn't need to remove the comments from your sources.list, just the #s in front of the deb and deb-src lines.

---

