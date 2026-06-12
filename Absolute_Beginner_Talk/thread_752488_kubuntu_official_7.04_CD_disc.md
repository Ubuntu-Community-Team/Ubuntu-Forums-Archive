---
title: "kubuntu official 7.04 CD disc"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-11
Hello,

i have an official Kubuntu 7.04 install cd...

what command should i use at the boot prompt....so the CD only installs a base ubuntu system...... just a base ubuntu install giving a command prompt screen .....and not the full kde gui install....

would there be any extra commands...... that would allow it to load kde library's but not the actual kde desktop?

sorry for any missunderstanding...

Vince.

---

### Post by hyper_ch on 2008-04-11
download the alternate install cd (or server). That one will let you install a base system.

---

### Post by vinceUUUU on 2008-04-11
Hello

yeah...sorry but that is what i just can't do..downloading...cos my broadband supply company cap my data rates...

surely the boot prompt of this kubuntu CD will allow choices on the type of install?...as arguments 

like

boot  ==kde-  

(or something?)

no?

thanks

Vince.

---

### Post by bt224 on 2008-04-11
You can always install it from the disk, then not use it. Someone will need to confirm it, but I think you can even remove it after install.

---

### Post by vinceUUUU on 2008-04-11
Hello

very good idea...why didn't i think of that...?

install the whole thing then remove the kde desktop...to get the distro just to boot up into a command prompt style screen...

then put a new window manager in...windowmaker 

i have got all the instructions here for doing this....in detail

i wonder if removing kde desktop will still leave behind the base kde library's....(if i understand things correctly, this is what i want...

it would be good to still have those kde library's...and just loose the memory hogging KDE desktop....

yes

thanks

Vince.



thanks a lot

Vince.

---

### Post by bt224 on 2008-04-11
Uninstalling using Synaptic Package Manager should grab everything.

---

### Post by zvacet on 2008-04-11
You can allways download [minimal.](https://help.ubuntu.com/community/Installation/MinimalCD)If you want to rermove KDE 

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon
```

---

### Post by stchman on 2008-04-11
> **vinceUUUU said:**
> Hello

yeah...sorry but that is what i just can't do..downloading...cos my broadband supply company cap my data rates...

surely the boot prompt of this kubuntu CD will allow choices on the type of install?...as arguments 

like

boot  ==kde-  

(or something?)

no?

thanks

Vince.

Time to get a new broadband that does not cap you and tell you what you can and cannot do.

---

