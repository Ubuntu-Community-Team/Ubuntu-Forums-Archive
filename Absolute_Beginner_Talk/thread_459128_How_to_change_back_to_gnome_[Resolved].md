---
title: "How to change back to gnome? [Resolved]"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-05-30
Okay. I switched to KDE because I wanted to see what it was like, (more specifically I wanted transparent windows xD) but it was slow, and sluggish, cluttered and the transparent windows lagged. So, I want to switch back.

Okay, logging into gnome is easy enough, but when I start my PC I still get Kubuntu and blue and the kde login screen, as opposed to my regular Ubuntu one.

Any chance of changing this back?

Thanks.

---

### Post by Outrunner on 2007-05-30
If you installed with aptitude you can do
```

sudo aptitude remove kubuntu-desktop
```

if you installed with apt-get

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools
```

---

### Post by Neon_Knight on 2007-05-30
I installed it with Synaptic Package manager...

I presume I can just remove it in there...

---

### Post by Outrunner on 2007-05-30
Yes, or use the second command

---

### Post by reckless2k2 on 2007-05-30
I assume you didn't remove GNOME so you can switch between both desktop environments. In the KDM menu under or next to the username area is a box that you can switch desktop environments. Choose GNOME and then you will log back into GNOME by default from that point after. Getting the KDM login menu (KDE) to change back to the GDM login menu (GNOME) is something different. Regardless, you can login to either desktop if you wish following the instructions above and or add others to try out like fluxbox and such.

---

### Post by aysiu on 2007-05-30
If all you're worried about is the boot splash screen, you can [change that back](http://doc.gwos.org/index.php/Different_usplash) without uninstalling KDE.

Also, if you're interested in a faster KDE, you can try [*kde-core* instead of *kubuntu-desktop*](http://www.psychocats.net/ubuntu/kde-core)

If you really want to remove KDE completely, try [this](http://www.psychocats.net/ubuntu/puregnome). You'll need to do that, since you installed using Synaptic instead of *aptitude*.

---

### Post by plcdfa on 2007-05-30
> **Neon_Knight said:**
> Okay. I switched to KDE because I wanted to see what it was like, (more specifically I wanted transparent windows xD) but it was slow, and sluggish, cluttered and the transparent windows lagged. So, I want to switch back.

Okay, logging into gnome is easy enough, but when I start my PC I still get Kubuntu and blue and the kde login screen, as opposed to my regular Ubuntu one.

Any chance of changing this back?

Thanks.

Also, the lag is most probably caused by the absence of the right driver for your graphics card. Or the right graphics card. Or the right settings in xorg.conf. Anyhow, it's not KDE's fault. :D

---

### Post by Immolatus on 2007-05-30
Just remove KDM from synaptic, and all should be well. If you want Gnome by default, choose it at login. When GDM asks if it should be default answer "yes"

---

### Post by Neon_Knight on 2007-05-30
Okay, thanks for the help, guys. It's back to normal. 



I hate having an ATI card on Linux, D:  All the shiny stuff is out-of-bounds.

---

