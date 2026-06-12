---
title: "repositories problems again"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by Redneo on 2008-11-03
I have upgraded to 8.10 but I try switching the archives over to ports i had fix the problem but it's back again and I find the fix so I could use some help

---

### Post by stream303 on 2008-11-09
Apply your fix again - but if I'm correct, be sure to uncheck anything you find in the first tab of software sources, and from now on, use the "third party" tab - which is where your fixes to the repos will show up.

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

This only applies to upgrades that can't seem to find the repos after you have fixed them by pointing them to ports.  With Hardy and Intrepid, they were taken care of, although it pays to look in the third-party tab too just in case.

At least that's what happened to me awhile back.

---

### Post by Redneo on 2008-11-14
I applied the fix again and I get the failed to fetch the ports.ubuntu.com/dist/ hardy-security/release and some other stuff it failed to get

---

### Post by stream303 on 2008-11-15
Ok, can you post the output of sources.list file?

```
cat  /etc/apt/sources.list
```

---

### Post by Redneo on 2008-11-15
This is what the sources.list  looks like

# deb cdrom: [Ubuntu 8.04.1_Hardy Heron_- Release powerpc (20080703.1)]/ Hardy main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) intrepid-backports main restricted universe multiverse
#deb-src [http://ports.ubuntu.com/ubuntu](http://ports.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-security main restricted universe
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-security restricted main multiverse universe

I thought i had fixed it and I upgraded to intrepid still get the problem

---

### Post by stream303 on 2008-11-15
Aha, I think you are missing the trailing slash!

> 
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-security main restricted universe
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) intrepid-security restricted main multiverse universe

For each url, make sure that they have a trailing slash ie:

> deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)  intrepid main restricted universe multiverse

AND, make sure there is at least one space after that trailing slash!  That can trip you up also.

When you've added that trailing slash and verified that there is a space afterwards, be sure to update the system.  Simple to do in a terminal:

```
sudo apt-get update
```

or I suppose you could just use the gui and go into software sources and update from there, although anytime I manually edit the sources.list file, I just use the commandline to update.

With my old Hardy upgrade, once that was done, I had to make sure that nothing was checked in the main tab, and only used the "third party" tab.  With a recent install of Hardy and Intrepid, that seems to be fixed, although there are still references to the ports in the third-party tab.

Let's see how this goes....

---

### Post by Redneo on 2008-11-16
I think it's fix I applied the changes now for the wifi thanks for your help

---

### Post by Redneo on 2008-11-18
I've used it a few days now and no errors thank for the help Stream303

---

