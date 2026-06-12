---
title: "Can I download KDE 4 from the repos?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-04-08
Read the title.

---

### Post by Oldsoldier2003 on 2008-04-08
> **Fixman said:**
> Read the title.

its in the hardy repos:

```
$ sudo apt-get install -s kde4
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amor-kde4 ark-kde4 blinken-kde4 bovo-kde4 dolphin-kde4 edict gwenview-kde4
  indi-kde4 juk-kde4 kalgebra-kde4 kalzium-data-kde4 kalzium-kde4 kamera-kde4
  kanagram-kde4 kanjidic kappfinder-kde4 katomic-kde4 kbattleship-kde4
  kblackbox-kde4 kbounce-kde4 kbruch-kde4 kcalc-kde4 kcharselect-kde4
  kcolorchooser-kde4 kcron-kde4 kde-icons-oxygen kde4-amusements kde4-core
  kde4libs-bin kdeaccessibility-kde4 kdeadmin-kde4 kdeartwork-emoticons-kde4
  kdeartwork-kde4 kdeartwork-misc-kde4 kdeartwork-style-kde4
  kdeartwork-theme-icon-kde4 kdeartwork-theme-window-kde4 kdebase-bin-kde4
  kdebase-data-kde4 kdebase-kde4 kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace
  kdebase-workspace-bin kdebase-workspace-data kdeedu-kde4
  kdegames-card-data-kde4 kdegames-kde4 kdegames-mahjongg-data-kde4
  kdegraphics-kde4 kdelibs5 kdelibs5-data kdemultimedia-kde4
  kdemultimedia-kio-plugins-kde4 kdenetwork-kde4 kdepasswd-kde4
  kdepimlibs-data kdepimlibs5 kdessh-kde4 kdetoys-kde4 kdeutils-kde4
  kdewallpapers-kde4 kdf-kde4 kdm-kde4 kfind-kde4 kfloppy-kde4
  kfourinline-kde4 kgamma-kde4 kgeography-data-kde4 kgeography-kde4 kget-kde4
  kgoldrunner-kde4 kgpg-kde4 khangman-kde4 kig-kde4 kiriki-kde4 kiten-kde4
  kjots-kde4 kjumpingcube-kde4 klettres-data-kde4 klettres-kde4 klines-kde4
  klipper-kde4 kmahjongg-kde4 kmilo-kde4 kmines-kde4 kmix-kde4 kmplot-kde4
  knetwalk-kde4 knetworkconf-kde4 knewsticker-kde4 kolf-kde4 kolourpaint4-kde4
  konqueror-kde4 konqueror-nsplugins-kde4 konquest-kde4 konsole-kde4
  kopete-kde4 kpackage-kde4 kpat-kde4 kpercentage-kde4 kppp-kde4 krdc-kde4
  kreversi-kde4 krfb-kde4 kruler-kde4 ksame-kde4 kscan-kde4 kscd-kde4
  kscreensaver-kde4 kshisen-kde4 ksnapshot-kde4 kspaceduel-kde4 ksquares-kde4
  kstars-data-kde4 kstars-kde4 ksudoku-kde4 ksysguard-kde4 ksysguardd-kde4
  kteatime-kde4 ktimer-kde4 ktouch-kde4 ktuberling-kde4 kturtle-kde4
  kuser-kde4 kwalletmanager-kde4 kwikdisk-kde4 kwin-kde4 kwordquiz-kde4
  kworldclock-kde4 kwrite-kde4 libboost-python1.34.1 libcapseo0 libcaptury0
  libcfitsio3 libclucene0ldbl libexiv2-2 libgmp3c2 libkcddb4-kde4
  libkdeedu4-kde4 libkdegames4-kde4 libkiten4-kde4 libkonq5 libkonq5-templates
  libmarble4-kde4 libnova-0.12-1 libokularcore1-kde4 libopenbabel2 libphonon4
  libplasma1 libpoppler-qt4-2 libqca2 libqca2-plugin-ossl libqimageblitz4
  libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libvncserver0 libzip1
  lskat-kde4 marble-data-kde4 marble-kde4 okular-kde4 parley-data-kde4
  parley-kde4 python-pexpect python-pycurl python-rpm smartpm-core
  superkaramba-kde4 sweeper-kde4 systemsettings-kde4 ttf-dustin ttf-sjfonts
Suggested packages:
  khelpcenter-kde4 lookup xjdic sdic-edict k3b kdebase kde-i18n
  kdebase-workspace-wallpapers kdegames-doc-html-kde4 khelpcenter libqt4-dev
  libvncserver0-dbg python-pycurl-dbg
Recommended packages:
  xine-ui kdegraphics-strigi-plugins-kde4 okular-extra-backends-kde4 pmount
  kfreebsd-gnu hurd kdenetwork-filesharing-kde4 kscreensaver-xsavers kwin
  exiv2 raptor-utils redland-utils
The following NEW packages will be installed:
  amor-kde4 ark-kde4 blinken-kde4 bovo-kde4 dolphin-kde4 edict gwenview-kde4
  indi-kde4 juk-kde4 kalgebra-kde4 kalzium-data-kde4 kalzium-kde4 kamera-kde4
  kanagram-kde4 kanjidic kappfinder-kde4 katomic-kde4 kbattleship-kde4
  kblackbox-kde4 kbounce-kde4 kbruch-kde4 kcalc-kde4 kcharselect-kde4
  kcolorchooser-kde4 kcron-kde4 kde-icons-oxygen kde4 kde4-amusements
  kde4-core kde4libs-bin kdeaccessibility-kde4 kdeadmin-kde4
  kdeartwork-emoticons-kde4 kdeartwork-kde4 kdeartwork-misc-kde4
  kdeartwork-style-kde4 kdeartwork-theme-icon-kde4
  kdeartwork-theme-window-kde4 kdebase-bin-kde4 kdebase-data-kde4 kdebase-kde4
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-data kdeedu-kde4 kdegames-card-data-kde4 kdegames-kde4
  kdegames-mahjongg-data-kde4 kdegraphics-kde4 kdelibs5 kdelibs5-data
  kdemultimedia-kde4 kdemultimedia-kio-plugins-kde4 kdenetwork-kde4
  kdepasswd-kde4 kdepimlibs-data kdepimlibs5 kdessh-kde4 kdetoys-kde4
  kdeutils-kde4 kdewallpapers-kde4 kdf-kde4 kdm-kde4 kfind-kde4 kfloppy-kde4
  kfourinline-kde4 kgamma-kde4 kgeography-data-kde4 kgeography-kde4 kget-kde4
  kgoldrunner-kde4 kgpg-kde4 khangman-kde4 kig-kde4 kiriki-kde4 kiten-kde4
  kjots-kde4 kjumpingcube-kde4 klettres-data-kde4 klettres-kde4 klines-kde4
  klipper-kde4 kmahjongg-kde4 kmilo-kde4 kmines-kde4 kmix-kde4 kmplot-kde4
  knetwalk-kde4 knetworkconf-kde4 knewsticker-kde4 kolf-kde4 kolourpaint4-kde4
  konqueror-kde4 konqueror-nsplugins-kde4 konquest-kde4 konsole-kde4
  kopete-kde4 kpackage-kde4 kpat-kde4 kpercentage-kde4 kppp-kde4 krdc-kde4
  kreversi-kde4 krfb-kde4 kruler-kde4 ksame-kde4 kscan-kde4 kscd-kde4
  kscreensaver-kde4 kshisen-kde4 ksnapshot-kde4 kspaceduel-kde4 ksquares-kde4
  kstars-data-kde4 kstars-kde4 ksudoku-kde4 ksysguard-kde4 ksysguardd-kde4
  kteatime-kde4 ktimer-kde4 ktouch-kde4 ktuberling-kde4 kturtle-kde4
  kuser-kde4 kwalletmanager-kde4 kwikdisk-kde4 kwin-kde4 kwordquiz-kde4
  kworldclock-kde4 kwrite-kde4 libboost-python1.34.1 libcapseo0 libcaptury0
  libcfitsio3 libclucene0ldbl libexiv2-2 libgmp3c2 libkcddb4-kde4
  libkdeedu4-kde4 libkdegames4-kde4 libkiten4-kde4 libkonq5 libkonq5-templates
  libmarble4-kde4 libnova-0.12-1 libokularcore1-kde4 libopenbabel2 libphonon4
  libplasma1 libpoppler-qt4-2 libqca2 libqca2-plugin-ossl libqimageblitz4
  libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libvncserver0 libzip1
  lskat-kde4 marble-data-kde4 marble-kde4 okular-kde4 parley-data-kde4
  parley-kde4 python-pexpect python-pycurl python-rpm smartpm-core
  superkaramba-kde4 sweeper-kde4 systemsettings-kde4 ttf-dustin ttf-sjfonts
0 upgraded, 183 newly installed, 0 to remove and 3 not upgraded.
Inst kde-icons-oxygen (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-runtime-data-common (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-runtime-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libclucene0ldbl (0.9.20-1 Ubuntu:8.04/hardy)
Inst libraptor1 (1.4.16-1 Ubuntu:8.04/hardy)
Inst libgmp3c2 (2:4.2.2+dfsg-1ubuntu2 Ubuntu:8.04/hardy)
Inst librasqal0 (0.9.15-2 Ubuntu:8.04/hardy)
Inst librdf0 (1.0.7-1 Ubuntu:8.04/hardy)
Inst libsoprano4 (2.0.0-1 Ubuntu:8.04/hardy)
Inst kde4libs-bin (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst kdelibs5-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst libphonon4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst libqt4-sql (4.3.4-0ubuntu2 Ubuntu:8.04/hardy) []
Inst libqt4-qt3support (4.3.4-0ubuntu2 Ubuntu:8.04/hardy) []
Inst libstreams0 (0.5.7-2 Ubuntu:8.04/hardy) []
Inst libstreamanalyzer0 (0.5.7-2 Ubuntu:8.04/hardy) []
Inst kdelibs5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-runtime-bin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst libstrigiqtdbusclient0 (0.5.7-2 Ubuntu:8.04/hardy) []
Inst kdebase-runtime (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst amor-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libzip1 (0.8-1 Ubuntu:8.04/hardy)
Inst ark-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst libkdeedu4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ttf-sjfonts (2.0.2-1ubuntu1 Ubuntu:8.04/hardy)
Inst blinken-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libkonq5-templates (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libkonq5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst dolphin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst edict (2007.09.14-1 Ubuntu:8.04/hardy)
Inst libcfitsio3 (3.040-5 Ubuntu:8.04/hardy)
Inst libnova-0.12-1 (0.12.1-1 Ubuntu:8.04/hardy)
Inst indi-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst juk-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kalgebra-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kalzium-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libopenbabel2 (2.1.1-4 Ubuntu:8.04/hardy)
Inst kalzium-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kanagram-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kanjidic (2007.09.14-1 Ubuntu:8.04/hardy)
Inst kappfinder-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kbruch-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kcalc-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kcharselect-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kcron-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-bin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdepasswd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kfind-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst konqueror-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst konqueror-nsplugins-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst konsole-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kwrite-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-workspace-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ksysguardd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libqimageblitz4 (0.0.706674-2build1 Ubuntu:8.04/hardy)
Inst kdm-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libplasma1 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst ksysguard-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy) []
Inst kdebase-workspace-bin (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst klipper-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libcapseo0 (0.3.0+svn20070725-0ubuntu1 Ubuntu:8.04/hardy)
Inst libcaptury0 (0.3.0+svn20070725-0ubuntu3 Ubuntu:8.04/hardy)
Inst kwin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst systemsettings-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdebase-workspace (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdepimlibs-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdepimlibs5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kde4-core (3.3 Ubuntu:8.04/hardy)
Inst kgeography-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kgeography-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ttf-dustin (20030517-6 Ubuntu:8.04/hardy)
Inst khangman-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libboost-python1.34.1 (1.34.1-4ubuntu3 Ubuntu:8.04/hardy)
Inst kig-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libkiten4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kiten-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst klettres-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst klettres-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kmplot-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kpercentage-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kstars-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kstars-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ktouch-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kturtle-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kwordquiz-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libmarble4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst marble-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst marble-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst parley-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst parley-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeedu-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libkdegames4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst bovo-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst katomic-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kbattleship-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kblackbox-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kbounce-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kfourinline-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kgoldrunner-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kiriki-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kjumpingcube-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst klines-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdegames-mahjongg-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kmahjongg-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kmines-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst knetwalk-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kolf-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst konquest-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdegames-card-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kpat-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kreversi-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ksame-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kshisen-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kspaceduel-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ksquares-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ksudoku-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ktuberling-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst lskat-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdegames-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kteatime-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kworldclock-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdetoys-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kde4-amusements (3.3 Ubuntu:8.04/hardy)
Inst kdeaccessibility-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst knetworkconf-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst python-pexpect (2.1-1build1 Ubuntu:8.04/hardy)
Inst python-pycurl (7.16.4-1 Ubuntu:8.04/hardy)
Inst python-rpm (4.4.2.1-1ubuntu6 Ubuntu:8.04/hardy)
Inst smartpm-core (0.52-2 Ubuntu:8.04/hardy)
Inst kpackage-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kuser-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeadmin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-emoticons-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-misc-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-style-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-theme-icon-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-theme-window-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdewallpapers-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kscreensaver-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdeartwork-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libexiv2-2 (0.16-3ubuntu1 Ubuntu:8.04/hardy)
Inst gwenview-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kamera-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kcolorchooser-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kgamma-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kolourpaint4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kruler-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kscan-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst ksnapshot-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libokularcore1-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libpoppler-qt4-2 (0.6.4-1 Ubuntu:8.04/hardy)
Inst okular-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdegraphics-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libkcddb4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdemultimedia-kio-plugins-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kmix-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kscd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdemultimedia-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kget-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst knewsticker-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libqca2 (2.0.0-3 Ubuntu:8.04/hardy)
Inst libqca2-plugin-ossl (0.1~20070904-3 Ubuntu:8.04/hardy)
Inst kopete-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kppp-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst libvncserver0 (0.9.3.dfsg.1-1ubuntu1 Ubuntu:8.04/hardy)
Inst krdc-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst krfb-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdenetwork-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Inst kdessh-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kdf-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kfloppy-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kgpg-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kjots-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kmilo-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst ktimer-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kwalletmanager-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kwikdisk-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst superkaramba-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst sweeper-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kdeutils-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Inst kde4 (3.3 Ubuntu:8.04/hardy)
Conf kde-icons-oxygen (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-runtime-data-common (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-runtime-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libclucene0ldbl (0.9.20-1 Ubuntu:8.04/hardy)
Conf libraptor1 (1.4.16-1 Ubuntu:8.04/hardy)
Conf libgmp3c2 (2:4.2.2+dfsg-1ubuntu2 Ubuntu:8.04/hardy)
Conf librasqal0 (0.9.15-2 Ubuntu:8.04/hardy)
Conf librdf0 (1.0.7-1 Ubuntu:8.04/hardy)
Conf libsoprano4 (2.0.0-1 Ubuntu:8.04/hardy)
Conf kdelibs5-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libphonon4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libqt4-sql (4.3.4-0ubuntu2 Ubuntu:8.04/hardy)
Conf libqt4-qt3support (4.3.4-0ubuntu2 Ubuntu:8.04/hardy)
Conf libstreams0 (0.5.7-2 Ubuntu:8.04/hardy)
Conf libstreamanalyzer0 (0.5.7-2 Ubuntu:8.04/hardy)
Conf kdelibs5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kde4libs-bin (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libstrigiqtdbusclient0 (0.5.7-2 Ubuntu:8.04/hardy)
Conf kdebase-runtime (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-runtime-bin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf amor-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libzip1 (0.8-1 Ubuntu:8.04/hardy)
Conf ark-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf libkdeedu4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ttf-sjfonts (2.0.2-1ubuntu1 Ubuntu:8.04/hardy)
Conf blinken-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libkonq5-templates (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libkonq5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf dolphin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf edict (2007.09.14-1 Ubuntu:8.04/hardy)
Conf libcfitsio3 (3.040-5 Ubuntu:8.04/hardy)
Conf libnova-0.12-1 (0.12.1-1 Ubuntu:8.04/hardy)
Conf indi-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf juk-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kalgebra-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kalzium-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libopenbabel2 (2.1.1-4 Ubuntu:8.04/hardy)
Conf kalzium-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kanagram-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kanjidic (2007.09.14-1 Ubuntu:8.04/hardy)
Conf kappfinder-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kbruch-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kcalc-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kcharselect-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kcron-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-bin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdepasswd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kfind-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf konqueror-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf konqueror-nsplugins-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf konsole-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kwrite-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-workspace-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksysguardd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libqimageblitz4 (0.0.706674-2build1 Ubuntu:8.04/hardy)
Conf kdm-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksysguard-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-workspace-bin (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libplasma1 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf klipper-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libcapseo0 (0.3.0+svn20070725-0ubuntu1 Ubuntu:8.04/hardy)
Conf libcaptury0 (0.3.0+svn20070725-0ubuntu3 Ubuntu:8.04/hardy)
Conf kwin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf systemsettings-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdebase-workspace (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdepimlibs-data (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdepimlibs5 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kde4-core (3.3 Ubuntu:8.04/hardy)
Conf kgeography-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kgeography-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ttf-dustin (20030517-6 Ubuntu:8.04/hardy)
Conf khangman-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libboost-python1.34.1 (1.34.1-4ubuntu3 Ubuntu:8.04/hardy)
Conf kig-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libkiten4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kiten-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf klettres-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf klettres-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kmplot-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kpercentage-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kstars-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kstars-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ktouch-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kturtle-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kwordquiz-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libmarble4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf marble-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf marble-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf parley-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf parley-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeedu-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libkdegames4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf bovo-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf katomic-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kbattleship-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kblackbox-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kbounce-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kfourinline-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kgoldrunner-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kiriki-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kjumpingcube-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf klines-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdegames-mahjongg-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kmahjongg-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kmines-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf knetwalk-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kolf-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf konquest-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdegames-card-data-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kpat-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kreversi-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksame-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kshisen-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kspaceduel-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksquares-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksudoku-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ktuberling-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf lskat-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdegames-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kteatime-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kworldclock-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdetoys-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kde4-amusements (3.3 Ubuntu:8.04/hardy)
Conf kdeaccessibility-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf knetworkconf-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf python-pexpect (2.1-1build1 Ubuntu:8.04/hardy)
Conf python-pycurl (7.16.4-1 Ubuntu:8.04/hardy)
Conf python-rpm (4.4.2.1-1ubuntu6 Ubuntu:8.04/hardy)
Conf smartpm-core (0.52-2 Ubuntu:8.04/hardy)
Conf kpackage-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kuser-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeadmin-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-emoticons-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-misc-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-style-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-theme-icon-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-theme-window-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdewallpapers-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kscreensaver-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdeartwork-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libexiv2-2 (0.16-3ubuntu1 Ubuntu:8.04/hardy)
Conf gwenview-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kamera-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kcolorchooser-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kgamma-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kolourpaint4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kruler-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kscan-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf ksnapshot-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libokularcore1-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libpoppler-qt4-2 (0.6.4-1 Ubuntu:8.04/hardy)
Conf okular-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdegraphics-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libkcddb4-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdemultimedia-kio-plugins-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kmix-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kscd-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdemultimedia-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kget-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf knewsticker-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libqca2 (2.0.0-3 Ubuntu:8.04/hardy)
Conf libqca2-plugin-ossl (0.1~20070904-3 Ubuntu:8.04/hardy)
Conf kopete-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kppp-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf libvncserver0 (0.9.3.dfsg.1-1ubuntu1 Ubuntu:8.04/hardy)
Conf krdc-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf krfb-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdenetwork-kde4 (4:4.0.3-0ubuntu1 Ubuntu:8.04/hardy)
Conf kdessh-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kdf-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kfloppy-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kgpg-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kjots-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kmilo-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf ktimer-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kwalletmanager-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kwikdisk-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf superkaramba-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf sweeper-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kdeutils-kde4 (4:4.0.3-0ubuntu2 Ubuntu:8.04/hardy)
Conf kde4 (3.3 Ubuntu:8.04/hardy)
```

---

### Post by DAC1138 on 2008-06-04
What repos should one add when trying to install from Ubuntu (not Kubuntu)? Are the kde files in the standard Ubuntu repository?

---

### Post by Fixman on 2008-06-04
> **DAC1138 said:**
> What repos should one add when trying to install from Ubuntu (not Kubuntu)? Are the kde files in the standard Ubuntu repository?

If you use Hardy, you don't need to add any repos, you just need to install kubuntu-kde4-desktop.

---

