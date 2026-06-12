---
title: "Automatix install help needed"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by bar10der on 2007-05-05
hello, I am trying to install automatix to check it out

i Am getting this error:
```
W: GPG error: http://www.getautomatix.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

```

And when i tried on the package installer i got this error:
```
Error dependency is not satisfiable: python2.4
```

here is my source.list
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


# deb http://archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

# deb http://archive.ubuntu.com/ubuntu breezy multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# deb http://security.ubuntu.com/ubuntu breezy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
 deb-src http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse #Added by software-properties
 deb http://security.ubuntu.com/ubuntu/ feisty-security universe main multiverse restricted
 deb-src http://security.ubuntu.com/ubuntu/ feisty-security universe main multiverse restricted
 deb http://archive.ubuntu.com/ubuntu/ feisty-updates universe main multiverse restricted
 deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates universe main multiverse restricted
 deb http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted
 deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted
 deb http://archive.ubuntu.com/ubuntu/ feisty-backports universe main multiverse restricted
 deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports universe main multiverse restricted
 deb http://www.getautomatix.com/apt dapper main
heath@heath-laptop:~$ 


```
thanks for you time,
Heath

---

### Post by Steve H on 2007-05-05
There is a similar problem and solution listed [_here_]("http://marc.abramowitz.info/archives/2007/04/01/ubuntu-fixing-no_pubkey-cc919a31e23c5fc3-error-from-automatix-repository/")

Hope that helps.

:)

---

### Post by STREETURCHINE on 2007-05-05
what version you trying to down load ,dapper feisty or breezy, they aint interchangable.
if you have fiesty you need the automatix deb for feisty etc etc .
i could be wrong but i see breezy and feisty in your source list and you have downloaded the dapper deb.

any way if you go to the automatix web site arnieboy will help you fix it.

there is a link in my signature:)

---

