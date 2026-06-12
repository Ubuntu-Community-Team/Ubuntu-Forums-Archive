---
title: "Ubuntu: Help installing KDE"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by koganinja89 on 2007-07-22
I heard that if one installs Ubuntu then shoves the Kubuntu CD into the compy that it will notice the packages and you can install from them. If this is true why won't it work for me? I want to install KDE and I don't have have the internet at MY house. I do however have a 2 gb thumb drive and a neighbor with awesome internet. SBS how can I do it? with the whole "download all of the dependencies" thing.

__________________________________________
Thanks in advanced.

---

### Post by koganinja89 on 2007-07-22
Help please!!!

---

### Post by koganinja89 on 2007-07-22
Pppllleeeaaassseee!!!!!!!!!

---

### Post by .nedberg on 2007-07-22
You should be able to download the kubuntu-iso and burn it as a cd, then add that cd as a repository with synaptic. I am using KDE and don't have gnome installed so I can not tell you exactly how to do it. Look for somewhere you can add a cd as a repository.

When this is done you can install kubuntu-desktop

---

### Post by forestpixie on 2007-07-22
not sure but go to synaptic > edit and add cd rom that might do it for you

---

### Post by por100pre1 on 2007-07-22
These are the files you need to download:

```
sudo apt-get download adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools
```
[B]
I think it's a lot easier if tou take your PC to your neighbor's house!!![/B]

---

### Post by koganinja89 on 2007-07-22
do you have Ubuntu or Kubuntu installed because I have Already tried adding it as a cd and the list of things that can be installed is the same there are a whole bunch of blacked out ones and I don't know why.

---

### Post by sad_iq on 2007-07-22
Don't know if it will work...but here goes...You have to download the kubuntu iso image, take it to your house, burn on disk then use synaptic to add your kubuntu cd to the list of repositories...then install **kubuntu-desktop** package. Could be wrong thou...but if you can reinstall you'll have the kubuntu cd at hand!

---

### Post by por100pre1 on 2007-07-22
> **.nedberg said:**
> You should be able to download the kubuntu-iso and burn it as a cd, then add that cd as a repository with synaptic. I am using KDE and don't have gnome installed so I can not tell you exactly how to do it. Look for somewhere you can add a cd as a repository.

When this is done you can install kubuntu-desktop

I recommended that previously to this poster but he says it doesn't work....

---

### Post by koganinja89 on 2007-07-22
I have both U and KU, I don't know why I can't install anything off of the other or vise versa

---

### Post by por100pre1 on 2007-07-22
Did you try adding the CD using APTonCD?

---

### Post by sad_iq on 2007-07-22
> **koganinja89 said:**
> I have both U and KU, I don't know why I can't install anything off of the other or vise versa
You alreay have the kubuntu cd?? Why can't you add that as a repository??? Insert the cd and type in a terminal ```
sudo apt-cdrom add
``` then ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

