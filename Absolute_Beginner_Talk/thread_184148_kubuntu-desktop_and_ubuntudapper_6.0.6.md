---
title: "kubuntu-desktop and ubuntu/dapper 6.0.6"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-05-29
I would like the option of chosing which desktop i want gnome or kde upon login
i tryied sudo apt-get install kubuntu-desktop  but it won't install cause it needs alot of other packages as well.. even tried thru synaptic but that complains as well about all the packages..Is there a way to get this installed thru command line maybe that would also install all other req packages??
running the release canidate 6.0.6

---

### Post by Daegon on 2006-05-29
Have you tried by switching to root mode?
> sudo -s
(password)
Sometimes this will help, don't know why, it just does. 
You should also try to use the mark all updates function in synaptic before you try again.
For me it was just to open a Terminal and write:
> sudo -s
(password)
apt-get install kubuntu-desktop

---

### Post by user1397 on 2006-05-29
just do
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
that will install all of the dependencies

---

### Post by aysiu on 2006-05-29
If it complains about missing packages, you may have conflicting repositories.

Get a fresh list.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by lime4x4 on 2006-05-29
ok this is the error i'm getting now

Building tag database... Done
The following packages are BROKEN:
  banshee libdbus-glib-1-1 libipoddevice0 libnautilus-burn2
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon dbus
  dcraw debtags flac gtk2-engines-gtk-qt gwenview hal k3b kaffeine
  kaffeine-xine karm katapult kate kaudiocreator kcron kde-guidance
  kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libavahi-core4 libdaemon0 libflac++5c2 libgadu3 libiso9660-4
  libjpeg-progs libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1
  liblockdev1 libnss-mdns libpoppler1-qt libpythonize0 libqt-perl librsync1
  libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1
  libtunepimp2c2a libvcdinfo0 ncompress ocrad openoffice.org-kde poster
  psutils pykdeextensions python-id3lib python-kde3 python2.4-dev
  python2.4-id3lib python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls
  qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch vcdimager
  wlassistant zoo
The following packages will be automatically REMOVED:
  libdbus-1-1
The following packages have been kept back:
  alsa-utils apache2 apache2-common apache2-mpm-prefork apache2-utils
  app-install-data binfmt-support gnome-app-install gnome-power-manager
  gnome-system-tools gsfonts-x11 language-support-en libapr0 libdbus-1-cil
  libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtk2.0-cil libid3tag0 libipod-cil libkpathsea4 libscim8c2a
  libscrollkeeper0 libssl0.9.7 licq licq-plugin-qt
  linux-restricted-modules-2.6.15-23-386 linux-restricted-modules-common
  mono-classlib-1.0 mono-common mono-jit mpd msttcorefonts ntpdate numlockx
  openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-pgsql python-uno python2.4-pgsql scim scim-gtk2-immodule
  scim-modules-socket scrollkeeper shared-mime-info ttf-opensymbol
  ubuntu-artwork ubuntu-base ubuntu-docs ubuntu-minimal ubuntu-standard
  unattended-upgrades x-window-system-core x11-common xbase-clients
  xserver-xorg xserver-xorg-driver-all xserver-xorg-input-all xutils
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon dbus
  dcraw debtags flac gtk2-engines-gtk-qt gwenview hal k3b kaffeine
  kaffeine-xine karm katapult kate kaudiocreator kcron kde-guidance
  kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libavahi-core4 libdaemon0 libflac++5c2 libgadu3
  libiso9660-4 libjpeg-progs libk3b2 libkexif1 libkipi0 libkpimexchange1
  libkscan1 liblockdev1 libnss-mdns libpoppler1-qt libpythonize0 libqt-perl
  librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1
  libtdb1 libtunepimp2c2a libvcdinfo0 ncompress ocrad openoffice.org-kde
  poster psutils pykdeextensions python-id3lib python-kde3 python2.4-dev
  python2.4-id3lib python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls
  qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch vcdimager
  wlassistant zoo
The following packages will be REMOVED:
  libdbus-1-1
0 packages upgraded, 145 newly installed, 1 to remove and 77 not upgraded.
Need to get 113MB of archives. After unpacking 350MB will be used.
The following packages have unmet dependencies:
  libdbus-glib-1-1: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
  banshee: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
  libipoddevice0: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
  libnautilus-burn2: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
avahi-daemon [Not Installed]
dbus [Not Installed]
gwenview [Not Installed]
hal [Not Installed]
kdnssd [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libdbus-1-1 [0.36.2-0ubuntu7 (now)]

Score is 91

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
john@ubuntu:~$

---

### Post by richbarna on 2006-05-29
It looks like a repository problem.
You need to edit your sources.list like this :-
go to 
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")
and copy the whole sources.list
Then open your terminal/konsole and type :-
> sudo gedit /etc/apt/sources.list
Now delete everything and paste the file from psychocats.net
Save and exit.

If all is well :-
> sudo aptitude update && sudo aptitude install kubuntu-desktop

---

### Post by lime4x4 on 2006-05-29
i did here is a copy of it
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by lime4x4 on 2006-05-29
i got it to install.. I had to install dbus first then kubuntu-desktop

---

