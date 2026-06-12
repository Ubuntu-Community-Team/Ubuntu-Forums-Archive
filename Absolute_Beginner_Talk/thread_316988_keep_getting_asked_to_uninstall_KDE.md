---
title: "keep getting asked to uninstall KDE"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-12-11
Whenever I try to install anything using the terminal, I am faced with this:

> ross@ross-laptop:~$ sudo aptitude install neverball
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater apt-index-watcher bogofilter bogofilter-bdb 
  bogofilter-common debtags hwdb-client-kde karm katapult kbstate 
  kde-guidance kde-guidance-powermanager kde-icons-mono kde-systemsettings 
  kdebluetooth kdenetwork-filesharing kdenetwork-kfile-plugins 
  kdepim-kresources kdepim-wizards kdnssd keep kio-apt kio-locate 
  kitchensync kmag kmailcvt kmilo kmousetool kmplayer-base 
  kmplayer-konq-plugins knotes koffice-data koffice-libs kontact kopete 
  korganizer kpf kppp krdc krfb krita krita-data ksnapshot ksvg ksystemlog 
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs 
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal 
  language-selector-qt latex-xft-fonts libgmp3c2 libjasper-runtime 
  libkpimexchange1 liblockdev1 libpythonize0 libqt-perl libqt4-core 
  libqt4-gui libqt4-qt3support libqt4-sql librsync1 libskim0 libsmokeqt1 
  libsqlite0 libtdb1 openoffice.org-kde pykdeextensions python-elementtree 
  python-kde3 python-qt4 python2.4-dev qca-tls qobex rdiff-backup 
  scim-qtimm skim speedcrunch 
The following NEW packages will be automatically installed:
  neverdata 
The following NEW packages will be installed:
  neverball neverdata 
0 packages upgraded, 2 newly installed, 87 to remove and 0 not upgraded.
Need to get 14.5MB of archives. After unpacking 194MB will be freed.
Do you want to continue? [Y/n/?] 


It seems that it's asking me if I want to install neverball and remove KDE... how can I fix this?!

---

### Post by capink on 2007-05-24
try the following command
```
sudo aptitude keep-all
```

---

