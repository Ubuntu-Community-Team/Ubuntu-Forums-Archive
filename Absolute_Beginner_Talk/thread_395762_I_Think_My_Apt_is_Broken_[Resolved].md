---
title: "I Think My Apt is Broken? [Resolved]"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by sushii. on 2007-03-28
Sorry to bother you, but my apt-get is reeeeally screwed. I think it has something to do with my sources.list. I can barely install anything without getting an error. For example, 'xubuntu-desktop':
```
yoshi@yoshi-pc:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libecore1-desktop: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
                     Depends: libecore1-file but it is not going to be installed  libemotion0: Depends: libecore1 (>= 0.9.9.037) but it is not going to be installed
               Depends: libecore1-con but it is not going to be installed
               Depends: libecore1-config but it is not going to be installed
               Depends: libecore1-dbus but it is not going to be installed
               Depends: libecore1-evas but it is not going to be installed
               Depends: libecore1-fb but it is not going to be installed
               Depends: libecore1-file but it is not going to be installed
               Depends: libecore1-ipc but it is not going to be installed
               Depends: libecore1-job but it is not going to be installed
               Depends: libecore1-txt but it is not going to be installed
               Depends: libecore1-x but it is not going to be installed
               Depends: libevas1 (>= 0.9.9.037) but it is not going to be installed
  xubuntu-desktop: Depends: abiword-plugins but it is not going to be installed
                   Depends: foomatic-db-hpijs but it is not going to be installed
                   Depends: gaim but it is not going to be installed
                   Depends: gnumeric-gtk but it is not going to be installed
                   Depends: gqview but it is not going to be installed
                   Depends: gtk2-engines-xfce but it is not going to be installed
                   Depends: hplip but it is not going to be installed
                   Depends: libgoffice-gtk-1-2 but it is not going to be installed
                   Depends: orage but it is not going to be installed
                   Depends: scim-anthy but it is not going to be installed
                   Depends: scim-chewing but it is not going to be installed
                   Depends: scim-hangul but it is not going to be installed
                   Depends: scim-pinyin but it is not going to be installed
                   Depends: thunar but it is not going to be installed
                   Depends: thunar-media-tags-plugin but it is not going to be installed
                   Depends: xarchiver but it is not going to be installed
                   Depends: xfburn but it is not going to be installed
                   Depends: xfce4-appfinder but it is not going to be installed
                   Depends: xfce4-battery-plugin but it is not going to be installed
                   Depends: xfce4-clipman-plugin but it is not going to be installed
                   Depends: xfce4-cpugraph-plugin but it is not going to be installed
                   Depends: xfce4-fsguard-plugin but it is not going to be installed
                   Depends: xfce4-mailwatch-plugin but it is not going to be installed
                   Depends: xfce4-mixer-alsa but it is not going to be installed                   Depends: xfce4-mount-plugin but it is not going to be installed
                   Depends: xfce4-netload-plugin but it is not going to be installed
                   Depends: xfce4-panel but it is not going to be installed
                   Depends: xfce4-quicklauncher-plugin but it is not going to be installed
                   Depends: xfce4-screenshooter-plugin but it is not going to be installed
                   Depends: xfce4-session but it is not going to be installed
                   Depends: xfce4-systemload-plugin but it is not going to be installed
                   Depends: xfce4-taskmanager but it is not going to be installed
                   Depends: xfce4-utils but it is not going to be installed
                   Depends: xfce4-verve-plugin but it is not going to be installed
                   Depends: xfce4-weather-plugin but it is not going to be installed
                   Depends: xfce4-xkb-plugin but it is not going to be installed                   Depends: xfdesktop4 but it is not going to be installed
                   Depends: xfmedia but it is not going to be installed
                   Depends: xubuntu-artwork-usplash but it is not going to be installed
                   Depends: xubuntu-docs but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
WDF? It always has to do with dependencies. Rawr! I'm gettin' pizzled! :( 
Here's my /etc/apt/sources.list:

```

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/

# deb http://ubuntu.beryl-project.org dapper main
deb http://download.tuxfamily.org/3v1deb dapper beryl-svn

## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu dapper e17
deb-src http://edevelop.org/pkg-e/ubuntu dapper e17

deb http://www.getautomatix.com/apt dapper main

```

... and my apt gets pwned!!!1111111111 OMGWTFBBQ

---

### Post by DSn0wMan on 2007-03-28
Here is a good resource for fixing your sources.list

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by sushii. on 2007-03-28
Followed the tutorial and still got the error. Thanks though! Anyone else?

---

### Post by sushii. on 2007-03-28
Oooh nvm it works with aptitude now. Thanks!

---

### Post by DSn0wMan on 2007-03-28
Yes, aptitude for some reason or another is better at resolving dependencies.

---

