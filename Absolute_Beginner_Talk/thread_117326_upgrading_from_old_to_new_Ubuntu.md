---
title: "upgrading from old to new Ubuntu"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-01-14
Is it possible to upgrade Linux:Ubuntu from an old version to the newest without formatting and installing fresh?
Can you like upgrade from the 2:nd version to the 5:th I guess without leaving the desktop and going through the versions in between?  Or do you have to be in an outside environment like the BOOT CD?

---

### Post by Zelut on 2006-01-14
You can update from one version to another however, in my opinion, it is suggested to just backup your /home and re-install to the latest.  If you'd like to try an upgrade like that you can do it this way (probably want to make sure you're backed up either way)

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by carlosqueso on 2006-01-14
[QUOTE=kuyaedz]You can update from one version to another however, in my opinion, it is suggested to just backup your /home and re-install to the latest.  If you'd like to try an upgrade like that you can do it this way (probably want to make sure you're backed up either way)

sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

Before you apt-get dist-upgrade, you need to make sure all of the lines in your /etc/apt/sources.list look like this (to upgrade to Breezy): ```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
```

---

### Post by jingo811 on 2006-01-15
tnx for the replies and tips guys!
The list thing looked too scary for me :confused: so I'm just gonna burn Breezy to a CD.

How do you guys usually do it, do you "sudo apt-get dist-upgrade" a lot?
Or do you usually burn the new Distro versions on CD and Boot from it?
Is it possible to boot from an external USB harddrive and run the install .iso directly from it, to install the new OS on your stationary harddrives?

---

### Post by Zelut on 2006-01-15
When I have upgraded I simply backed up my /home folder & re-installed from the later CD.  I'd say installing from the latest CD is probably the easiest solution for you..

---

