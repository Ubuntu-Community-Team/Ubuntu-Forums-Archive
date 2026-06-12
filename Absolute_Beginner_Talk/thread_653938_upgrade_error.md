---
title: "upgrade error"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-30
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing libwxbase2.4-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

trying to upgrade from 7.4 to 7.10

---

### Post by taurus on 2007-12-30
> **frenchsquared said:**
> E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing libwxbase2.4-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_**[COLOR="Blue"]edgy[/COLOR]**_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

trying to upgrade from 7.4 to 7.10

Are you sure you are running Feisty right now, 7.04?  How come it complains about Edgy?

What does your /etc/apt/sources.list look like?

```
cat /etc/apt/sources.list
```

---

### Post by frenchsquared on 2007-12-30
gordon@Asus:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
gordon@Asus:~$

---

### Post by taurus on 2007-12-30
Wow!  You've mixed three releases into one /etc/apt/sources.list.  I recommend you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace both **dapper** and **edgy** words with **feisty**.  Save it and close down the gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```
Wait for it to finish (reboot if it tells you to) and see if you can upgrade to Gutsy now.

---

### Post by frenchsquared on 2007-12-30
its installing
?I mixed?
or it mixed?

anyway thanks
hope I understand this stuff soon

is there somewhere I can go to learn what the comands like sudo gksudo mean

---

### Post by taurus on 2007-12-30
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

