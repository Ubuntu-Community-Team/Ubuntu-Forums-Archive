---
title: "E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by guypilkinton on 2007-08-04
I installed ubuntu today and I am an absolute beginner.  A magarzine article I had suggested installing Beryl I gave it a go and now I get this error when I try to use synaptic.  How can I fix this?


E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am a total beginner with ubuntu and linux so I should not have been playing but I guess that is how you learn.

Thanks for your help

---

### Post by forestpixie on 2007-08-04
post your sources.list

open a terminal - accessories >terminal  enter this

```
gedit /etc/apt/sources.list
```

once text editor has opened post the contents here

---

### Post by guypilkinton on 2007-08-04
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

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

---

### Post by sad_iq on 2007-08-04
Just remove the first line, but first copy that line and paste it in a terminal!!!

---

### Post by forestpixie on 2007-08-04
the first line needs to be deleted
open a terminal again ,do 

```
sudo cp /etc/apt/sources.list sources.list.bak.0408
```

gives you a backup, then 

```
gksudo gedit /etc/apt/sources.list
```

when text editor is open - delete the first line - then save your sources.list and exit
then update your sources

```

sudo apt-get update
```

and all should, I hope, be fine

---

### Post by Majorix on 2007-08-04
I guess a few things can be advised:
- /etc/apt/sources.list is NOT the terminal. So when it tells you to paste things into terminal, use the one under Apps>Accessories>Terminal (if you are using Gnome that is).
- Do NOT use Automatix! I see you have it installed. Its best you avoid it. Even though it offers simple installation, it can break your system. It is not supported by Ubuntu devs and noone here will help you if you say you need help with Automatix.
- Uncomment all the lines starting with deb in your sources.list file. That will get you more software, and newer ones.

Have fun with Ubuntu :)

---

### Post by ThrobbingBrain66 on 2007-08-04
If you still want beryl, enter the following command in a terminal:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
and then follow the instructions found here:
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html)

---

### Post by guypilkinton on 2007-08-04
Thanks for your help the error messages have gone but the desktop effects don't seem to be working like they were before I tried to install Beryl.  I don't get the little squares coming up in the bottom right hand corner any more either.

---

### Post by forestpixie on 2007-08-04
Excellent glad you're nearly ok - can't help with desktop effects - i've never bothered with them. try following throbbingbrain66 link - it might get you there.

---

