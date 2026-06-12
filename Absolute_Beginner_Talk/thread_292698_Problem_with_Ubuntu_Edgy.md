---
title: "Problem with Ubuntu Edgy"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by akyd on 2006-11-04
Hi there,
I'm very sorry if you find my question is very easy, but I'm a beginner with Ubuntu.

my problem is when I'm using the code:

> sudo aptitude update

then:

> sudu aptitude install kubuntu-desktop

in order to install the kde desktop, it told me that the (kubuntu-desktop) pakege is not found.

can anyone help me? please?

---

### Post by PriceChild on 2006-11-04
Could you post the output of```
cat /etc/apt/sources.list
```please? :)

---

### Post by koo-koo on 2006-11-04
If you haven't already, go into System>Administration>Synaptic Package Manager.  Once there, check out the Repositories option.  Assuming you just installed it from the CD, that should be the only option there.  If this is so, click Add and choose 'Ubuntu 6.10', but not Security Updates or Updates.  Next, check all four options (the first two should already be checked).  From there, retry the apt-get commands.

You can also make a few changes directly from sources.list in /etc/apt, though doing it through Synaptic is easier.

---

### Post by akyd on 2006-11-05
I'm very sorry about this dely. the output of the command you gave me is:
```
deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb http://sa.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sa.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://sa.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://sa.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```

---

