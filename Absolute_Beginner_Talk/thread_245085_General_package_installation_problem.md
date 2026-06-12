---
title: "General package installation problem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by p0pnfresh on 2006-08-27
Hi,

After installing UBUNTU I upgraded UBUNTU and apt-get install Kde. I logged out and logged in using kde and eveything worked fine. However, now, evey time I want to install a package, using apt or synaptic, the installer finds it necesarry to remove 527 packages, most of which are critical, to continue. 

Also, in synaptic, a lot of packages appear as marked for removal and there is no way to unmark them. 

Why does my system wants to break itself? :oops:

---

### Post by Bachstelze on 2006-08-27
To install KDE, you should have run

```
sudo aptitude install kubuntu-desktop
```

try running it now. Also, there's a special repo to get KDE's latest version, see [here](http://kubuntu.org/announcements/kde-354.php).

---

### Post by p0pnfresh on 2006-08-27
It seems like a mess

#aptitude install kubuntu-desktop

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: acpi-support but it is not installable
                   Depends: adept but it is not installable
                   Depends: akode but it is not installable
                   Depends: akregator but it is not installable
                   Depends: amarok but it is not installable
                   Depends: ark but it is not installable
                   Depends: arts but it is not installable
                   Depends: bluez-cups but it is not installable
                   Depends: cupsys but it is not installable
                   Depends: cupsys-driver-gimpprint but it is not installable
                   Depends: dvd+rw-tools but it is not installable
                   Depends: foomatic-db-gimp-print but it is not installable
                   Depends: foomatic-db-hpijs but it is not installable
                   Depends: gs-esp but it is not installable
                   Depends: gstreamer0.8-misc but it is not installable
                   Depends: gstreamer0.8-vorbis but it is not installable
                   Depends: gtk2-engines-gtk-qt but it is not installable
                   Depends: gwenview but it is not installable
                   Depends: hplip-base but it is not installable
                   Depends: k3b but it is not installable
                   Depends: kaddressbook but it is not installable
                   Depends: kaffeine-gstreamer but it is not installable
                   Depends: kamera but it is not installable
                   Depends: karm but it is not installable
                   Depends: katapult but it is not installable
                   Depends: kate but it is not installable
                   Depends: kaudiocreator but it is not installable
                   Depends: kcontrol but it is not installable
                   Depends: kcron but it is not installable
                   Depends: kde-guidance but it is not installable
                   Depends: kde-systemsettings but it is not installable
                   Depends: kdeadmin-kfile-plugins but it is not installable
                   Depends: kdebase-kio-plugins but it is not installable
                   Depends: kdebluetooth but it is not installable
                   Depends: kdegraphics-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kappfinder-data but it is not installable
                   Depends: kdemultimedia-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kio-plugins but it is not installable
                   Depends: kdenetwork-filesharing but it is not installable
                   Depends: kdenetwork-kfile-plugins but it is not installable
                   Depends: kdepasswd but it is not installable
                   Depends: kdepim-kio-plugins but it is not installable
                   Depends: kdepim-wizards but it is not installable
                   Depends: kdeprint but it is not installable
                   Depends: kdesktop but it is not installable
                   Depends: kdm but it is not installable
                   Depends: kfind but it is not installable
                   Depends: kghostview but it is not installable
                   Depends: khelpcenter but it is not installable
                   Depends: kicker but it is not installable
                   Depends: kio-apt but it is not installable
                   Depends: kio-locate but it is not installable
                   Depends: klaptopdaemon but it is not installable
                   Depends: klipper but it is not installable
                   Depends: kmail but it is not installable
                   Depends: kmenuedit but it is not installable
                   Depends: kmilo but it is not installable
                   Depends: kmix but it is not installable
                   Depends: knetworkconf but it is not installable
                   Depends: knotes but it is not installable
                   Depends: konq-plugins but it is not installable
                   Depends: konqueror but it is not installable
                   Depends: konqueror-nsplugins but it is not installable
                   Depends: konserve but it is not installable
                   Depends: konsole but it is not installable
                   Depends: kontact but it is not installable
                   Depends: konversation but it is not installable
                   Depends: kooka but it is not installable
                   Depends: kopete but it is not installable
                   Depends: korganizer but it is not installable
                   Depends: kpdf but it is not installable
                   Depends: kpf but it is not installable
                   Depends: kppp but it is not installable
                   Depends: krdc but it is not installable
                   Depends: krfb but it is not installable
                   Depends: krita but it is not installable
                   Depends: kscd but it is not installable
                   Depends: kscreensaver but it is not installable
                   Depends: ksmserver but it is not installable
                   Depends: ksnapshot but it is not installable
                   Depends: ksplash but it is not installable
                   Depends: ksvg but it is not installable
                   Depends: ksysguard but it is not installable
                   Depends: ksystemlog but it is not installable
                   Depends: kubuntu-default-settings but it is not installable
                   Depends: kubuntu-docs but it is not installable
                   Depends: kubuntu-konqueror-shortcuts but it is not installable
                   Depends: kuser but it is not installable
                   Depends: kwalletmanager but it is not installable
                   Depends: kwifimanager but it is not installable
                   Depends: kwin but it is not installable
                   Depends: lftp but it is not installable
                   Depends: libgl1-mesa but it is not installable
                   Depends: libglut3 but it is not installable
                   Depends: openoffice.org2 but it is not installable
                   Depends: openoffice.org2-kde but it is not installable
                   Depends: pnm2ppa but it is not installable
                   Depends: powermanagement-interface but it is not installable
                   Depends: python-apt but it is not installable
                   Depends: python-id3lib but it is not installable
                   Depends: python-musicbrainz but it is not installable
                   Depends: python-opengl but it is not installable
                   Depends: qca-tls but it is not installable
                   Depends: speedcrunch but it is not installable
                   Depends: wvdial but it is not installable
                   Depends: x-window-system-core but it is not installable
                   Depends: xorg-driver-synaptics but it is not installa

---

### Post by Bachstelze on 2006-08-27
Could you please paste your /etc/apt/ources.list file ?

---

### Post by p0pnfresh on 2006-08-27
Hey thnx for the quick replies!

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by Bachstelze on 2006-08-27
Okay, at the end of the file, add :

```
deb http://kubuntu.org/packages/kde-354 dapper main
```

then run :
```

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by p0pnfresh on 2006-08-27
It doesn't work. It gives a similar errir. It says at the end "apt-get -f install" and if I do it returns the list 512 packaged to be removes with a warning that I'm about to break my UBUNTU. hehe, thnx for the help anyway!

#apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: gtk2-engines-gtk-qt but it is not going to be installed
                   Depends: gwenview but it is not going to be installed
                   Depends: ivman but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: katapult but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdebluetooth but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: knetworkconf but it is not going to be installed
                   Depends: konserve but it is not going to be installed
                   Depends: konversation but it is not going to be installed
                   Depends: krita but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kubuntu-artwork-usplash but it is not going to be in stalled
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
                   Depends: python-opengl
                   Depends: qca-tls but it is not going to be installed
                   Depends: speedcrunch but it is not going to be installed
                   Depends: ttf-dejavu but it is not going to be installed
                   Depends: vorbis-tools but it is not going to be installed
  libarts1-dev: Depends: libartsc0-dev (= 1.4.3-0ubuntu1) but 1.5.4-1 is to be installed
  libasound2-dev: Depends: libasound2 (= 1.0.9-2) but 1.0.11-7 is to be installed
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6.ds1-4 is to beinstalled
  libc6-i686: PreDepends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6.ds1-4 is to  be installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-5) but it is not installable
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.3-3) but 2.8.3-0ubuntu1 is to be  installed
  locales: Depends: glibc-2.3.5-0ubuntu1
  wine: Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed        Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed        Depends: libxml2 (>= 2.6.24) but 2.6.21-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by sbassett on 2006-08-27
You state that you upgraded ubuntu. Did you upgrade from Breezy to Dapper??? If so, it appears that you are still using the Breezy sources, which is leading to a LOT of unmet dependencies. This would be the case if you are trying to move to KDE 3.5.4.

---

### Post by Bachstelze on 2006-08-27
*slaps forehead*

How on earth could I miss that...

**p0pnfresh**, how did you upgrade ? You have to get a Dapper sources.list to do it properly...

---

### Post by p0pnfresh on 2006-08-27
ok, 

How do I ckeck which UBUNTU version do I have? 

Maybe I'm confused. I think I updated UBUNTU by clicking a notice in the upper tray. It's not the same as upgrading right?

---

### Post by Bachstelze on 2006-08-27
nope lol, it just updates your packages :) Here's in short how do upgrade :

open your sources.list

```
gkudo gedit /etc/apt/sources.list
```

delete everything and copy/paste [this](http://paste.ubuntu-nl.org/6666) instead, don't forget to add the line for KDE repo as I mentioned above. then save/close gedit and run

```

sudo apt-get update
sudo apt-get dist-upgrade
```

beware, it will take quite a while !

---

### Post by p0pnfresh on 2006-08-27
Ok thnx, I'm doing what you've instructed. I've no idea if it'll solve my problem but hey, its fun! :KS

---

### Post by p0pnfresh on 2006-08-27
# apt-get update went on fine, however,

# apt-get dist-upgrade 

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libarts1-dev: Depends: libartsc0-dev (= 1.4.3-0ubuntu1) but 1.5.4-1 is installed
  libasound2-dev: Depends: libasound2 (= 1.0.9-2) but 1.0.11-7 is installed
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6.ds1-4 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6.ds1-4 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-5) but it is not installable
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.3-3) but 2.8.3-0ubuntu1 is installed
  locales: Depends: glibc-2.3.5-0ubuntu1
  wine: Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is installed
        Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is installed
        Depends: libxml2 (>= 2.6.24) but 2.6.21-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

---

### Post by Bachstelze on 2006-08-27
It suggests using -f so go for it ;)

sudo apt-get -f install

---

### Post by p0pnfresh on 2006-08-27
Ok, wouldn't it mess up my system?

How can I enclose the code in a scrollbar box for better reading like you do? I don't think it's nice to paste it like this, but oh well, look at this it just makes me nervous. Do you think it's ok to proceed? :confused: :confused: 

root@p0pnfresh:/home/jose# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  belocs-locales-bin ca-certificates cpp-3.4 cpp-4.0 gcc-3.4-base gcc-4.0-base
  gcj-4.0-base gconf2 gconf2-common gettext gij-4.0 gnome-applets-data
  gs-common gs-esp gstreamer0.10-alsa gstreamer0.10-plugins-base hplip-data
  iso-codes language-selector-common laptop-mode-tools libavahi-common-data
  libavahi-common3 libavahi-glib1 libbeagle0 libbonobo2-0 libbonobo2-common
  libbtctl2 libcairo2 libcdio6 libcupsys2 libcupsys2-gnutls10 libdrm2
  libedataserver1.2-7 libegroupwise1.2-9 libfreetype6 libgcj6 libgconf2-4
  libgcrypt11 libglib2.0-0 libglib2.0-data libgnutls12 libgpg-error0
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgutenprint2 libidn11
  libidn11-dev libkadm55 libkrb53 libogg0 liboil0.3 libopencdk8
  libopenobex-1.0-0 libpango1.0-0 libpango1.0-common libsasl2 libsasl2-modules
  libsexy2 libsoup2.2-8 libssl0.9.8 libtasn1-2 libtasn1-2-dev libvorbis0a
  libvorbisenc2 libxml2 locales openssl python-gst0.10 radeontool
  xserver-xorg-driver-neomagic xserver-xorg-driver-siliconmotion
  xserver-xorg-input-citron xserver-xorg-input-kbd xserver-xorg-input-mouse
Suggested packages:
  gcc-4.0-locales gettext-doc gcj-4.0 libgcj6-awt rng-tools gnutls-bin
  gstreamer0.10-tools gstreamer0.10-plugins gutenprint-locales krb5-doc
  krb5-user ttf-thryomanes
Recommended packages:
  curl psfontmgr hplip libgcj6-jar libtasn1-2-bin
The following packages will be REMOVED:
  acpi-support akode akregator amor apt apt-utils aptitude ark arts
  artsbuilder aspell aspell-en atlantik atlantikdesigner base-config
  bluez-cups bug-buddy build-essential cervisia comerr-dev
  contact-lookup-applet cupsys cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data dcoprss dselect dvd+rw-tools eog evince
  evolution evolution-exchange evolution-plugins evolution-webcal eyesapplet
  fifteenapplet file-roller firefox firefox-gnome-support foomatic-db-hpijs
  freeglut3 g++ g++-4.0 g77 g77-3.4 gaim gcalctool gcc gcc-3.4 gcc-4.0
  gconf-editor gdm gedit gksu gnome-about gnome-app-install gnome-applets
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
  gnome-media gnome-netstatus-applet gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-utils gnome-volume-manager
  gnomemeeting groff-base gstreamer0.8-misc gstreamer0.8-vorbis gthumb
  gtkhtml3.8 gucharmap hal-device-manager hpijs hplip-base hwdb-client juk
  kaboodle kaddressbook kaddressbook-plugins kalarm kalzium kamera kandy
  kappfinder karm kasteroids kate kate-plugins katomic kaudiocreator kbabel
  kbackgammon kbattleship kblackbox kbounce kbruch kbstate kbugbuster
  kcachegrind kcalc kcharselect kcoloredit kcontrol kcron kdat kde
  kde-amusements kde-core kdeaccessibility kdeaddons kdeaddons-kfile-plugins
  kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-style
  kdeartwork-theme-window kdebase kdebase-bin kdebase-kio-plugins kdeedu
  kdegames kdegraphics kdegraphics-kfile-plugins kdelibs kdelibs-bin
  kdelibs4-dev kdelibs4c2 kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesdk
  kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdetoys kdeutils kdevelop3
  kdevelop3-data kdevelop3-plugins kdewebdev kdf kdict kdvi kedit keduca
  kenolaba kfax kfilereplace kfind kfloppy kfouleggs kgamma kget kghostview
  kgoldrunner kgpg khangman khelpcenter khexedit kicker kicker-applets
  kiconedit kig kimagemapeditor kitchensync kiten kjots kjumpingcube
  klaptopdaemon klatin kleopatra klettres klickety klines klinkstatus klipper
  kmag kmahjongg kmail kmailcvt kmenuedit kmessedwords kmid kmilo kmines kmix
  kmoon kmousetool kmouth kmplot kmrml kmtrace knewsticker knode knotes kodo
  kolf kolourpaint kommander kompare konq-plugins konqueror
  konqueror-nsplugins konquest konsole konsolekalendar kontact kooka kopete
  korganizer korn kpackage kpager kpat kpdf kpercentage kpersonalizer kpf
  kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor kreversi krfb kruler
  ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim ksirc
  ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash
  kspy kstars ksvg ksync ksysguard ksysv kteatime ktimer ktip ktnef ktouch
  ktron kttsd ktuberling kturtle ktux kuickshow kuiviewer kuser kverbos kview
  kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin kwin4
  kwordquiz kworldclock kxsldbg language-selector language-support-en lftp
  libart-2.0-dev libarts1-audiofile libarts1-dev libarts1-mpeglib
  libarts1-xine libarts1c2 libartsc0-dev libasound2-dev libaspell-dev
  libaspell15 libaudiofile-dev libboost-python1.33.0 libbz2-dev libc6-dev
  libc6-i686 libcupsys2-dev libcvsservice0 libdbus-qt-1-1c2 libdjvulibre15
  libedataserverui1.2-6 libeel2-2 libesd0-dev libexchange-storage1.2-0
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgc1c2 libgcc1
  libgcrypt11-dev libgksu1.2-0 libgksuui1.0-0 libgl1-mesa libgl1-mesa-dev
  libgl1-mesa-dri libgle3 libglib2.0-dev libglu1-mesa libglu1-mesa-dev
  libglut3 libgnome-desktop-2 libgnome2-perl libgnomecupsui1.0-1 libgnomeui-0
  libgnutls11-dev libgpg-error-dev libgtkhtml3.8-15 libgtkspell0 libgucharmap4
  libid3-3.8.3c2 libjpeg62-dev libkcal2a libkcddb1 libkdeedu1 libkdegames1
  libkdepim1 libkgantt0 libkiten1 libkleopatra0a libkonq4 libkpimexchange1
  libkpimidentities1 libkrb5-dev libkscan1 libksieve0 libktnef1 libmimelib1a
  libmng-dev libmodplug0c2 libmusicbrainz2c2 libmusicbrainz4c2 libmyspell3c2
  libogg-dev libopenal0 libopencdk8-dev libopenexr-dev libopenexr2c2
  libopenh323-1.15.3c2 libpanel-applet2-0 libpcre3-dev libpng12-dev
  libpoppler0c2 libpoppler0c2-glib libpt-1.8.3c2 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libqt3-mt libqt3-mt-dev librss1
  libsasl2-dev libsigc++-1.2-5c2 libsmpeg0c2 libstdc++6 libstdc++6-4.0-dev
  libstlport4.6c2 libtag1c2 libtiff4-dev libtiffxx0c2 libtunepimp-bin
  libtunepimp2c2 libvorbis-dev libwpd8c2 libwvstreams4.0c2-base
  libwvstreams4.0c2-extras libxft-dev libxine1c2 libxml2-dev libxplc0.3.11c2
  libxslt1-dev lshw lskat man-db mesa-utils mozilla-firefox-locale-en-gb
  mpeglib nautilus nautilus-cd-burner nautilus-sendto networkstatus noatun
  noatun-plugins notification-daemon openoffice.org2 openoffice.org2-base
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-evolution openoffice.org2-gnome
  openoffice.org2-impress openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer pinentry-qt powermanagement-interface poxml
  python-apt python-gnome2 python-gnome2-extras python-id3lib
  python-musicbrainz python-uno python2.4-apt python2.4-gnome2
  python2.4-gnome2-extras python2.4-id3lib python2.4-musicbrainz qt3-dev-tools
  quanta rhythmbox rss-glx secpolicy serpentine sound-juicer synaptic telnet
  toshset totem totem-gstreamer tsclient ubuntu-desktop ubuntu-minimal
  ubuntu-standard umbrello update-manager update-notifier vimpart vino w3m
  wine wvdial x-window-system-core xbase-clients xdriinfo xlibs-static-dev
  xorg-driver-synaptics xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glide
  xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740
  xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-sis xserver-xorg-driver-tdfx xserver-xorg-driver-tga
  xserver-xorg-driver-trident xserver-xorg-driver-tseng
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad
  xserver-xorg-input-aiptek xserver-xorg-input-calcomp
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mutouch xserver-xorg-input-palmax
  xserver-xorg-input-penmount xserver-xorg-input-spaceorb
  xserver-xorg-input-summa xserver-xorg-input-tek4957 xserver-xorg-input-void
  xserver-xorg-input-wacom xvncviewer yelp zlib1g-dev
The following NEW packages will be installed:
  belocs-locales-bin ca-certificates gcj-4.0-base gconf2-common
  gstreamer0.10-alsa gstreamer0.10-plugins-base iso-codes
  language-selector-common laptop-mode-tools libavahi-common-data
  libavahi-common3 libavahi-glib1 libbeagle0 libbtctl2 libcdio6 libcupsys2
  libdrm2 libedataserver1.2-7 libegroupwise1.2-9 libgnutls12
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgutenprint2
  libopenobex-1.0-0 libsexy2 libssl0.9.8 openssl python-gst0.10 radeontool
The following packages will be upgraded:
  cpp-3.4 cpp-4.0 gcc-3.4-base gcc-4.0-base gconf2 gettext gij-4.0
  gnome-applets-data gs-common gs-esp hplip-data libbonobo2-0
  libbonobo2-common libcairo2 libcupsys2-gnutls10 libfreetype6 libgcj6
  libgconf2-4 libgcrypt11 libglib2.0-0 libglib2.0-data libgpg-error0 libidn11
  libidn11-dev libkadm55 libkrb53 libogg0 liboil0.3 libopencdk8 libpango1.0-0
  libpango1.0-common libsasl2 libsasl2-modules libsoup2.2-8 libtasn1-2
  libtasn1-2-dev libvorbis0a libvorbisenc2 libxml2 locales
  xserver-xorg-driver-neomagic xserver-xorg-driver-siliconmotion
  xserver-xorg-input-citron xserver-xorg-input-kbd xserver-xorg-input-mouse
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libgcc1 (due to apt) libstdc++6 (due to apt)
45 upgraded, 29 newly installed, 533 to remove and 760 not upgraded.
3 not fully installed or removed.
Need to get 42.9MB of archives.
After unpacking 1078MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] n
Abort.

---

### Post by Bachstelze on 2006-08-27
If you go on with it, it seems it wil uninstall all of your graphical stuff. Then you can reinstall it from command line. There might be an other way but I don't know it.

EDIT : hmm, it seems it will also remove your c++ libs, better not do it I gues, can you afford a reinstall ?

---

### Post by p0pnfresh on 2006-08-27
Synaptic just gave me 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by Bachstelze on 2006-08-27
If I were you, I'd just reinstall UBuntu and do the upgrade properly.

---

### Post by p0pnfresh on 2006-08-27
Ok, but I'll try the apt-get -f install and break my Ubuntu first! =D> =D> =D>

---

### Post by Bachstelze on 2006-08-27
And be sure that the first thing you do is upgrade to Dapper (or use a Dapper CD).

---

### Post by p0pnfresh on 2006-08-27
ok, I'm in the fresh install. I'll upgrade as you've instructed! :D

---

### Post by Bachstelze on 2006-08-27
And then to install KDE, run sudo aptitude install kubuntu-desktop :)

(aptitude intead of apt-get makes it easier to remve KDE later if you don't like it)

---

### Post by p0pnfresh on 2006-08-27
merci beaucoup!

Upgrade is taking forever, but running smoothly so I'm happy. :KS :KS :KS

---

