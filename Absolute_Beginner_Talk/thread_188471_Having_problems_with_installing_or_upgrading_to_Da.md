---
title: "Having problems with installing or upgrading to Dapper? Here are some fixes"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by ubuntu_demon on 2006-06-03
Are you having problems with installing or upgrading to Dapper? Here are some fixes.
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

---

### Post by ubuntu_demon on 2006-06-04
**WARNING / take a look here prior to upgrading and installing! :**
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

**Here's a clean sources.list for Dapper :**

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

To use this sources.list replace your sources.list with this one using your favorite editor do the following command in the terminal (without the $):
$sudo gedit /etc/apt/sources.list

Then do this command to take the new sources.list into effect do the following command in the terminal (without the $) :

get into ctrl-alt-f1

$sudo apt-get update

It happens quite often that this command wants to remove ubuntu-desktop / kubuntu-desktop so don't worry :

$sudo apt-get dist-upgrade

Make sure everything is installed by :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop (or kubuntu-desktop / edubuntu-desktop / xubuntu-desktop)

Now do a reboot and you should be dist-upgraded from breezy to dapper.
$sudo reboot

---

