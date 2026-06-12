---
title: "[SOLVED] I think I totally messed up Ubuntu :("
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-02-24
Last night i was trying desperately to get my broadcom 43xx wireless card working (the light's on, it can connect to networs but it wont get packets and ubuntu kind of freezes on the internet settings because it wont let mego back to wired :( )  and i installed a KDE pack because i thought kubuntu would do better..  Well, since i just installed it on top of gnome it's not really kubuntu and it's just a bunch of cluttering programs, but how can I get rid of them ? I want my computer to go back to the way it was 12 hours ago, is it any way to do that?

---

### Post by radiocognition on 2008-02-24
How did you install KDE?  Did you use apt-get or aptitude?  Also, realize that when you log into your system, you can choose what graphics manager to use.  Its all outlined [here]("http://www.psychocats.net/ubuntu/kde")

---

### Post by biffinson on 2008-02-24
i just installed Kubuntu-Desktop and now i'm trying to uninstall it but I can't.. I installed the actual "kubuntu-desktop" but everythign else is still there and i don't knwo how to get rid of it

---

### Post by sanderella on 2008-02-24
Your problem sounds like the broadcom 43xx wireless card problem, well known, but now solved. Try pasting "broadcom 43xx wireless card" into the search box above, and follow the links. The latest versions of Ubuntu have solved this problem, try installing the latest version. I had this problem on my laptop too.

---

### Post by sanderella on 2008-02-24
> **biffinson said:**
> i just installed Kubuntu-Desktop and now i'm trying to uninstall it but I can't.. I installed the actual "kubuntu-desktop" but everythign else is still there and i don't knwo how to get rid of it

Doownload and install Gutsy Gibbon. That should overwrite what you have.

---

### Post by biffinson on 2008-02-24
used this command to get it uninstaleld :D

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-deskto

---

### Post by radiocognition on 2008-02-24
You need to uninstall all the programs that came with Kubuntu-Desktop.  This is explained [here]("http://www.psychocats.net/ubuntu/puregnome").  Run the command in your terminal and you should be back to normal.

---

