---
title: "help--- I am completely new to ubuntu 7.04"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2007-05-10
hi
I finally got windows out :guitar: 

I tried Fubuntu 7.04 and loved it but it kept crashing,
now i got the ubuntu 7.04 and its different :lolflag: 

problem is: I have a KV2 Extreme Mobo with AMD64 3000+
                     Corsair 2Gb XMS Ram (V.soon to be 4Gb---y not:popcorn: )
                     ASUS v9999 6800 GT 256mg  (Nvidia AGP Card)
                     (I came across major problems installing 6800gt drivers and had to ReInstall O/S)
                     
How do I setup Ubuntu 7.04 to use what I have properly and maybe if its possible to give the desktop the custom options from kubuntu 7.04 or even making ubuntu 7.04 into kubuntu7.04(i like being able to change everything on my O/S)

Also to play Games like Battlefield1942, Call of duty2,  SimCity4 rush hour.... (which take a lot of power to run full spec in XP) 

Any help would be great as i haven't a clue YET how to use it.

NeoEIRE
:lolflag: ':guitar:  (1st day of freedom from the evil Microsoft Empire:mad: ):guitar: :lolflag:

---

### Post by rich.bradshaw on 2007-05-10
What exactly are you asking?

---

### Post by Cypher on 2007-05-10
Wow..all those icons are just distracting..

Anyway..to make Ubuntu use the KDE desktop, you'd do "sudo apt-get install kubuntu-desktop" and that will get you KDE in addition to the GNOME you already have.

To install the nVidia drivers, use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

Check out [Cadega]("http://cedega.com/") for gaming or you can always use [Wine]("http://winehq.com") for free.

---

### Post by NeoEIRE on 2007-05-10
hi thanks for the quick reply.
I tried Envy but the download like is messed up is there other programs? or I wait for that one.

and i done the sudo

and got this(hi-lited end in red...did it work?):
neoeire@neoeire-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adept adept-batch adept-installer adept-notifier adept-updater akregator
  amarok amarok-xine apport-qt arts bogofilter bogofilter-bdb
  bogofilter-common enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b
  kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate
  kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono
  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-data
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm
  kdnssd kexi kfind kghostview khelpcenter kicker kio-apt kio-locate
  kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool
  kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes
  koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins kontact
  konversation kooka kopete korganizer kpf kppp krdc krfb kscreensaver
  ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd
  ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin
  kwin-style-crystal language-selector-qt libakode2 libarts1-akode
  libavahi-compat-libdnssd1 libcurl3-gnutls libflac++5c2 libgmp3c2 libgpgme11
  libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2
  libkcal2b libkcddb1 libkdepim1a libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmeanwhile1
  libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5
  libofa0 liboggflac3 libopenobex1 libpoppler1-qt libpq5 libpulse0
  libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql
  libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtunepimp5
  libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde
  openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions
  python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex
  ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch
  vorbis-tools
Suggested packages:
  libvisual-0.4-plugins libqt0-ruby1.8 amarok-engines pax db4.4-util fftw3-dev
  k3b-i18n normalize-audio toolame sox movixmaker-2 libk3b2-mp3 kate-plugins
  egroupware efax hylafax-client mgetty-fax menu htdig kicker-applets gallery
  kipi-plugins-doc gnupg-agent pinentry-qt pinentry-x11 kleopatra clamav
  f-prot-installer koffice-doc-html wordnet tetex-extra kdeaddons-doc-html
  libgcj7-awt libjessie-java kpilot knewsticker kweather libsoap-lite-perl
  kdeartwork-emoticons php5-cli kpager gpgsm gsl-ref-psdoc gsl-doc-pdf
  gsl-ref-html pulseaudio libqt4-dev libxine1-plugins xine-ui gxine
  kde-icons-crystal crystalcursors cryptsetup gv python-kde3-dbg python-qt3-gl
  python-qt3-doc libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql python-qt3-dbg
  python-qt4-dbg python-sip4-dbg libc6-dev libc-dev ruby1.8-examples rdoc1.8
  ri1.8 scim-chewing scim-chinese scim-hangul scim-m17n scim-tables-additional
  scim-tables-ja scim-tables-ko scim-tables-zh scim-uim
Recommended packages:
  vcdimager kregexpeditor graphicsmagick-imagemagick-compat imagemagick
  sane-utils procmail openoffice.org-mimelnk latex-xft-fonts kitchensync knode
  ocrad gocr kscreensaver-xsavers kpersonalizer python-all-dev qt4-qtconfig
  libxine1-ffmpeg python-elementtree
