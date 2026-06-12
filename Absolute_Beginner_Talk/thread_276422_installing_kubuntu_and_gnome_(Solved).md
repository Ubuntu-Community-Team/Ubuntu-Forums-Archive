---
title: "installing kubuntu and gnome (Solved)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-12
i am trying to install kde so i can switch from gnome to kde and vice versa. when i attempted to install kubuntu-desktop, it failed. here's what happened.

```
sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libpoppler1-qt
The following NEW packages will be automatically installed:
  adept akregator ark arts artsbuilder dcraw debtags flac
  gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm katapult
  kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libiso9660-4 libjasper-runtime libjpeg-progs libk3b2 libkexif1 libkipi0
  libkpimexchange1 libkscan1 liblockdev1 libpythonize0 libqt-perl librsync1
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libvcdinfo0
  ncompress ocrad openoffice.org-kde poster psutils pykdeextensions
  python-kde3 python2.4-dev python2.4-kde3 qca-tls qobex rdiff-backup
  scim-qtimm skim speedcrunch vcdimager wlassistant zoo
The following NEW packages will be installed:
  adept akregator ark arts artsbuilder dcraw debtags flac
  gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm katapult
  kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libiso9660-4 libjasper-runtime libjpeg-progs libk3b2
  libkexif1 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libpythonize0
  libqt-perl librsync1 libsamplerate0 libsensors3 libskim0 libsmokeqt1
  libtdb1 libvcdinfo0 ncompress ocrad openoffice.org-kde poster psutils
  pykdeextensions python-kde3 python2.4-dev python2.4-kde3 qca-tls qobex
  rdiff-backup scim-qtimm skim speedcrunch vcdimager wlassistant zoo
0 packages upgraded, 128 newly installed, 0 to remove and 0 not upgraded.
Need to get 104MB of archives. After unpacking 318MB will be used.
The following packages have unmet dependencies:
  libpoppler1-qt: Depends: libpoppler1 (= 0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kdegraphics-kfile-plugins [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libpoppler1-qt [Not Installed]

Score is 62

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

```

---

### Post by John.Michael.Kane on 2006-10-12
In synaptic click edit then fix broken packages

Then try installing libpoppler1-qt alone frist following that by installing kubuntu-desktop.

---

### Post by shanepardue on 2006-10-12
synaptic doesn't see any broken packages even after reloading. when i tried to install libpoppler1-qt, i got "libpoppler1-qt:
  Depends: libpoppler1 (=0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is to be installed"

---

### Post by aysiu on 2006-10-12
Maybe you have conflicting repositories.

Try getting a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then try again: ```
sudo aptitude update
sudo aptitude -f install
sudo aptitude install kubuntu-desktop
```

---

### Post by shanepardue on 2006-10-13
i followed those steps then installed libpoppler1-qt. that caused it to work. i did have to install libpoppler1-qt before installing kubuntu-desktop to avoid errors.

thanks guys!

---

### Post by shanepardue on 2006-10-13
oh no! i lost all my programs! the command "sudo aptitude -f install" must've gotten rid of everything!

is there s way to get them back?

---

### Post by aysiu on 2006-10-13
*All* your programs?

How about this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop kubuntu-desktop
```

---

### Post by shanepardue on 2006-10-13
sorry, i freaked out a little bit..it wasn't all, but there were a few important ones. i've since installed them and i think i'm ok now. what exactly was that command?

thanks again for all your help! i've been on these forums for a little while now and i've seen what you do for the community. i respect your dedication and patience in a big way!

---

### Post by aysiu on 2006-10-13
That command is supposed to try to fix broken packages.

---

