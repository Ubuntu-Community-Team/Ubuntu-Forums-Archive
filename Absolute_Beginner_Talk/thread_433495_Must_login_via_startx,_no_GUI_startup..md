---
title: "Must login via startx, no GUI startup."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-05-05
There must be a hundred posts on this, but none of them match my problem. Despite my time, I know this has to be a noob question.

When I bootup, im kicked to a command prompt, and i must open my DE using startx. This of course doesnt allow me to choose fluxbox, although im sure I could do it via prompt.

Ive tried to create a inittab file in /etc with the id:2:initdefault: command in it, as I was told upstart looks for the inittab file on bootup, but this doesnt work.

When I put in 

sudo aptitude install kdm

I get the following message:

poeticrpm@poeticrpm-laptop:~$ sudo aptitude install kdm
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  adept adept-batch adept-installer adept-notifier adept-updater akregator
  amarok amarok-xine apport-qt ark bogofilter bogofilter-bdb
  bogofilter-common dhcdbd digikam digikamimageplugins exiv2 fftw3
  gtk-qt-engine gwenview hwdb-client-kde imagemagick k3b kaddressbook
  kaffeine kaffeine-xine karm katapult kbstate kcron kde-guidance
  kde-guidance-powermanager kde-icons-mono kde-style-polyester
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kio-plugins
  kdepim-kresources kdepim-wizards kdnssd keep kexi kio-apt kio-locate
  kipi-plugins kitchensync kmag kmilo kmix kmousetool knetworkconf
  knetworkmanager knode knotes koffice-data koffice-libs konq-plugins
  konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver
  kscreensaver-xsavers ksnapshot ksplash-engine-moodin ksvg ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libcurl3-gnutls libexiv2-0.12
  libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libifp4 libimlib2 libiso9660-4
  libjasper-runtime libk3b2 libkcal2b libkdepim1a libkexiv2-0 libkipi0
  libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmtp5
  libmysqlclient15off libnjb5 libnl1-pre6 libnm-util0 libofa0 libopenobex1
  libpoppler1-qt libpq5 libpythonize0 libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libskim0 libsqlite0
  libtunepimp5 libvcdinfo0 mysql-common ncompress network-manager
  networkstatus ocrad openoffice.org-kde p7zip-full procmail
  pykdeextensions python-all python-all-dev python-dev python-elementtree
  python-kde3 python-qt4 python2.4-dev python2.5-dev qca-tls qobex
  qt4-qtconfig rdiff-backup ruby ruby1.8 scim-qtimm skim
  software-properties-kde speedcrunch vcdimager vorbis-tools zoo
The following packages have been kept back:
  planetpenguin-racer
0 packages upgraded, 0 newly installed, 160 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 423MB will be freed.
Do you want to continue? [Y/n/?] n

Whats worse, no matter what I try to install via aptitude or apt-get, I get this message telling me that its going to remove all this stuff. Correct me if im wrong... but Id essentailly be uninstalling Kubuntu and be left with KDE core.

So, what do I do to get back to a graphical login, and get back apt-get/aptitude without uninstalling my whole desktop?

Thanks for any help...

---

### Post by aysiu on 2007-05-05
Are you sure *apt-get* also wants to remove everything? As I recall, *apt-get* will tell you certain packages are unused, but it won't automatically remove them unless you use the *autoremove* function.

Try this: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo /etc/init.d/kdm restart
``` *kubuntu-desktop* includes *kdm*.

---

### Post by GSF1200S on 2007-05-05
> **aysiu said:**
> Are you sure *apt-get* also wants to remove everything? As I recall, *apt-get* will tell you certain packages are unused, but it won't automatically remove them unless you use the *autoremove* function.

Try this: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo /etc/init.d/kdm restart
``` *kubuntu-desktop* includes *kdm*.

Well, this took care of my apt-get/aptitude problem (you are right, apt-get just informed me of unused packages where aptitude wanted to uninstall). Thanks!

After doing those commands, though, Im still pushed to a command prompt and must use startx to get to the desktop... Any other ideas on this?

---

### Post by aysiu on 2007-05-05
Maybe try the reverse of [this](http://ubuntuforums.org/showpost.php?p=866500&postcount=3)?

---

