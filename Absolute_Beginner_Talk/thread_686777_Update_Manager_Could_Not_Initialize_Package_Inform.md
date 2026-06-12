---
title: "Update Manager Could Not Initialize Package Information"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Kunks on 2008-02-03
I'm getting an error message when I try to install updates through the update manager
see attached screen shot....How do I correct this???

---

### Post by taurus on 2008-02-03
Did you modify or add something to /etc/apt/sources.list because there is something wrong with line 56 in there.  So, either edit it and remove it or post it here.

```
cat /etc/apt/sources.list
```

---

### Post by jan quark on 2008-02-03
please copy and paste the content of your sources.list
run in terminal

```

sudo gedit /etc/apt/sources.list
```

---

### Post by Kunks on 2008-02-03
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
 sudo tee -a /etc/apt/sources.list
wget [http://download.tuxfamily.org/syzygy42/reacocard.ascsudo](http://download.tuxfamily.org/syzygy42/reacocard.ascsudo) apt-key add reacocard.ascrm reacocard.ascsudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

echo 'deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator' 
sudo tee -a /etc/apt/sources.list
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

---

### Post by taurus on 2008-02-03
You need to edit /etc/apt/sources.list

```
**[COLOR="Blue"]gksudo[/COLOR]** gedit /etc/apt/sources.list
```
and remove all these lines at the bottom.

```

sudo tee -a /etc/apt/sources.list
wget http://download.tuxfamily.org/syzygy...cocard.ascsudo apt-key add reacocard.ascrm reacocard.ascsudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

echo 'deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator'
sudo tee -a /etc/apt/sources.list
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

```
Save it.  Then, run (make sure you have the update window close first)

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Kunks on 2008-02-03
That fixed it-you guys are great!
Thanks

---

