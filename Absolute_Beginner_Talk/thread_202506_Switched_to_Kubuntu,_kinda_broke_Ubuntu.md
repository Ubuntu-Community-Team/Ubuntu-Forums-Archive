---
title: "Switched to Kubuntu, kinda broke Ubuntu"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by morganpatrick on 2006-06-23
Ok,

So I installed Dapper Drake on a new hard drive, partitioned it into /boot, swap, / (root) and /home.

So I installed some stuff, got my particulars, and then I thought I'd check out KDE. So I installed KDE desktop.

Then I decided I didn't like KDE. So I found a site on google with a script to remove KDE...

only the same page had a script to remove Gnome, and I copied the wrong script. So I'm looking at the list of things being deleted in my terminal, and I realized, "oh no I need that!  Oh no I need that too!" and then I realized what I had done and I closed the terminal.

So anyway I tried to reinstall Gnome Deskop but it didn't really fix anything. all it did was allow a gnome session in Kubuntu. I don't want to be in Kubuntu. But now I'm stuck with Kubuntu because I deleted so much of my Ubuntu.

So the question is this: How do I restore my Ubuntu and nix my Kubuntu?

---

### Post by bruce89 on 2006-06-23
To install GNOME
```
sudo aptitude install ubuntu-desktop
```
To remove KDE
[QUOTE=http://psychocats.net/ubuntu/puregnome.php]```
sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon bogofilter bogofilter-bdb bogofilter-common debtags enscript flac gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt latex-xft-fonts libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-core4 libavahi-qt3-1 libdaemon0 libdbus-qt-1-1c2 libflac++5c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmodplug0c2 libmpcdec3 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpythonize0 libqt-perl libqt3-mt librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a libxcomposite1 libxine-main1 libxvmc1 menu-xdg openoffice.org-kde perl-suid poster postfix procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant
```[/QUOTE]

---

### Post by morganpatrick on 2006-06-23
aha. so I think i just installed gnome-desktop. ubuntu-desktop will resore everything huh?

---

### Post by aysiu on 2006-06-23
*ubuntu-desktop* points to everything that would be in a default Ubuntu (Gnome) installation.

---

