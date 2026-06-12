---
title: "[SOLVED] Software Update Question"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-01-09
Hi all,

  Having a little problem when I try to run an update. I did not post this on "Installation & Upgrades" cz I'm a noob...  :-? 

  When I run my gnome update manager, it prompts me saying:

> Not all updates can be installed

Run a distribution upgrade, to install as many updates as possible.

This can be caused by an uncompleted upgrade, unofficial software packages or by running a development version

I can choose "Distribution Upgrade" or "Cancel". If I choose "Distribution Upgrade" I get the box:

> Upgrading Ubuntu to version 6.10

But I already have Edgy... 
Then I get the following msg:

> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libdvdcss2

Anyone has any idea??

Thanks,


Vic

---

### Post by vf514 on 2007-01-09
Do you have Beryl installed? I am experiencing the same problem. Here is what aptitude has to say about it:

```
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9746 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
nvidia-glx [1.0.9746+2.6.17.6-2~release.lupine1 (edgy, now) ->
1.0.8776+2.6.17.7-10.1 (edgy-security)]

Score is -40
```

---

### Post by Sef on 2007-01-09
> This may be a transient network problem.

I would wait a day since it may be a network problem and see if it works itself out.  

If not, then post your sources list.

Open the terminal (Applications > Accessories > Terminal):

```
cat /etc/apt/sources.list
```

---

### Post by victorbrca on 2007-01-09
> **vf514 said:**
> Do you have Beryl installed? I am experiencing the same problem. Here is what aptitude has to say about it:

```
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9746 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
nvidia-glx [1.0.9746+2.6.17.6-2~release.lupine1 (edgy, now) ->
1.0.8776+2.6.17.7-10.1 (edgy-security)]

Score is -40
```

I have 915resolution - Compiz - Aiglx


Vic.

---

### Post by victorbrca on 2007-01-09
> **Sef said:**
> I would wait a day since it may be a network problem and see if it works itself out.  

If not, then post your sources list.

Open the terminal (Applications > Accessories > Terminal):

```
cat /etc/apt/sources.list
```

Thanks... will do so!!!

My sources.list

```
victor@victor-laptop:~$ cat /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## Gandalfn for Compiz
deb http://gandalfn.club.fr/ubuntu edgy stable
deb http://gandalfn.club.fr/ubuntu edgy stable dev

## GPG Key Information
# gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ; \
# gpg --export -a 0x483170E9 | sudo apt-key add -

## VLC Player plugin
deb http://medibuntu.sos-sts.com/repo/ edgy free

## Samba
# deb http://www.linux2go.dk/ubuntu edgy main
# deb-src http://www.linux2go.dk/ubuntu edgy main

```

Thanks,


Vic.

---

