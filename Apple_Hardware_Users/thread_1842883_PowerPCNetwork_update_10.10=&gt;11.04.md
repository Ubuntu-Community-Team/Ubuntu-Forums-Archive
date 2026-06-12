---
title: "PowerPC:Network update 10.10=&gt;11.04"
date: 2011-09-12
forum: Apple Hardware Users
---

### Post by ka823 on 2011-09-12
Hi,

using an iBook G4 powerpc, I only run Ubuntu 10.10 LTS. The updater function informs me that 11.04 is available. When chosing to update to 11.04 in the updater, it downloads the required packages, but then stops with the message:

W:Fehlschlag beim Holen von [http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release](http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

Any ideas on how I could manage to perform an update over the network from 10.10 to 11.04?

Thanks in advance!

---

### Post by An Sanct on 2011-09-12
update-manager -d
(maybe sudo .... performs a distribution update)

Also, you can try to download the ISO and burn the CD or make a live USB and upgrade from within that.

PS. Make sure you backup all the critical data!

---

### Post by svtguy88 on 2011-09-13
I'm not sure what the German (I think?) messages mean, but it looks like your system can't find the update packages, for one reason or another.

Maybe try manually adding the 11.04 repositories to your software sources and see what happens?

---

### Post by ka823 on 2011-09-13
The german text
"E:Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt." 
says:
"E: Some index files could not be downloaded, they will be ignored, or old files will be used instead."

---

### Post by linuxopjemac on 2011-09-13
Your /etc/apt/sources.list file is corrupt...

---

### Post by ka823 on 2011-09-13
@linuxopjemac: What would you suggest I do about the corrupt /etc/apt/sources.list file? I´m pretty new to Ubuntu, so not aware of how to fix this. I guess if this file is corrupt, my next update then would stop because of the same error.

---

### Post by linuxopjemac on 2011-09-13
ask someone here to paste a working /etc/apt/sources.list file for 11.04

First try with the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by ka823 on 2011-09-13
I tried the above, but still get the same error.
Where could I get the required file?

---

### Post by linuxopjemac on 2011-09-14
post yours, I can have a look. I have a similar one for Lucid on my own site:
[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)

If you want to amend it for 11.04, you'd have to replace lucid by natty.

---

### Post by ka823 on 2011-09-19
@[linuxopjemac]("http://ubuntuforums.org/member.php?u=468914"):
Thanks for the link. I copied your file, replaced  andlucis by natty and  attached it here. Do I have to rename it sorces.list and just put it in etc/apt/sources.list.d? I have to have root rights to do so, right?
More generally: Can you tell me why I can get Natty using software update? I will have the same problem with the next update, right?

Thanks!

---

### Post by rsavage on 2011-09-19
This is a sources.list for natty:

```
# deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted

# deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates main restricted
# deb http://security.ubuntu.com/ubuntu natty-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ natty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty-backports main restricted universe multiverse

deb http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
```To edit type:

gksudo gedit /etc/apt/sources.list

I recommend installing xubuntu or lubuntu though instead of doing a straight upgrade.

---

### Post by ka823 on 2011-09-20
So the solution was to disable "software from partners" in the software sources.
@rsavage: Thanks for posting the file.
It seems 11.04 keeps my iBook G4 pretty busy. But the upgrade worked.

---

### Post by svtguy88 on 2011-09-20
^^^Give Lubuntu a try if Ubuntu is too heavy for your iBook.  Or Linux Mint-PPC.  Both are much lighter weight than Ubuntu.

---

### Post by ka823 on 2011-09-21
Thanks for the tips. I´ll give them a try.

---

