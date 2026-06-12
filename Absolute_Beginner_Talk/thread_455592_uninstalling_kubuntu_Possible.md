---
title: "uninstalling kubuntu?? Possible?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by HaimishTheRed on 2007-05-26
I have 7.04 Fiesty installed so I can learn about running a LAMP server. I wanted a GUI, but i think I made a mistake and installe Kubuntu. Its using alot of crucial disk space. Is there a way I can uninstall it?

I was just looking for a basic GUI for the server.

---

### Post by DSn0wMan on 2007-05-26
If you are going to install a LAMP server you should download the server CD. It provides a very easy to install and configure a LAMP server. 

As for uninstalling Kubuntu it is best to just wipe your partition, and install the server version. You could if you want just uninstall the kubuntu-desktop meta package. This however still leaves a lot of heafty files laying around.

---

### Post by taurus on 2007-05-26
How did you install KDE (Kubuntu-desktop)?  Did you use apt-get or aptitude?

For aptitude:
```
sudo aptitude remove kubuntu-desktop
```

For apt-get:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools
```

---

### Post by Pizzarth on 2007-05-26
just reinstall the server edition, format the drive/partition while you're there.that or follow taurus is what I'd do.

---

### Post by tams on 2007-05-29
I too vote for a fresh install of the server edition so you'd get better performance with it. Servers and desktops have different optimization needs.

---