The following NEW packages will be installed
  adept adept-batch adept-installer adept-notifier adept-updater akregator
  amarok amarok-xine apport-qt arts bogofilter bogofilter-bdb
  bogofilter-common enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b
  kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate
  kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono
  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-data
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm
  kdnssd kexi kfind kghostview khelpcenter kicker kio-apt kio-locate
  kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool
  kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes
  koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins kontact
  konversation kooka kopete korganizer kpf kppp krdc krfb kscreensaver
  ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd
  ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin
  kwin-style-crystal language-selector-qt libakode2 libarts1-akode
  libavahi-compat-libdnssd1 libcurl3-gnutls libflac++5c2 libgmp3c2 libgpgme11
  libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2
  libkcal2b libkcddb1 libkdepim1a libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmeanwhile1
  libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5
  libofa0 liboggflac3 libopenobex1 libpoppler1-qt libpq5 libpulse0
  libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql
  libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtunepimp5
  libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde
  openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions
  python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex
  ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch
  vorbis-tools
[COLOR="Red"]0 upgraded, 178 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/COLOR]

and I'v got wine and automatrix2, just think its the nvidia issue lest

thanks for all your help with this...

anything not to got back to B.Gate Rapesoft:KS 
Neoeire

---

### Post by Cypher on 2007-05-10
No, the kubuntu installation didn't work. You must have Synaptic or something else running at the same time. Also, what exactly was the problem with the Envy download?

---

### Post by NeoEIRE on 2007-05-10
hi, let me retry your 1st answer as there was something still running or installing. and now is finished.. 1 moment

---

### Post by NeoEIRE on 2007-05-10
help......................................
it went badly wrong---- at least i think it did....

the kubuntu coverion went good, and the wine install and automatrix--- all good...

ran Envy, and program ran, installed new nvidia drivers and when it restart, it goes to a blank screen(black dos like) and thats it....
restart and the same happened....
I try to boot in recovery and guess at every comand i can think of and nothing......

I am now running the system online with LiveCD so.......

How do I undo the changes made by Envy or retry it to work or? something...
do I have to do a fresh boot? if not?

thanks
Neoeire

---

### Post by NeoEIRE on 2007-05-10
Can anyone be able to help Please
or am i best off reinstalling again?

thanks
neoeire

---

### Post by Cypher on 2007-05-10
That is very strange, as long as the NVidia drivers for the 6800 are OK you shouldn't have gotten that. When you had it initially working before installing the nVidia drivers, were there any problems with the video card?

I'm sure there should be a way of removing the drivers that Envy installed and allow you to return to whatever things were like before, but I'm at work without access to my Ubuntu machine at home.

if you don't have any important stuff in Ubuntu yet, by all means re-install it and we can go from there..

---

### Post by tommcd on 2007-05-10
For the nvidia drivers you don't need the driver from nvidia, the one in the ubuntu repositories will work fine.
To enable extra repositories in synaptic:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
For nvidia driver, use the 7.04 method here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
If that doesn't work follow this:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
The short answer from the above link:
sudo apt-get install linux-generic
sudo apt-get install nvidia-glx-new
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup  (to be safe!)
sudo nvidia-xconfig
Reboot. Hope this helps.

---

### Post by NeoEIRE on 2007-05-11
hi all Im back from da hell of rebooting again...

I sorted the problem with nvidia 6800 with a fresh reinstall and install envy and try again, but this time it work perfect....

I found a sign in screen which lets you choose which (K)ubuntu you want to run after the sudo kubuntu-desktop command thing to activate the KDE stuff. so... that was all fine

until I logged into the KDE desktop and went online, after 10min or so i lost connection and wasn't able to get it back even on the Gnome ubuntu. so i tested to see if i still have the internet with the liveCD and had no problem getting my email and surfin....

so to end it i just reinstalled again and going to try again all agin....

if it goes wrong again, keep an eye out for this as i'll be looking for help on LiveCD mode...

thanks to all who have helped and gave advice...... sorry I'm a Noob on this....lol
neoeire

**On a side note:-**  I usual overclocked my xp system(not over the top, hardware is all fine and working---tested in xp pro 64bit-10thMay07) to play games a top graphics and effects.

Whats? the story about fubuntu running hi-end games cause even after the nvidia driver was sorted the o/s still seamed sluggish or laggy with 3d stuff or affects....?? and i havn't tried battlefield(2)(1942)(other modded BF games), Call of Duty 2, SimCity4 Rhr, WarCraft too.

Some of the games i want to run at max...

hardware:
ECS KV2 Extreme Mobo
2Gb corsair XMS ram DDR400 (soon to be 4Gb-any Problems?)
AMD64 3000+
ASUS Nvidia 6800 gt 256mb
creative Audgy 7.1  Sound Card.

thanks all:guitar:

---

