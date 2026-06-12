---
title: "Kubuntu removal"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-02
Hi there, i installed the 
kubuntu desktop
package from the synaptics package manager, and now i'm having regrets. For the time being i'd like to stick to gnome, just to get to learn ubuntu.  Here's the problem though, when i installed kubuntu desktop, it also installed a bunch of other packages.  My question is: is there a way to uninstall all of the packages that kubuntu desktop installed as well as kubuntu desktop?  I just want to get rid of this in it's entirety.
Example:
it installed many, many programs, like:
Ark
Katapult
Knotes
digiKam
Kjobviewer
Kaffeine

I want all of these gone.  Will i have to go through 1 by 1 and uninstall of them to get rid of the entire kubuntu desktop package, or is there an easier way? I just want plain old gnome!
thanks

---

### Post by dje on 2007-11-02
Try:
```
sudo apt-get autoremove --purge kubuntu-desktop
sudo apt-get install ubuntu-desktop
```

HTH :)

---

### Post by jordank on 2007-11-02
that didn't work. i'm still left with krap like:

Kontact
Kaffeine
Konversation
Kopete
Knotes
Katapult.

this is the stuff i wanted to get rid of.
Do i have remove everything individually?

---

### Post by RomeReactor on 2007-11-02
Hi. Since you didn't install kubuntu-desktop using aptitude, you'll need to enter the command listed In [ PsychoCats]("http://www.psychocats.net/ubuntu/puregnome"). Choose the command below the "Remove Kubuntu" text in orange.

---

### Post by jordank on 2007-11-02
awesome. thank you very much, that was a huge command line.
It's working it's magic right now.
Question though:
How do you find these commands?
did you just google it, or are they certain reference sites i should know for future?

Thanks a lot :)

---

### Post by rsambuca on 2007-11-02
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

---

