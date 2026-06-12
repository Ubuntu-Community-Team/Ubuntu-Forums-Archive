---
title: "i screwed up my synaptic"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-02-11
i was being foolish, and accidentally deleted and added random stuf to my synaptic pakage manager's repository's. I was trying to fix one main problem on line 32 sources.list. but i didn't have the permission to edit it. I do not know how to get root on dapper (im using dapper for know). can somebode tel me like, how to reset synaptic to defaults. 

Also, i can't use the updater either, it pops up for half a second then disappears.

---

### Post by taurus on 2007-02-11
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by nickoli_02 on 2007-02-11
Here's the default sources.list file:

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

```
gksudo gedit /etc/apt/sources.list
```

replace your sources.list file with what I included above to restore it to default (with restricted repositories enabled)

---

### Post by Cardmaster91 on 2007-02-11
ok, cool, that worked. Also, how do you update to 6.10? can you do it through snptc pkg mngr?

---

### Post by taurus on 2007-02-11
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by nickoli_02 on 2007-02-11
Your not running 6.10? your forum header lies...

---

### Post by Cardmaster91 on 2007-02-11
yea, i know. i used to run 6/10, but i had to reinstall. I did not feel like downloading the 6.10 image, i had the 6.06 so i used that

---

### Post by shakyone on 2007-10-26
Can someone post the default sources.list files for Gutsy 7.10.  I am in the same boat as cardmaster91.  I got hung up while restoring my sources list with Automatix.

---

### Post by Maestro23 on 2007-10-26
> **shakyone said:**
> Can someone post the default sources.list files for Gutsy 7.10.  I am in the same boat as cardmaster91.  I got hung up while restoring my sources list with Automatix.

Here's mine for 64-bit Gutsy:

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
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

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse



Can also use the following link to generate your own:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by shakyone on 2007-10-26
Maestro23,

     1.  Thanks for the help.  I happen to be running the 32bit version.  If someone else has that, I could use a pointer.  

     2.  Also for anyone else, if I gedit my sources list to match the defaults, do I need to make changes to my software sources window?  I would think I have to, or I would probably confuse "apt"  If so anyone have a suggestion?

Thanks again.

Shaky

---

### Post by jon zendatta on 2007-10-26
i have a similar problem with fiesty. could someone please post the sources.list for fiesty :KS

---

