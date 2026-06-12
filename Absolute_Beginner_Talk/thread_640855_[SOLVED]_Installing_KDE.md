---
title: "[SOLVED] Installing KDE"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-12-14
Greetings all,
I have a question about installing KDE.  I've heard great reviews about the new KDE version 4.0, and I am thinking about installing it on my system (mostly so my wife can make the transition from windows to linux).  Anywho, I really don't want to download kubuntu and loose everything I have downloaded and working now).  I am still rather new at the whole linux thing (but I am really enjoying it).  My question is, how would one go about installing KDE on ubuntu?

Thanks for the help in advance.

---

### Post by celticbhoy on 2007-12-14
To install KDE 3.x just go to system-->administration-->synaptic package manager.
Search for KDE, select and click on apply.

---

### Post by mmb1 on 2007-12-14
Like celticbhoy said, you will be able to install KDE from synaptic, but you might want to wait for KDE 4 to be officially released due to bugs that might be present

---

### Post by Sef on 2007-12-14
The [scheduled release date]("http://techbase.kde.org/Schedules/KDE4/4.0_Release_Schedule") for KDE 4.0 is 11 January.   After that it should be in the repositories within a week or so.

---

### Post by RomeReactor on 2007-12-14
Hi. KDE 4 is in its [second release candidate]("http://www.kde.org/announcements/announce-4.0-rc2.php"), but it's not yet ready for production machines, meaning that it still has bugs and quirks to iron out. I would recommend, as celticbhoy did, that you install KDE 3 and wait until next year (February, I think) when KDE 4 will be available as an update through the repositories. An easy way to install KDE is to enter the following in a terminal:
```
sudo aptitude install kubuntu-desktop
```

Once it's installed, you can select which desktop environment you want at the login screen. The benefit of using Aptitude over Synaptic is that, in case you decide to uninstall KDE later, for whatever reason, all you have to do is:
```
sudo aptitude remove kubuntu-desktop
```

Otherwise, if you used Synaptic, Add/Remove or Apt-Get to install it, the only way to completely remove KDE and all of its components would be to do:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

More information on that in [Aysiu's Psychocats page]("http://www.psychocats.net/ubuntu/puregnome").

---

### Post by SunnyRabbiera on 2007-12-14
Yeh give KDE4 a wait, as even if it goes final it might be as sturdy as a glass house built on sand in the middle of the San Andreas fault line

---

### Post by mangurt on 2007-12-14
Wow!  Thanks for all the replies.  Of course, I was the speed demon and did the synaptic grab of KDE.  Now my question is, how to I get KDE to work over gnome (I think that's what I am using)?

---

### Post by SunnyRabbiera on 2007-12-14
actually KDE and gnome are two entirely different things.
to use KDE as opposed to gnome you have to change the session, this is a non issue though as both GDM and KDM (your log in managers) have the capacity to load both.
Now during KDE's setup you will probably be offered to use either KDM or GDM, both work well so it really doesnt matter

---

### Post by mmb1 on 2007-12-14
When you get to your login screen, you should see an options menu in the lower right corner, click it and select KDE, after that, the next time you reboot, select "use last session", and you should be good to go.

---

### Post by mangurt on 2007-12-14
Great!  Thanks for all the help.  I think my wife is really going to enjoy the way this is set up!!!

---

