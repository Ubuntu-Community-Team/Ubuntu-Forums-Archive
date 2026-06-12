---
title: "Apt-get issues"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by bloodfyr on 2006-12-03
I recently went through my install of Kubuntu and uninstalled a bunch of the software that came preinstalled that I don't need, such as Kopete, and the bluetooth packages, for example.

I uninstalled all of them successfully. Then, later...I went to remove an LJ client that I was no longer using, and this was what I got:

```
bloodfyr@olympus:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc krfb kscd kppp libktnef1 krita-data kubuntu-default-settings libkscan1 python2.4-dev kdeprint
  adept-manager kmplayer-konq-plugins ksvg kscreensaver kwin libavahi-compat-libdnssd1 kio-locate libk3b2 libpythonize0
  vorbis-tools ksnapshot liblockdev1 kcontrol libkipi0 wlassistant mplayer-skins libkcal2b libflac++5c2 openoffice.org-kde
  libmagick++9c2a adept-installer libkexif1 kdegraphics-kfile-plugins konqueror-nsplugins kdebase-data libpoppler1-qt
  libtdb1 adept-updater kdepim-kio-plugins hwdb-client-kde qca-tls libmimelib1c2a klipper kubuntu-artwork-usplash
  kdeadmin-kfile-plugins kicker ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls dcraw kmenuedit
  pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts ksplash libkleopatra1 skim kipi-plugins
  korganizer k3b kdenetwork-kfile-plugins kdebase-kio-plugins kbstate kio-apt kwin-style-crystal arts python-qt4 kamera ark
  libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2 libkonq4 libggi2 libgii1 libksieve0 kfind
  kdebase-bin kdm speedcrunch libkpimidentities1 libskim0 kpf bogofilter-bdb libkdepim1a kdnssd kdemultimedia-kfile-plugins
  katapult poster kdenetwork-filesharing kubuntu-docs knotes bogofilter kde-guidance debtags libdbus-qt-1-1c2
  libgii1-target-x libgsl0 khelpcenter apt-index-watcher kdesktop konqueror kaddressbook libkpimexchange1
  gtk2-engines-gtk-qt knetworkconf ksysguardd konq-plugins libkmime2 psutils language-selector-qt qobex libgpgme11
  scim-qtimm kwalletmanager python-elementtree karm kate koffice-libs adept-notifier bogofilter-common libimlib2
  kde-guidance-powermanager libjpeg-progs kde-systemsettings kdepim-kresources kdepim-wizards kmilo kmplayer-base
  kaudiocreator python-kde3 kdepasswd libungif4g

```

I understand that some of them may be libraries and such attached to the old programs that I removed...but some of those are programs that I use everyday, like Katapult. And suggestions on how to get them off the list so I can run "apt-get autoremove" without losing all those programs?

---

### Post by taurus on 2006-12-03
Maybe this helps...

[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by bloodfyr on 2006-12-03
Thanks a bunch! I'll do that with my next reinstall.

---

### Post by taurus on 2006-12-03
Good luck.

---

