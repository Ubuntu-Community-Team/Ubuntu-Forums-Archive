---
title: "Installing kiba-dock removes KDE apps"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-16
I'm trying to install kiba-dock by following [this howto.]("http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock") 


The first thing I had to do was **sudo aptitude remove automake**
Unfortunately...
```
sudo aptitude remove automake1.4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater akregator ark arts debtags dhcdbd digikam
  gtk-qt-engine gwenview hwdb-client-kde k3b karm katapult kate kbstate
  kcron kde-guidance kde-guidance-powermanager kde-icons-mono
  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins klipper kmag kmailcvt kmenuedit kmilo
  kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf
  konq-plugins konqueror-nsplugins konversation kooka kpdf kpf kppp krdc
  krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg
  ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts
  kwalletmanager kwin-style-crystal libavahi-compat-libdnssd1 libexiv2-0.12
  libflac++5c2 libjpeg-progs libk3b2 libkexiv2-0 libkipi0 liblockdev1
  libnl1-pre6 libnm-util0 libpythonize0 libqt4-qt3support libqt4-sql
  librsync1 libskim0 libsqlite0 libtdb1 network-manager networkstatus
  poster psutils pykdeextensions python-kde3 python-qt4 python2.5-dev qobex
  rdiff-backup scim-qtimm skim software-properties-kde speedcrunch
0 packages upgraded, 0 newly installed, 109 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 258MB will be freed.
Do you want to continue? [Y/n/?]           
```

What do I do now? Why does it want to uninstall kde apps?

---

### Post by rabbitnightmare on 2008-05-09
Because Kiba-Dock replaces these

---

### Post by russo.mic on 2008-05-09
NO NO NO NO

I'm pretty sure kiba-dock shouldn't remove adept_notifier for example.

kiba-dock doesn't remove these applications.  Your removing automake1.4.  I believe that what you have to do is remove that to install the newer automake.  

Try just installing the automake version over 1.4, it shouldn't let you if there's a problem.  It looks like you have a dependency problem.
but DO NOT remove all those applications.  that would be bad.  I suspect it's trying to remove the kubuntu-desktop package.

Russo

---

