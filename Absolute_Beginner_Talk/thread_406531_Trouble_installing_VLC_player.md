---
title: "Trouble installing VLC player"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by enkidu1016 on 2007-04-11
when i try to install vlc player on edgy using apt-get install vlc i am getting this error message.  I have also tryed going through Synaptic package manager and will get the same error:confused: i installed off of cd kernel 2.6.17-10 and updated to  2.6.17-11.. 

[PHP]The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
[/PHP]
:confused:

---

### Post by o_fortuna on 2007-04-11
Weird! Looks like you might have some funny stuff in your sources list? Maybe you can post it. (/etc/apt/sources.list)

---

### Post by enkidu1016 on 2007-04-11
here is the file

[PHP]deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ubuntu.beryl-project.org edgy main
[/PHP]

---

### Post by nudnik on 2007-04-11
> **enkidu1016 said:**
> when i try to install vlc player on edgy using apt-get install vlc i am getting this error message.  I have also tryed going through Synaptic package manager and will get the same error:confused: i installed off of cd kernel 2.6.17-10 and updated to  2.6.17-11.. 

[PHP]The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
[/PHP]
:confused:

Try:

sudo apt-get update

in the event your repositories need updating after the kernel upgrade, or some other change.

Addtionally, make sure all the repositories are selected using synaptic, with the exception of "proposed updates" and "backports" which might destabilise your system.

---

### Post by o_fortuna on 2007-04-11
I see your problem (I think): Open up software properties (System-Administration-Software Properties (or Software Sources). Make sure that universe has a checkmark next to it, since vlc is in universe. If that didn't make sense, there's always the "other way" ;) : use the Terminal
```
gksudo gedit /etc/apt/sources.list
```

Copy this into that file (deleting everything that was there before):
```
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ubuntu.beryl-project.org edgy main
```

After which do this final bit:
```
sudo apt-get update
sudo apt-get install vlc
```

Hope that helps :)

---

### Post by enkidu1016 on 2007-04-11
Cool i went into the synaptic and found the repository way not checked like you said.. it it now downloading... thanks alot.:guitar:

---

