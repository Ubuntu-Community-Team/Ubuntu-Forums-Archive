---
title: "aptitude wants to remove 110 programs"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-03
```
sudo aptitude install lineak
<yadda yadda>
Couldn't find package "lineak".  However, the following
packages contain "lineak" in their name:
  lineak-kdeplugins klineakconfig liblineak-dev liblineak0
  lineak-xosdplugin lineak-defaultplugin lineakd
The following packages are unused and will be REMOVED:
  adept akregator amarok amarok-xine ark artsbuilder debtags flac
  gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm katapult
  kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings
  kdeadmin-kfile-plugins kdegraphics-kfile-plugins
  kdemultimedia-kfile-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdnssd keep kio-apt kio-locate kitchensync klaptopdaemon
  kmail kmailcvt kmilo kmix knetworkconf knotes koffice-data koffice-libs
  konq-plugins kontact konversation kooka kopete korganizer kpdf kpf kppp
  krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers
  ksnapshot ksplash-engine-moodin ksvg ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libflac++5c2 libgadu3 libjpeg-progs libk3b2 libkipi0 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 liblockdev1 libmimelib1c2a
  libpoppler1-qt libpythonize0 librsync1 libruby1.8 libsamplerate0 libskim0
  libtdb1 libtunepimp2c2a openoffice.org-kde procmail pykdeextensions
  python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3
  qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch
  vorbis-tools wlassistant
The following packages have been kept back:
  apache apache-common apache2-utils gedit gedit-common gnome-about
  gnome-desktop-data gnome-games gnome-games-data gnome-panel
  gnome-panel-data libgnome-desktop-2 libgnomeui-0 libgnomeui-common
  libgtksourceview-common libgtksourceview1.0-0 libpanel-applet2-0
  linux-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common openoffice.org-evolution zenity
0 packages upgraded, 0 newly installed, 110 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 314MB will be freed.
Do you want to continue? [Y/n/?]  
```

