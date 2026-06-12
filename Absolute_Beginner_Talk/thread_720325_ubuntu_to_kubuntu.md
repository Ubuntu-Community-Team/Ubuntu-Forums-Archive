---
title: "ubuntu to kubuntu"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-03-10
is it necessary to think of kubuntu 7.10 as separate system from ubuntu 7.10?  I mean, can't I have both on my system, and simply choose which to use at logon.  With another linux distribution I was trying, I just selected Gnome or KDE at logon - 

so, I guess I'm asking, is the only difference between Ubuntu and Kubuntu the choice of desktop environment used by default?  And, can I just download the kde base and tools and have both, with out using the kubuntu install CD?

thanks :)

---

### Post by NightwishFan on 2008-03-10
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

No thats the only difference. (as far as I know) You can use both if you wish.

---

### Post by Arthur Archnix on 2008-03-10
Yup. Open a terminal and type:
```
sudo apt-get install kubuntu-desktop
```
When it's done, log out and choose kde at the session startup menu.

---

### Post by pbpersson on 2008-03-10
Yes, that is totally true - the only difference is that Ubuntu uses Gnome and Kubuntu uses KDE.  It is really the same OS with a different face

If you can get them both loaded and working on your machine then you can have the same OS with a different name each time you logon  :)

I say IF because I had some weird problems doing that, but that is another story.....  :confused:

---

### Post by forestpixie on 2008-03-10
I was under the impression that using aptitude made it easier to get rid if you so decided

---

### Post by .nedberg on 2008-03-10
> **forestpixie said:**
> I was under the impression that using aptitude made it easier to get rid if you so decided

```
apt-get autoremove kubuntu-desktop
```will do what aptitude did before. I don't think there is any reason to use aptitude instead of apt-get anymore. I use only apt-get and I have not had one single problem with it.

---

### Post by forestpixie on 2008-03-10
I've only ever used aptitude to install kubuntu- xubuntu-desktops - following advice on the psychocat pure gnome page, whether that's right or wrong I'm not sure

```
sudo aptitude remove kubuntu-desktop
```

instead of

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

---

### Post by .nedberg on 2008-03-10
> **forestpixie said:**
> I've only ever used aptitude to install kubuntu- xubuntu-desktops - following advice on the psychocat pure gnome page, whether that's right or wrong I'm not sure


You are not wrong! But ```
sudo apt-get autoremove kubuntu-desktop
``` will do just the same as ```
sudo aptitude remove kubuntu-desktop
``` I think the psychocat page is a bit outdated as this is a "new" feature of apt-get.

---

### Post by forestpixie on 2008-03-10
ok thanks for letting me know about that :)

---

