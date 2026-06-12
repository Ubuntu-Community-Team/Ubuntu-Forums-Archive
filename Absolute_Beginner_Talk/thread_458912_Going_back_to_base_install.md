---
title: "Going back to base install?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by freakboysystem on 2007-05-30
Hey, Is there a way to go back to ubuntu default settings and programs. because ive manked my ubuntu up and also broke my dvd drive so i have to wait 2 weeks until it get shipped by sony. AND I REALLY NEED MY PC WORKING!!!
Thankyou, any info or tips is really appreciated.

---

### Post by moffa on 2007-05-30
What's broken with it? Maybe we can try to help you fix it.

---

### Post by Simran on 2007-05-30
I had this problem at one point, my CD-Drive broke and i messed up my ubuntu So i found a guide to re-installing from a USB Key. So if you have a 1GB USB Key and access to windows try following this guide:

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

You can use any .iso doesn't just have to be 6.10 i got it to work with 7.04

I'm pretty sure it only works with live CD's i couldn't get it going with an alternate but might have just been me :)

Simran

---

### Post by sankarv on 2007-05-30
if u remember the packages u installed seperately after os install u could use synaptic and then remove the newly installed ones. 


to get back the default user settings for gnome, just delete the folders (.gnome, .gnome2, .gconf, .gconfd, .metacity).  they will be created once u login again.

---

### Post by freakboysystem on 2007-05-30
Right, I have been using ubuntu for 3 weeks then for some foolish reason i heard that you can run ubuntu and kubuntu so i tried the command line sudo apt-get install kubuntu-desktop, (i thought it would do something like let me choose os when i switched my machine on) all it did was change the startup splash to kubuntu and changed the logon screen, then i noticed when i press the little power button on th ubuntu desktop the screen that shows doesn't have the power off button, i have now tried sudo apt-get remove kubuntu-desktop this doesn't do jack. when installing that kubuntu package it also install every single piece of kubuntu software which is really annoying PLEASE PLEASE PLEASE HELP ME!!!

---

### Post by Simran on 2007-05-30
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```

You have to specifiy the packages individually if you use apt-get, next time use aptitude then you can just aptitude remove kubuntu-desktop
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) For future reference :)

Simran

---

### Post by cferthorney on 2007-05-30
Try the following [Link to restore pure GNOME (Pyschocats.net) ](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Docter on 2007-05-30
I tried KDE and too wasn't happy with the way it infects... er installs. Even removing everything by hand with the appropriate date-stamp I found that the splash screen endured and who knows what else. So annoyed was I that I reinstalled ubuntu and can quite happily live without KDE. Apparently, looking like windows isn't enough, it tries to behave like it too:???:.

---

### Post by freakboysystem on 2007-05-30
The code didn't work still got kubuntu splash and logon, and the power button icon has still disapeared.

---

### Post by Simran on 2007-05-30
> **freakboysystem said:**
> The code didn't work still got kubuntu splash and logon, and the power button icon has still disapeared.

Have all the KDE apps gone now though ?

Simran

---

### Post by freakboysystem on 2007-05-30
ive done it, i used konsole and put in the sudo apt-get remove kubuntu-desktop, obviously doesn't work with terminal. thanks for all your knowledge.

---

### Post by freakboysystem on 2007-05-30
i found a way, i used konsole & put in sudo apt-get remove kubuntu-desktop, so it doesn't work with terminal thankyou. i just posted this repy as a new post i dint mean to. ignore it please.
thankyou for your knowledge.

---

