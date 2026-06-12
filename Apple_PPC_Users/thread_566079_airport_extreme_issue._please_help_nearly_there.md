---
title: "airport extreme issue. please help nearly there"
date: 2007-10-03
forum: Apple PPC Users
---

### Post by michael.blanche on 2007-10-03
hi all, ive just done a clean install of 7.04 on my macbook g4 with airport extreme, so far it recognises that i have a broadcom card however it is not working at all, and in the network manager i cannot even select to enable to wireless without it disabling itself. i have used a manual setup and all settings are correct for my network,

here is my output:

michael@laptop:~$ sudo aptitude show bcm43xx-fwcutter
Package: bcm43xx-fwcutter
State: partially configured
Automatically installed: no
Version: 1:006-1
Priority: optional
Section: universe/utils
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 123k
Depends: libc6 (>= 2.5-0ubuntu1), debconf (>= 0.5) | debconf-2.0
Recommends: wget | curl
Description: Utility for extracting Broadcom 43xx firmware
 fwcutter is a tool which can extract firmware from various source files. It's
 written for BCM43xx driver files.

 The project page is [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

michael@laptop:~$ sudo apt-get bcm43xx-fwcutter
E: Invalid operation bcm43xx-fwcutter
michael@laptop:~$ sudo aptitude install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  file libfreetype6 libgl1-mesa-glx libmagic1 libpng12-0
  linux-image-powerpc linux-restricted-modules-common
  linux-restricted-modules-powerpc mesa-utils
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater app-install-data apport apport-qt bind9-host
  dbus dnsutils hwdb-client-common hwdb-client-kde iptables kate kcontrol
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a
  kdepasswd kdeprint kdesktop kdm kexi kfind khelpcenter kicker klipper
  kmenuedit koffice-data koffice-libs konqueror konqueror-nsplugins konsole
  ksmserver ksplash ksysguard ksysguardd ktorrent kwin language-pack-en
  libbind9-0 libcurl3 libcurl3-gnutls libdbus-1-3 libdns22 libexif12
  libgl1-mesa-dri libglu1-mesa libisc11 libisccc0 libisccfg1
  libjasper-1.701-1 libjasper-runtime libkonq4 libkrb53 liblwres9
  libmagick9 libpoppler1 libpoppler1-qt libpq5 libpulse0 libqt3-mt
  libsmbclient libssl0.9.8 libvorbis0a libvorbisenc2 libvorbisfile3
  libwrap0 linux-headers-powerpc linux-headers-powerpc64-smp linux-powerpc
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-human openoffice.org-writer openssl poppler-utils
  python python-apport python-launchpad-bugs python-minimal
  python-problem-report python-uno python2.5 python2.5-dev
  python2.5-minimal rsync samba-common smbclient tar tcpdump ttf-opensymbol
  tzdata unattended-upgrades update-manager-core vim-common vim-tiny
0 packages upgraded, 0 newly installed, 0 to remove and 118 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up bcm43xx-fwcutter (006-1) ...
--15:55:32--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:55:33 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--15:55:39--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:55:40 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter



please tell me how to resolve this issue, as it is currently all that is stopping me from running linux full time.

cheers and thanks for your help

michael

---

### Post by pxwpxw on 2007-10-03
There is a problem with that package, see this post, 

[http://ubuntuforums.org/showpost.php?p=3461818&postcount=88](http://ubuntuforums.org/showpost.php?p=3461818&postcount=88)

you can use the bcm43xx compwiz18.1-all.deb package from the link, if the link is down there is a copy of the package attached at the bottom of that post. It is only 30Kb.
It just installs the bcm43xx firmware files in /lib/firmware/.

Edit:
I assume you have a ppc ibook or powerbook, not a macintel macbook? or is there a g4 macbook?

---

