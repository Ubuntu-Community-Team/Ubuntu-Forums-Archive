---
title: "removing KDE"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-17
I recently wanted to try out KDE because i upgraded my system memory. 

KDE is ok, but its nothing special.  I was perfectly happy with gnome.  Am i completely off base in making that statement?  Anyway, due to the fact that i was unimpressed and i have limited disk space, i am interested in removing  kde from the system.  I realize i can just choose to load gnome at the login screen, but i need to clear some space.  

Can anyone give me a reason to why i should stick with KDE or tell me how to remove it as if i had never touched it.

---

### Post by rickycodie on 2007-07-17
use this 

sudo apt-get autoremove  --purge kde-desktop

---

### Post by reset3x on 2007-07-17
> **ITdrummer said:**
> I recently wanted to try out KDE because i upgraded my system memory. 

KDE is ok, but its nothing special.  I was perfectly happy with gnome.  Am i completely off base in making that statement?  Anyway, due to the fact that i was unimpressed and i have limited disk space, i am interested in removing  kde from the system.  I realize i can just choose to load gnome at the login screen, but i need to clear some space.  

Can anyone give me a reason to why i should stick with KDE or tell me how to remove it as if i had never touched it.

See here... It will tell you how to add and remove desktop environments...

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by stchman on 2007-07-17
> **ITdrummer said:**
> I recently wanted to try out KDE because i upgraded my system memory. 

KDE is ok, but its nothing special.  I was perfectly happy with gnome.  Am i completely off base in making that statement?  Anyway, due to the fact that i was unimpressed and i have limited disk space, i am interested in removing  kde from the system.  I realize i can just choose to load gnome at the login screen, but i need to clear some space.  

Can anyone give me a reason to why i should stick with KDE or tell me how to remove it as if i had never touched it.

I have limited experience with KDE.  The only reason for choosing it over Gnome is personal preference.  Most of the info you will find here is about Gnome.

---

### Post by forestpixie on 2007-07-17
It depends on how you installed it - if you used apt-get it can be a bit different than if you used aptitude

I would look at the psychocat page re uninstalling the kubuntu desktop

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ITdrummer on 2007-07-17
Ok, i went to the link, and it says that if i used aptitude over apt-get that it would be easier to remove.  I used apt-get.  Will i have to do anything other than 
```
sudo apt-get autoremove --purge kde-desktop

```  to remove KDE and all of its components?

btw, the code I entered to instal kde was 
```
 sudo apt-get install kde
```

does this change anything?

---

### Post by forestpixie on 2007-07-17
to be honest I have no idea - I just remembered the enormous list for apt-get remove if you'd installed the desktop with apt-get instead of aptitude :D

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```

but if you only installed kde I would imagine that would be different  - and perhaps I'm getting confused between kde and kubuntu-desktop :???:

---

### Post by ITdrummer on 2007-07-17
yes, i did not install kubuntu_desktop.......any suggestions

---

### Post by forestpixie on 2007-07-17
I would assume that if you did the

sudo apt-get autoremove --purge kde-desktop

you could clear up residual configs with synaptic

---

### Post by davidjmayo on 2007-07-17
sorry another link to psychocats but there are 4 different KDE choices
    * kdebase - This is the absolute bare minimum to run KDE. You will get very little frills, and you may be missing what you consider a lot of essential software.
    * kde-core - This metapackage contains another minimal configuration for KDE but has enough to satisfy most users. The one major missing component is kde-guidance, the package that allows you to configure in the control panel preferred screen resolution and refresh rate.
    * kubuntu-desktop - This is Kubuntu's default set of applications and services.
    * kde - Everything but the kitchen sink... actually, this may have the kitchen sink, too! This metapackage points to all the KDE-related packages available. 

. I guess you did the last one in the list there?
[http://www.psychocats.net/ubuntu/kde-core#fromscratch](http://www.psychocats.net/ubuntu/kde-core#fromscratch)  --if you need it

---

### Post by ITdrummer on 2007-07-17
ok cool, i just wanted to make sure that i removed everything associated with kde as if i had never installed it.  Thanks. I shall try that line in the terminal and give it a shot.

---

