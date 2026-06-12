---
title: "Synaptic reports outdated Evolution &amp; Firefox"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Ms Dainty on 2006-08-16
Is my Synaptic working? It says the latest version of Evolution is 2.4.1, Firefox is 1.08, and they are both installed. I can't get it to fetch the later versions.

Here's what I had done so far:
1. Changed the repositories to ftp instead of http on the advice of a posting here. This worked to resolve the error message "http://ca.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: Sub-process gzip returned an error code (1)" 

2. Enabled Universe.

3. Hit Reload several times the last few days. Something like 22 packages are always downloaded, but Synaptic will report nothing to install/upgrade. However, today it triggered the Update Manager to install 3 libraries so I think it is working at some level.

Help! Is Synaptic is working properly? And is there some list that I can check in the future to ensure it is functioning?

Thank you.

---

### Post by taurus on 2006-08-16
Are you using Breezy???  I have firefox 1.5.0.5 on Dapper right now...  If in doubt, post your /etc/apt/sources.list!!!

---

### Post by Ms Dainty on 2006-08-16
Yes, I'm using Breezy. I'm waiting for the Dapper CD--I have limits on my downloading bandwidth so I would like to keep using Breezy for the moment.

Here's my sources.list:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [ftp://ca.archive.ubuntu.com/ubuntu](ftp://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [ftp://ca.archive.ubuntu.com/ubuntu](ftp://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ca.archive.ubuntu.com/ubuntu](ftp://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [ftp://ca.archive.ubuntu.com/ubuntu](ftp://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Ms Dainty on 2006-08-17
*bump* Help, Anyone??

---

### Post by taurus on 2006-08-17
Remove the # sign in from of universe & multiverse...  Then

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Ms Dainty on 2006-08-19
Nope. Tried what you suggested and nothing has changed.

In fact, I got so tired of figuring out Synaptic that I installed Automatix, which fetched the latest version of Firefox for me. Synaptic still thinks version 1.08 is installed. I've reloaded several times to no avail. ](*,) 

Anyone have any ideas? Or is Synaptic just a piece of crap?

---

### Post by arnieboy on 2006-08-19
> **Ms Dainty said:**
> Nope. Tried what you suggested and nothing has changed.

In fact, I got so tired of figuring out Synaptic that I installed Automatix, which fetched the latest version of Firefox for me. Synaptic still thinks version 1.08 is installed. I've reloaded several times to no avail. ](*,) 

Anyone have any ideas? Or is Synaptic just a piece of crap?

Firefox on Breezy (in the repositories) is locked at 1.0.x. Automatix installs FF 1.5 in /opt/firefox but not as a deb.

---

### Post by kombipom on 2006-08-19
Each release of Ubuntu sets the version of the applications it will use and they are not updated to the latest version for reasons of stability, ensuring that everything in the distro is compatible.  Any updates are mainly bug fixes but do not include major modifications to the code.  That's why Breezy sticks with version 1.0.x.  Dapper will stick with 1.5.x.  You can of course update it yourself (as you have done) but not from the Breezy repos as they only contain the versions "approved" at the release of Breezy.  This means that your system may not be on the cutting edge but also that you shouldn't get burned by dependancy problems if you stick with your releases repos.

That's my understanding anyway.

---

### Post by Ms Dainty on 2006-08-20
Ah, thank you for the explanation. It would have been nice if this was included in the help files in Ubuntu!

Final question: is there some webpage which lists which version is currently available from the repository? That would enable users to cross-check whether Synaptic is working and provide peace of mind.

Thanks for all your help.

---

