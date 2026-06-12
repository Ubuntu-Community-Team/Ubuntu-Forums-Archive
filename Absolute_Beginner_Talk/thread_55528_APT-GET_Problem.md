---
title: "APT-GET Problem"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by jaqkar on 2005-08-09
Hi

Can someone please help me with this:

I ran: apt-get -t unstable install mpeg4ip-server

The following packages have unmet dependencies:
mpeg4ip-server: Depends: libfaad2-0 (>= 2.1.beta+cvs20041121.12) but 2.0.0-0.5 is to be installed
Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages

--------------

Sources: /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#Other
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

------------
Pin: /etc/apt/preferences

Package: *
Pin: release o=xmixahlx
Pin-Priority: 920

Package: *
Pin: release o=Christian Marillat
Pin-Priority: 910

---

### Post by tonysathre on 2005-08-10
[QUOTE=jaqkar]Hi

Can someone please help me with this:

I ran: apt-get -t unstable install mpeg4ip-server

The following packages have unmet dependencies:
mpeg4ip-server: Depends: libfaad2-0 (>= 2.1.beta+cvs20041121.12) but 2.0.0-0.5 is to be installed
Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages

--------------

Sources: /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#Other
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

------------
Pin: /etc/apt/preferences

Package: *
Pin: release o=xmixahlx
Pin-Priority: 920

Package: *
Pin: release o=Christian Marillat
Pin-Priority: 910[/QUOTE]
 i would say just try to get all those packages that it depends on and run the command again

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=jaqkar]
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
[/QUOTE]

That line often gives me problems. Do you know what repo what you want is in?

---

