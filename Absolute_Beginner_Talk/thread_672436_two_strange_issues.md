---
title: "two strange issues"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-19
When i try and right click on my desktop, it will not bring up a menu and when i log out and log back in, i do not see my desktop...I have to System>Preferences>Appearance then almost click on background for it to come up?  Any idea why?

This all started happening when I installed kdecore and removed all the kde items through synmaptic

---

### Post by ajgreeny on 2008-01-19
Sounds like you indvertently removed something else with the kde packages.  Check in synaptic File>History to see what actually installed for kde-core, and then uninstalled, to see if there was anything that shouldn't have gone.

---

### Post by sports fan Matt on 2008-01-19
ok, i will post to see if you guys see something that went cause im not sure: 
Completely removed the following packages:
dolphin-kde4
kappfinder-kde4
kde-icons-oxygen
kde4libs-bin
kdebase-data-kde4
kdebase-runtime-data
kdebase-runtime-data-common
kdebase-workspace-data
kdelibs5-datakdepimlibs-data
ksysguardd-kde4
libkonq5-templates
libphonon4
libqimageblitz4
libcaptury0
libpostproc1d
libqt4-gui
libqt4-qt3support
libqt4-sql
libraptor1
librasqal0
librdf0
libsdl1.2debian-alsa
libsoprano4
libstreamanalyzer0dbus-x11
exiv2
kdebase-workspace-bin
kdelibs5
kdepasswd-kde4
kdepimlibs5
kfind-kde4
klipper-kde4
konqueror-kde4
konsole-kde4
ksysguard-kde4
kwin-kde4
kwrite-kde4
libaudio2
libavcodec1d
libavutil1d
libcapseo0
libclucene0
libcurl3
libdirectfb-0.9-25
libexiv2-0
libgpgme11
libgsm1
libkonq5
libmad0
libmng1
libmodplug0c2
libmpcdec3
libmysqlclient15off
libopenexr2c2a
libplasma1
libpq5
libpth20
libpulse0
libqt4-core
libsqlite0
libstreams0
libxcb1
libxine1-doc
libxvmc1
mysql-common
systemsettings-kde4

Removed the following packages:
libcaptury0
libpostproc1d
libqt4-gui
libqt4-qt3support
libqt4-sql
libraptor1
librasqal0
librdf0
libsdl1.2debian
libsdl1.2debian-alsa
libsoprano4
libstreamanalyzer0
libstrigiqtdbusclient0
libxcb-shape0
libxcb-shm0
libxcb-xv0
libxine1
libxine1-console
libxine1-ffmpeg
libxine1-gnome
libxine1-misc-plugins
libxine1-plugins
libxine1-x
qt4-qtconfig
raptor-utils
redland-utils

libstrigiqtdbusclient0
libxcb-shape0
libxcb-shm0
libxcb-xv0
libxine1
qt4-qtconfig

Anything in there look suspicious?  I know alot of KDE Packages were removed, but im not sure if something bundled went too:)

---

### Post by sports fan Matt on 2008-01-19
Now im confused...

---

### Post by RomeReactor on 2008-01-19
Hi. If you're in Gnome, try:
```
sudo aptitude install ubuntu-desktop
```
If it installs some packages, then reboot and see if it helps.

---

### Post by sports fan Matt on 2008-01-19
i'll try it, then remove things like rythymbox since i dont listen to music online:)

---

