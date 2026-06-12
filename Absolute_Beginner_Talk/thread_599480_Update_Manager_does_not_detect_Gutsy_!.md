---
title: "Update Manager does not detect Gutsy !"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by rochak on 2007-11-01
Hi,

I am using feistry fawn, my update manger once detected upgrade to Gutsy, I started downloading it but for some reason the update was unsucessful. 

Now, the update manager no longer detects update to Gutsy and I am still running Feisty Fawn :(( Is there any way to update without burning and downloading the whole gutsy on a CD. This is because I have modified a lot of themes in Feisty and I don't want a total fresh installation of gutsy.  Thanks!

---

### Post by taurus on 2007-11-01
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by rochak on 2007-11-01
hi taurus,

as I said, my update manager no longer detects a new update to a distribution :(( How do I upgrade now?

thanks

---

### Post by g2g591 on 2007-11-01
your sources.list has already been changed to gutsy (from the failed upgrade). all you need to do is run sudo apt-get upgrade a few times and you will be all set

---

### Post by rochak on 2007-11-03
Hi,

I din really get what you meant by running apt-get upgrade a few times? Don't I need to change any thing in my sources.list file. I have copied it below for your reference, further help will be great !!!

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by rochak on 2007-11-04
hi. .I got it working :))) 

Just ran sudo apt-get upgrade a few times and then clicked Alt+F2 and typed gksudo "update-manager -c" and it detected the upgrade for me :) 

thanks everyone

---