Some of these programs I've never used (speedcrunch) some I can't use (klaptopdaemon--I'm on a PC) and some I've never heard of, but I live off kmail and kppd.

The kept back packages are updates I've decided not to update.

Why would aptitiude want to remove any of these programs? It reminds me of XP saying "You haven't clicked this icon for a while so I'm going to remove it."

---

### Post by Metacarpal on 2006-08-03
Um, quite a lot of those are pretty much necessary if you're using KDE / Kubuntu.  If that's your desktop, you do not want to remove those.  Don't know why it's doing that, though.  Maybe connected to asking it to install a package that doesn't exist?  It might think it needs to remove all of your dependencies...

---

### Post by editrix on 2006-08-06
Well, it's down to 108 today, but it still means I can't install anything. I dont think it's because the programs don't exist. Today I tried it with alien. I got the 108 removals, and it didn't tell me it's already installed.

---

### Post by Metacarpal on 2006-08-06
> **editrix said:**
> Well, it's down to 108 today, but it still means I can't install anything. I dont think it's because the programs don't exist. Today I tried it with alien. I got the 108 removals, and it didn't tell me it's already installed.

Question:

Do you have both Ubuntu and Kubuntu (both Gnome and KDE desktops) on your machine?  If so, which did you install first, and what method did you use to install the second?

---

### Post by editrix on 2006-08-07
> **Metacarpal said:**
> Question:

Do you have both Ubuntu and Kubuntu (both Gnome and KDE desktops) on your machine?  If so, which did you install first, and what method did you use to install the second?

Installed Gnome first, but as it turns out, that's not the problem. I did some intensive googling and found *one* other person with this problem, and the answer is: Synaptic and Aptitude don't play nice with each other. Apt & Synaptic are friends, they talk to each other, but Aptitude doesn't talk to Synaptic, so it doesn't know what Synaptic's done.

> Maybe you have installed packages with synaptic -- synaptic installs additional "recommended" dependencies, just like aptitude, but aptitude doesn't know what you've installed with synaptic and so it thinks that you don't need any more the packages that synaptic has installed as "recommended" dependencies.
[http://www.linuxquestions.org/questions/showthread.php?t=330616](http://www.linuxquestions.org/questions/showthread.php?t=330616)

Sheesh! You'd think it would be a more common problem than 2 people.

---

### Post by Metacarpal on 2006-08-07
Weird.  Thanks for posting the solution to this!  Maybe a third person will run into this and it'll help.

---

### Post by opticyclic on 2006-08-07
It certainly has!
Thanks for posting your solution!

---

### Post by yopnono on 2006-08-08
I used to have this, it wanted to remove more and less everything when using aptitude. 
So I just totally removed the aptitude from synaptic and reinstalled it. And now it don't want to remove everything on my computer.

---

### Post by trippinnik on 2007-05-01
I'm having a somewhat similar problem.  I've upgraded to Feisty and use Amarok for playing music.  I like to do upgrades and install packages i know the name of in aptitude, because it will clear out unused dependecies when i unistall anyting later.. but even to upgrade now it wants to removed amarok because it's unused...  I guess I'll try unistalling/reinstalling aptitude...

---

### Post by mcduck on 2007-05-01
Just use apt-get or synaptic instead. Since apt-get got the autoremove feature aptitude has no benefits over apt-get, and as aptitude can get a bit confused sometimes (like yours now) I'd rather recommend forgetting about it :)

---

### Post by JBull on 2007-08-27
I'm getting the same problem too.
```
# aptitude install camorama
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  abiword-common abiword-gnome bug-buddy dia-common dia-gnome dia-libs ekiga eog esound fast-user-switch-applet
  file-roller gcalctool gconf-editor gdm gdm-themes gnome-backgrounds gnome-cards-data gnome-core gnome-cups-manager
  gnome-games gnome-games-data gnome-games-extra-data gnome-keyring-manager gnome-office gnome-system-tools gnome-themes
  gnome-themes-extras gnome-utils gnome-volume-manager gnumeric gnumeric-common gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-ugly gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-spherecrystal gucharmap
  industrial-cursor-theme inkscape libcairo-perl libdmx1 libgda2-3 libgda2-common libglib-perl libgnome2-canvas-perl
  libgnome2-perl libgnome2-vfs-perl libgnomecupsui1.0-1c2a libgoffice-1-2 libgpod0 libgsf-gnome-1-114 libgtk2-perl
  libgtkmm-2.4-1c2a libopal-2.2.0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libsidplay1 planner rhythmbox
  sound-juicer synaptic system-tools-backends totem totem-mozilla totem-xine vino
The following packages have been kept back:
  apache2-doc apache2-mpm-prefork apache2-utils apache2.2-common debian-archive-keyring desktop-base epiphany-browser
  file gimp gimp-data iceape-browser iceape-gnome-support initramfs-tools libexif12 libfreetype6 libfreetype6-dev
  libgadu3 libgimp2.0 libkrb5-17-heimdal libmagic1 libmozjs0d libneon26 libnspr4-0d libnss3-0d liborbit2 libpq4
  libsmbclient libxul-common libxul0d linux-image-2.6-686 lsb-base mozilla-browser mutt nano nfs-common
  openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-writer php-pear php5-common
  pppconfig python-uno rdesktop samba samba-common smbclient ttf-opensymbol winbind x11-common xlibmesa-gl xlibmesa-glu
  xlibs-static-dev xorg xserver-xfree86 xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
  xulrunner-gnome-support
0 packages upgraded, 0 newly installed, 68 to remove and 64 not upgraded.
Need to get 0B of archives. After unpacking 294MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```
This is the second time this has happened to me.  The first time was several months ago and I answered yes.  Bad move.  It really did uninstall gnome completely.

I usually use either apt-get or Synaptic.  Occasionally use aptitude because it really is smarter about certain things.  No more aptitude for me.

---

### Post by capink on 2007-08-27
The solution to this is to type:

```
sudo aptitude keep-all
```

---

