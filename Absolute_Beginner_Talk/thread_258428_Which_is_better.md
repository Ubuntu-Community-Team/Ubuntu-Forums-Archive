---
title: "Which is better??"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by grimx on 2006-09-15
I have Gnome installed on Ubuntu 5.04.
Which would be better Gnome or KDE??

---

### Post by kidders on 2006-09-15
That part is entirely up to you :-) Personally, I can't stand Gnome, but don't let that influence you ...

My advice is to carry on playing with Gnome for a few days, and then install KDE ... see what you think. It's the same but different hehe.

---

### Post by nudnik on 2006-09-15
> I have Gnome installed on Ubuntu 5.04.
Which would be better Gnome or KDE??

In my opinion, Gnome is more stable than KDE, particularly with Ubuntu. Of course I haven't experimented with KDE in a few months, so it is possible they have ironed out some the issues. 

](*,) <<The Ubuntu Mascot :biggrin:

---

### Post by kidders on 2006-09-15
No, you're right ... KDE can do some odd things from time to time!

---

### Post by Russty of Oz on 2006-09-15
I have them installed together so I can change whenever I feel like something different.  I actually prefer to look and feel of KDE, but as I have found, it is worth having both just in case something  goes wrong with one, like I had the other day when I installed a new theme in gnome and it wouldn't start properly again, so I then restarted and selected KDE so I could fix the problem.  

So install the Ubuntu desktop from the Live CD then after you have it up and running, go to the following link and you will have KDE installed in no time. 

[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

Russty.

---

### Post by bt224 on 2006-09-15
How do you switch between the 2, and will it save your settings on Gnome?

---

### Post by jordanmthomas on 2006-09-15
After you install KDE, press F10 on your GDM (login) screen.  Go to Session, and KDE will be an option.

Nothing will happen to your Gnome settings, and you can switch back whenever you want at the login screen.

---

### Post by bt224 on 2006-09-15
Thanks, Jordan, I'll give it a try.

---

### Post by Drakkor on 2006-09-16
Tried the psycocats page and got this:

drakkor@drakkor:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 6B in 1s (3B/s)
Reading package lists... Done
drakkor@drakkor:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libpoppler1-qt
The following NEW packages will be automatically installed:
  adept akregator arj ark arts artsbuilder avahi-daemon bogofilter
  bogofilter-bdb bogofilter-common dcraw debtags enscript
  gtk2-engines-gtk-qt gwenview kaddressbook kaffeine kaffeine-xine kamera
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint
  kdesktop kdm kdnssd keep kfind kghostview khelpcenter kio-apt kio-locate
  kipi-plugins kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit
  kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes
  koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins
  kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp
  krdc kregexpeditor krfb krita krita-data kscd kscreensaver
  kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin
  ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts
  kwalletmanager kwin kwin-style-crystal language-selector-qt
  latex-xft-fonts libakode2 libarts1-akode libavahi-core4 libdaemon0
  libgadu3 libgpgme11 libgsl0 libjpeg-progs libkcal2b libkcddb1 libkdepim1a
  libkexif1 libkipi0 libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1
  libmimelib1c2a libnss-mdns libpythonize0 libqt-perl librsync1
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 ncompress ocrad
  openoffice.org-kde perl-suid poster postfix procmail psutils
  pykdeextensions python-kde3 python2.4-dev python2.4-kde3 qca-tls qobex
  rdiff-backup resolvconf sane-utils scim-qtimm skim speedcrunch ssl-cert
  wlassistant zoo
The following NEW packages will be installed:
  adept akregator arj ark arts artsbuilder avahi-daemon bogofilter
  bogofilter-bdb bogofilter-common dcraw debtags enscript
  gtk2-engines-gtk-qt gwenview kaddressbook kaffeine kaffeine-xine kamera
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint
  kdesktop kdm kdnssd keep kfind kghostview khelpcenter kio-apt kio-locate
  kipi-plugins kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit
  kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes
  koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins
  kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp
  krdc kregexpeditor krfb krita krita-data kscd kscreensaver
  kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin
  ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libavahi-core4 libdaemon0 libgadu3 libgpgme11 libgsl0 libjpeg-progs
  libkcal2b libkcddb1 libkdepim1a libkexif1 libkipi0 libkleopatra1
  libkmime2 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 liblockdev1 libmimelib1c2a libnss-mdns libpythonize0 libqt-perl
  librsync1 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1
  ncompress ocrad openoffice.org-kde perl-suid poster postfix procmail
  psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 qca-tls
  qobex rdiff-backup resolvconf sane-utils scim-qtimm skim speedcrunch
  ssl-cert wlassistant zoo
0 packages upgraded, 159 newly installed, 0 to remove and 0 not upgraded.
Need to get 95.3MB/110MB of archives. After unpacking 350MB will be used.
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

Accept this solution? [Y/n/q/?]

:confused:

---

### Post by Christopher Cook on 2006-09-16
I like Gnome, it's stable, and the loading is faster. It's like comparing window$ 98 to xp, with all the good things, but visuals in 98.

---

### Post by jordanmthomas on 2006-09-16
Drakkor, I use this to get the latest KDE.
```
# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

```
Slap that in sources.list and then type this:
```
 gpg --keyserver subkeys.pgp.net --recv DD4D5088
 gpg --export --armorDD4D5088  | sudo apt-key add -
sudo apt-get update
sudo apt-get install kubuntu-desktop

```

See if that will make your packages not break.  Mine didn't when I installed KDE.

**edit**
The site that was linked to earlier also shows those errors, so chances are it's fine to go ahead and install.

---

### Post by Russty of Oz on 2006-09-16
Drakkor, just type Y to the question.  

Russty.

---

