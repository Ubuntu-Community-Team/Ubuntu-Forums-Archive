---
title: "Broken pakage has me stumped."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by BillyBudd on 2007-04-21
Running Kde in Ubuntu 6.10.  Ran fine until this morning.  System wanted to upgrade, but then announced that there were broken packages and nothing has made sense since.
I've tried all the install/update packages and everything I could find on the inet, and deleted every instance of the package files I could find, but no joy.
If someone could just tell me how to find and identify the damned package files so I can delete them, and also tell me how to get the apt-get, synaptic, etc. unstuck I'd probably be able to get back to having a usable computer.  (This is the sort of stuff I abandoned Windows to get away from. (insert lots of whining here.))

Here's the latest load of crap I've had from the system:
-----------------------------------------------------------------------------
nobreakfast@nobreakfast:~$ sudo apt-get remove opera -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto libgnucrypto-java ksystemlog gambas-gb-vb krita-data
  kubuntu-default-settings libmono2.0-cil cracklib2 python2.4-dev
  libcairo-java-gcj libmono-data-tds2.0-cil adept-manager fakeroot
  kmplayer-konq-plugins libmono-system-data2.0-cil debhelper gambas-gb-qt-ext
  kio-locate libk3b2 libpythonize0 libxvidcore4 libkipi0 libbcprov-java-gcj
  gambas-gb-eval wlassistant libflac++5c2 gambas-gb-compress vcdimager
  openoffice.org-kde libglib-java-gcj libmagick++9c2a adept-installer
  libkexif1 gwenview libsmokeqt1 libmp4v2-0 adept-updater python-pymad
  hwdb-client-kde krita liblog4j1.2-java kubuntu-artwork-usplash opera
  python-pyogg libsgutils1 libswt3.2-gtk-java adept-batch libseda-java
  libgtk-java-gcj libcommons-cli-java libgtk-jni libmono-cairo2.0-cil
  libqt-perl gambas-gb-net-curl pykdeextensions adept gambas-gb-qt-editor
  ksplash-engine-moodin kubuntu-konqueror-shortcuts python-pyvorbis skim
  kipi-plugins k3b libcairo-java kio-apt kwin-style-crystal
  gambas-gb-db-postgresql python-qt3 python-qt4 cfv libexif-dev libusb-dev
  libgphoto2-2-dev adept-common libmono-security2.0-cil libggi2 libbcprov-java
  gambas-gb-db-sqlite libmikmod2 python-sip4 libgii1 digikam libskim0
  bogofilter-bdb katapult libmono-sqlite2.0-cil kubuntu-docs bogofilter
  libglib-java kde-guidance python-pysqlite2 libifp4 libmono-system-web2.0-cil
  debtags libgii1-target-x libgsl0 apt-index-watcher libmono-sharpzip2.84-cil
  dpkg-dev libmono-corlib2.0-cil gtk2-engines-gtk-qt libipoddevice0
  rdiff-backup gnomeicu-common libsdl-mixer1.2 digikamimageplugins
  language-selector-qt qobex ktorrent gambas-gb-db-mysql scim-qtimm
  gambas-gb-net html2text libgtk-java python-elementtree gambas-gb-sdl keep
  libswt3.2-gtk-jni adept-notifier bogofilter-common libimlib2
  kde-guidance-powermanager alien kde-systemsettings libgtkglext1 liblame0
  librsync1 gambas-gb-debug gambas-gb-xml libnjb5 libmono-system2.0-cil
  kmplayer-base gambas-gb-db python-kde3 libfaac0 gambas-doc libsmpeg0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing opera (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 opera
Aborted (core dumped)
nobreakfast@nobreakfast:~$ 
-----------------------------------------------------------------------
Of course the package will not reinstall, so what now?
Thanks in advance for any help anyone ventures.

---

### Post by jiminycricket on 2007-04-21
You can try

sudo dpkg --force-remove-reinstreq --remove opera

---

### Post by BillyBudd on 2007-04-21
Thanks Jiminy.  That seems to have done the trick.  Now to research and find out how it did whatever it did.
I think I came at this Linux thing from the wrong direction by starting with an installation of Ubuntu.  All the nice bells, whistles, and graphics mask what's really going on, so if something goes wrong I'm helpless.   I have a feeling that the Linux system is a lot simpler than it appears, if one can get under the fancy stuff, but at the moment I'm barely treading water.  I should have started by learning via the command line in a terminal, like I learned starting with CP/M.    Perhaps I'll just start over.
Thanks again.

---

