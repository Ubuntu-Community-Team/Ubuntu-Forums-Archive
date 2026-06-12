---
title: "incomplete Kubuntu reversion"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-03-18
Hello.

I just wanted to try the KDE desktop environment and hence i tried to install the kubuntu desktop using
```

sudo apt-get install kubuntu-desktop

```

However in the middle somewhere it asked me what kinda display manager i'd like to use and i selected gdm as i wanted to stick with gnome for most of my time.

Then it asked me something about the cnfiguration which i ddnt really read all that well..and i assumed it was talkin about the general config of my computer and i selected no  configuration from it..

then it install KDE. It somehow overwrote my openoffice installation and also made some crazy changes to my other programs...yes..my gnome programs were already there as i had expected but some of them were disabled with only the name beig stuck in the menus...

i wanted to revert back and i did
```

sudo apt-get remove kubuntu-desktop

```

and hoped everything would be fine. However, whenever i boot my PC and when it selects the kernel..it loading screen shows kubuntu instead of ubuntu when it is being booted and when it says its detecting hardware and stuff.

But suprisingly when the log in screen finally appears, its ubuntu not kubuntu...

what do u think is going on folks...i mean theres this kubuntu residue stillleft..i wonder if removing the linux kernel which im using now would help.do u have any other suggestions.

Hope to hear frm you,

Aijaz.

---

### Post by miggols99 on 2007-03-18
I think because you used apt-get you have to put the following into the terminal:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apt-index-watcher ark arts bogofilter bogofilter-bdb bogofilter-common dcraw debtags digikam enscript gtk2-engines-gtk-qt gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libc6-dev libcurl3-gnutls libdbus-qt-1-1c2 libexif-dev libflac++5c2 libgmp3c2 libgpgme11 libgphoto2-2-dev libgsl0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmagick++9c2a libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpq4 libpythonize0 libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsqlite0 libtdb1 libtunepimp3 libungif4g libvorbisfile3 libxcomposite1 libxine1 libxvmc1 linux-libc-dev mysql-common openoffice.org-kde openoffice.org-style-crystal perl-suid poster psutils pykdeextensions python-elementtree python-kde3 python-qt3 python-qt4 python-sip4 python2.4-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch vorbis-tools wlassistant
```
From [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

