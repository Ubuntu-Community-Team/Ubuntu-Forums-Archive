---
title: "Removing All KDE Software from Ubutnu installed by &quot;kubuntu-desktop&quot; package"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-19
Hi I recently installed the kubuntu-desktop package on my Ubunru machine as referred to [here]("http://ubuntuforums.org/showthread.php?t=474647") however I decided to uninstall the kubuntu-desktop package again, but now I'm left with all the KDE software on my ubuntu machine? How do I uninstall that again?

---

### Post by sailor2001 on 2007-06-19
why uninstall? KDE is compatible with gnome and works just fine in gnome...I have almost all KDE programs running in my gnome

---

### Post by corney91 on 2007-06-19
Hav you tried 'sudo apt-get autoclean', 'sudo apt-get autoremove', or sudo 'apt-get remove --purge kubuntu-desktop'. You could also try [this thread.]("http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+unnecessary+files") If none of these work you may have to uninstall them manually, or reinstall which is what I did, but I'd planned to do that anyway.

---

### Post by aktiwers on 2007-06-19
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```Hehe couldnt resist posting that :)
Its from here:
[URL="http://www.psychocats.net/ubuntu/purekde"]http://www.psychocats.net/ubuntu/puregnome
[/URL]
EDIT: Ups fixed the code and link..  was Pure KDE I posted.

---

### Post by kasperbs on 2007-06-19
:( sigh. It worked but a lot of my other software got uninstalled as well. Especially all of my MySQL databases and PHP Apache and woow. I could have just reinstalled Ubuntu and forgetting to take backup nearly.. But thanks for the link anyway

---

### Post by luvinit on 2007-06-19
It won't help you now but I think if in future you install using the command "aptitude" rather than apt-get it makes  a much better job of removing things.

---

### Post by skymera on 2007-06-19
sorry to butt in, but didnt want to start new thread.

is it possible to installl kubuntu-desktop
with all the KDE crap?

or install kubuntu-desktop and remove the KDE software. will it affect it?

---

### Post by Songwind on 2007-06-19
> **skymera said:**
> sorry to butt in, but didnt want to start new thread.

is it possible to installl kubuntu-desktop
with all the KDE crap?

or install kubuntu-desktop and remove the KDE software. will it affect it?

Since Kubuntu is Ubuntu based on KDE instead of Gnome, I'm not sure what it is you're looking to accomplish.

What do you want to have installed when you're finished?

---

### Post by skymera on 2007-06-19
i want kubuntu-desktop

but none of the KDE software that appears in ubuntu-desktop.....

---

### Post by aktiwers on 2007-06-19
**** Im really sorry about that..   :(

---

### Post by Happy_Man on 2007-06-19
> **skymera said:**
> i want kubuntu-desktop

but none of the KDE software that appears in ubuntu-desktop.....

Kubuntu-desktop without all the KDE software is... nothing. the package Kubuntu-desktop is a *metapackage* that simply points to other packages to install as dependencies. If you are looking for a bare-bones KDE install, try *kde-core*. That gives you just the basics, and from there you can customize to your taste.

---

### Post by Tyke91 on 2007-06-20
lol, kubuntu IS kde. removing all kde from kubuntu would be an issue... you wouldnt be left with anything else unless you had installed gnome or xfce or something else in it's place.

---

