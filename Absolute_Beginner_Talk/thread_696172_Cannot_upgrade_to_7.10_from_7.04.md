---
title: "Cannot upgrade to 7.10 from 7.04"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by porlaizquierda on 2008-02-13
I can't upgrade from Ubuntu 7.04 to 7.10. When I try it begins to upgrade, but after a couple of minutes I get this message.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I don't know why it displays that message twice, but it does. Can anyone help me?

---

### Post by taurus on 2008-02-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by porlaizquierda on 2008-02-14
Here is what it said after I typed in the command in the terminal.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx


So what exactly does that mean? Can I upgrade? Is it even good for me to upgrade?

---

### Post by taurus on 2008-02-14
Maybe you want to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the last two lines to comment them out.

```

#deb http://ftp.debian.org sarge main
#deb http://mirror3.ubuntulinux.nl/ dapper-seveas freenx

```
Save it and run

```
sudo apt-get update
```
Now, see if you can upgrade from Feisty to Gutsy.

---

