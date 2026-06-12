---
title: "synaptic package problem"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by natanel on 2008-03-06
keep geting this problem fro synaptic

E: /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb: trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4

what should i do?

---

### Post by taurus on 2008-03-06
Can you post your /etc/apt/sources.list to be sure you haven't mixed the repos?

```
cat /etc/apt/sources.list
```

---

### Post by boeing777 on 2008-03-06
completely remove  libumfpack4 in synaptics

---

### Post by natanel on 2008-03-06
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main res
tricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by softwa
re-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse un
iverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multi
verse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted univers
e multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted uni                                                                            verse multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multive                                                                            rse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://www.atmel.no/beta_ware/avr32/ubuntu/dapper](http://www.atmel.no/beta_ware/avr32/ubuntu/dapper) binary/
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

---

### Post by taurus on 2008-03-06
Wow!  What happens with those two lines?  How did they get in your /etc/apt/sources.list?

```

deb http://www.atmel.no/beta_ware/avr32/ubuntu/dapper binary/
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

```

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those two lines.  Save the changes and close gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```
Now, see if you can install whatever you planned to install before.

---

### Post by natanel on 2008-03-06
I am using ATMEL32Studio over XP to program some MCU

so I follow it and instal it over Ubuntu
it running with out any problem

i don't think the problem is there, do I really need to remove them?

also when running update i keep getting 
Not all updated can be installed

which? why? how I can solve it?

Edit
also when running check

cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

and then
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7


what happened to my new UBUNTU ??????

---

### Post by PeterJS on 2008-03-06
You should probably comment out the CDROM entries, if you've got an active internet connection they don't add any value, and as illustrated here can some times cause trouble.

The issue with the screenlets repository isn't an error, just a warning, and it's letting you know that you didn't set up the repository key when you set up the screenlets repository so it can not verify the packages are untampered with. It's not strictly necessary, I've never heard of a repository being compromised, but it never hurts to be paranoid, the directions for setting up the key are here:
[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

---

