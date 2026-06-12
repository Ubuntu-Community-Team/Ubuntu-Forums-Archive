---
title: "Problems upgrading to Feisty"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2007-04-08
Hmmmm...I'm at a bit of a loss as to what's gone wrong as I wasn't paying a great deal of attention at the time time of updating.

Basically, I was running Edgy and the option popped up to upgrade to Feisty. I decided, why not and things kind of half upgraded, and half not. Anyway, when running apt-get upgrade I get the message back...............

Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                                 [ OK ]
 * Starting ACPI services...                                                      invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


ANy idea on how I can fix this?

---

### Post by Hieronymus on 2007-04-08
You could adept your /etc/apt/sources.list to feisty and do an apt-get update apt-get dist-upgrade like this:

```

cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list

```

remove all lines from the old /etc/apt/sources.list and add the following lines:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#deb http://beryl.xglusers.de/ubuntu.beryl-project.org edgy main
#deb http://ubuntu.beryl-project.org/ feisty main

```

then update and upgrade

```

sudo apt-get update && sudo apt-get dist-upgrade

```

see if this fixes the problems. 

Jeroen

---

### Post by SpongeBob SquarePants on 2007-04-08
Hmmmm....no....I still get......

errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

