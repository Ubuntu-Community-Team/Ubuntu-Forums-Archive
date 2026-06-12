---
title: "how to swich over to kde"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by rav on 2006-08-07
i have ordered the cd from ship it and installed the default version 5.10.how can i switch to kde. Please guide me.

---

### Post by jimbren on 2006-08-07
from a terminal window, do this:
```
sudo apt-get update
sudo aptitude install kubuntu-desktop
```

---

### Post by Klaidas on 2006-08-07
Here's a nice helpful tutorial: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by rav on 2006-08-07
i get this error please help me!

kde:
 Depends: kde-core  but it is not installable
 Depends: kde-amusements but it is not going to be installed
 Depends: kdeaddons  but it is not installable
 Depends: kdeadmin but it is not going to be installed
 Depends: kdeartwork  but it is not installable
 Depends: kdegraphics but it is not going to be installed
 Depends: kdemultimedia but it is not going to be installed
 Depends: kdenetwork but it is not going to be installed
 Depends: kdepim but it is not going to be installed
 Depends: kdeutils but it is not going to be installed
 Depends: kdewebdev  but it is not installable
 Depends: kdesdk but it is not going to be installed
 Depends: kdeaccessibility but it is not going to be installed
 Depends: kdevelop3 but it is not going to be installed


my sources.list is


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by user1397 on 2006-08-07
try my guide: [SIZE=2][install kde, gnome, or xfce]("http://ubuntuforums.org/showthread.php?t=205002")[/SIZE]

---

### Post by rav on 2006-08-07
I am getting a error even after going through the guide 



Reading package lists... 0
%


Reading package lists... 10
0%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... Done


Reading extended state information... 0
%
Reading extended state information... 95
%

Reading extended state information       


Initializing package states... 0%
 


Initializing package states... Done

Couldn't find any package whose name or description matched "kubuntu-desktop"
The following packages have been kept back:
  base-config binutils binutils-static bogofilter bogofilter-bdb 
  bogofilter-common cpio eog evms evms-ncurses fetchmail firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnupg gthumb 
  gtk2-engines-pixbuf info irssi-text libcairo2 libcurl3 libevms-2.5 
  libfreetype6 libgd2-noxpm libgda2-3 libgda2-common libgimp2.0 libgnutls11 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libkpathsea3 libmagick6 
  libmysqlclient12 libmysqlclient14 libnspr4 libnss3 libperl5.8 
  libpoppler0c2 libpoppler0c2-glib libpq4 librpm4 libsasl2 libsasl2-modules 
  libsmbclient libssl0.9.7 libtasn1-2 libtiff4 libtotem-plparser0 linux-386 
  linux-image-386 linux-restricted-modules-386 
  linux-restricted-modules-common login mysql-common openoffice.org2 
  openoffice.org2-base openoffice.org2-calc openoffice.org2-common 
  openoffice.org2-core openoffice.org2-draw openoffice.org2-evolution 
  openoffice.org2-gnome openoffice.org2-impress openoffice.org2-java-common 
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer 
  openssh-client passwd perl perl-base perl-modules pmount ppp python-pgsql 
  python-uno python2.4-pgsql rhythmbox rpm samba-common serpentine 
  smbclient ssh-askpass-gnome sudo tar totem totem-gstreamer ttf-opensymbol 
  unzip wget x-window-system-core xbase-clients xchat xchat-common 
  xorg-common xserver-common xserver-xorg xserver-xorg-core 
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati 
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus 
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy 
  xserver-xorg-driver-fbdev xserver-xorg-driver-glide 
  xserver-xorg-driver-glint xserver-xorg-driver-i128 
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 
  xserver-xorg-driver-imstt xserver-xorg-driver-mga 
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport 
  xserver-xorg-driver-nsc xserver-xorg-driver-nv 
  xserver-xorg-driver-rendition xserver-xorg-driver-s3 
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage 
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis 
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga 
  xserver-xorg-driver-trident xserver-xorg-driver-tseng 
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga 
  xserver-xorg-driver-via xserver-xorg-driver-vmware 
  xserver-xorg-input-acecad xserver-xorg-input-aiptek 
  xserver-xorg-input-calcomp xserver-xorg-input-citron 
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc 
  xserver-xorg-input-dynapro xserver-xorg-input-elographics 
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen 
  xserver-xorg-input-kbd xserver-xorg-input-magellan 
  xserver-xorg-input-microtouch xserver-xorg-input-mouse 
  xserver-xorg-input-mutouch xserver-xorg-input-palmax 
  xserver-xorg-input-penmount xserver-xorg-input-spaceorb 
  xserver-xorg-input-summa xserver-xorg-input-tek4957 
  xserver-xorg-input-void xserver-xorg-input-wacom xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 159 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Writing extended state information... 0%
Writing extended state information... Done

Reading package lists... 0%              
 
Reading package lists... 100%

Reading package lists... Done

Building dependency tree... 0%

Building dependency tree... Done

Reading extended state information... 0%

Reading extended state information       

Initializing package states... 0% 

Initializing package states... Done

---

