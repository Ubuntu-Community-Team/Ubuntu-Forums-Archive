---
title: "Removing unwanted programs"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-09-10
I have the standard installation of Ubuntu and wished to try out KDE.  Mistakenly, I installed what I thought was KDE desktop but it turned out to be kde (the K desktop environment official modules) which installed many different programs all at once. 

Eventually I found and downloaded KDE desktop and all is well. I'm now trying to unistall the kde (the K desktop environment official modules) which I mistakenly installed, but when I've marked kde to uninstall, it runs through the process and removes some items, but the majority of the programs remain.  

Firstly, I don't understand why all the programs weren't removed at the same time, as they did when they were installed.

Secondly, Is it possible to remove all the unwanted programs in one bach process, or will I need to individually remove each one individualy using Synaptic manager?

---

### Post by xyz on 2006-09-10
Did you use sudo apt-get install  or sudo aptitude install  to install?

If so, run sudo aptitude remove whatever_you_typed_here_to_install

---

### Post by Irony on 2006-09-10
From [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Remove Kubuntu
Paste this command into the terminal:

[PHP]sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon bogofilter bogofilter-bdb bogofilter-common debtags enscript flac gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt latex-xft-fonts libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-core4 libavahi-qt3-1 libdaemon0 libdbus-qt-1-1c2 libflac++5c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmodplug0c2 libmpcdec3 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpythonize0 libqt-perl libqt3-mt librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a libxcomposite1 libxine-main1 libxvmc1 menu-xdg openoffice.org-kde perl-suid poster postfix procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant[/PHP]

---

### Post by a.v.l on 2006-09-10
> **Irony said:**
> From [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Remove Kubuntu
Paste this command into the terminal:

[PHP]sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon bogofilter bogofilter-bdb bogofilter-common debtags enscript flac gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt latex-xft-fonts libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-core4 libavahi-qt3-1 libdaemon0 libdbus-qt-1-1c2 libflac++5c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmodplug0c2 libmpcdec3 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpythonize0 libqt-perl libqt3-mt librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a libxcomposite1 libxine-main1 libxvmc1 menu-xdg openoffice.org-kde perl-suid poster postfix procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant[/PHP]

I'm unsure what happened when I used the above. After copying and pasting the above into the terminal, KDE seemed to remain in place, but with far less of the programs I had previously installed with kde.  Nothing then worked in KDE so I rebooted into Gnome. When in Gnome the icons I had on the desktop had changed their appearance and would no longer work.

At this point I re-installed KDE from the command line and it now seems to work fine again. One thing that confuses me is that the new installation of KDE has retained most of the setting I had on the previous installation I thought I had removed.

I may be talking a load of nonsense here, so I'll have to ask you to humour me whilst I learn about this new OS.

---

### Post by a.v.l on 2006-09-10
> **a.v.l said:**
> I'm unsure what happened when I used the above. After copying and pasting the above into the terminal, KDE seemed to remain in place, but with far less of the programs I had previously installed with kde.  Nothing then worked in KDE so I rebooted into Gnome. When in Gnome the icons I had on the desktop had changed their appearance and would no longer work.

At this point I re-installed KDE from the command line and it now seems to work fine again. One thing that confuses me is that the new installation of KDE has retained most of the setting I had on the previous installation I thought I had removed.

I may be talking a load of nonsense here, so I'll have to ask you to humour me whilst I learn about this new OS.

******************************************************

To add to my confusion, when I now close down KDE I see an XUBUNTU shutdown screen where it once was a KUBUNTU screen.  Then when I startup KDE, I again see the XUBUNTU screen whilst it loads.  Eventually it will open in a KDE logon screen.

This is getting more confusing by the minute, enjoyable, but confusing.  Can anyone explain what might be happening please?

---

### Post by Irony on 2006-09-11
I assume you pasted the command whilst booted into gnome not KDE.

---

### Post by a.v.l on 2006-09-11
> **Irony said:**
> I assume you pasted the command whilst booted into gnome not KDE.


Yes I did as you have said, did I do something wrong by doing that?

---

