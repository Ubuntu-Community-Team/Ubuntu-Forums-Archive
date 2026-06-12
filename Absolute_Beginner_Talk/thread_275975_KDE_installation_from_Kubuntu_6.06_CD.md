---
title: "KDE installation from Kubuntu 6.06 CD"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Eugene RIMMER on 2006-10-12
Hi everyone!

I hope somebody heps me. I was watching the Ubuntu development since v.5.10. At that time there was no ShipIt for Kubuntu. When Ubuntu 6.06 was out, I ordered a CD WITHOUT EVEN LOOKING AT KUBUNTU, which was also available through ShipIt. I've installed GNOME-based Ubuntu, tweaked and pimped it throughout - now it's my main desktop OS. But alas: my friend gave me a Kubuntu 6.06 CD which he got through ShipIt (OMG!). I was crying out loud, when I tried it - even a liveCD was running pretty fast on my machine.

Now (no matter why) I want to have KDE. I know, that I'm just to apt-get install kubuntu-desktop, but I'm not ready to download all those 139 megs of that great stuff - I'm on dialup :( There was an advice to add the CD as repository and install kubuntu-desktop from there, but that was actual for 5.10 (Kubuntu 6.06 CD contains a very small amount of debs, not enough to install KDE).

So, is there any way to install KDE from Kubuntu CD onto my working Dapper?

---

### Post by jorn on 2006-10-12
I'm not sure of this. Have you tried to insert the Kubuntu cd while running your Ubuntu.
Open packetmanager >Edit>Add cdrom.
Find Kubuntu-desktop and install. I havn't tried it myself.

---

### Post by Eugene RIMMER on 2006-10-12
No, jorn, it won't work. I tried, apt-get connects to *.ubuntu.com all the time after hitting the CD once.

---

### Post by jorn on 2006-10-12
What about asking your friend to download the needed packages for you?

---

### Post by Eugene RIMMER on 2006-10-12
I repeat, he got the CD through ShipIt. He doesn't have a broadband either. (Funny, but he works at broadband provider - and doesn't even have a dialup at home).
Also, there's a whole bunch of packages, not just one. I'd download it if I could get a list of URL where to get this all.

---

### Post by meborc on 2006-10-12
it is not too late to order 6.10 dapper kubuntu from shipit... i know it must seem like a long time, but i bet the cd's will be there in 3-4 weeks...

OR if you happen to drop by estonia (don't know what part of russia do you come from) i can burn you a cd :)

---

### Post by mips on 2006-10-12
> **Eugene RIMMER said:**
> But alas: my friend gave me a Kubuntu 6.06 CD which he got through ShipIt (OMG!). I was crying out loud, when I tried it - even a liveCD was running pretty fast on my machine.


So do you still have the CD or can you borrow it again ???

If 'yes' then you can install Kubuntu from the Desktop/Live-CD or you could simply install the KDE part from the cd.

---

### Post by mips on 2006-10-12
> **Eugene RIMMER said:**
> No, jorn, it won't work. I tried, apt-get connects to *.ubuntu.com all the time after hitting the CD once.

Have you hashed out all the lines EXCEPT the cd-rom ? Or backup your sources list and create a new one with only the following line in it:

Kubuntu 6.06 CD
```
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
```Kubuntu 6.06.1 CD
```
deb cdrom:[Kubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
```

Remember to do an update before you install.

---

### Post by Eugene RIMMER on 2006-10-12
Thank you, meborc, but I now hold the CD in my hands. I told, my friend just gave it to me (as he's having his linux installed and running fine - it's not M$ Window$ to keep the precious installation CD as long as your system tries to work). My problem is how to scratch KDE out of there and put it onto my working Ubuntu.

mips, so there's a way? I've looked through the Kubuntu CD right now - there are only 35 debs not related to kde. All other stuff seems to be hidden somewhere (there's a huge 'filesystem.squashfs' file, may it be there?) And if I install from liveCD session - it might erase my whole current system with already running wine and beryl. I cannot afford downloading it all again, the only way for me is to install KDE to my current system - or forget it. I'll try now to hash all other repos, maybe this'll work...

/edit/ Ok, tried disabling other repositories. There's no packages for KDE on Kubuntu 6.06 CD (Synaptics returns only 'ubuntu-artwork' on 'kubuntu' search). I think, when we install the Dapper, it just copies the whole root filesystem to the selected partition. 
I mounted the squashfs file. It holds a normal root filesystem inside. And it seems to be a Kubuntu system which we get on liveCD session. And there's nothing as big as this FS on the CD. And nothing as big as 140 megs. So nowhere to install packages from. So, just a filesystem tree copying on install...

---

### Post by TheWizzard on 2006-10-12
i checked my kubuntu 6.06 CD. indeed no deb files!?!

if you run the kubuntu installer, doesn't give it an option just to install kde? not that i tried though. 

i'm affraid you have to get yourself the required collection of deb files. the nasty thing is you have to make sure you get all the dependencies...
do you have acces to internet somewhere? maybe write a nice email to the ubuntu-team. 

hope this helps.

btw how did you install wine?

---

### Post by Eugene RIMMER on 2006-10-13
Wine? Just checked it in Synaptics and downloaded those 9 MBs, that took about 1 night of 56k dial-up, just that simple.

---

### Post by TheWizzard on 2006-10-13
> **Eugene RIMMER said:**
> Wine? Just checked it in Synaptics and downloaded those 9 MBs, that took about 1 night of 56k dial-up, just that simple.

ok. so you have internet acces. 
is it an option to check kubuntu-desktop in synaptic? this is the standard way to install kde over ubuntu. 
synaptic can provide you with a full list of the needed deb files so you can download kubuntu in bits & pieces. 

hope this helps

---

### Post by meborc on 2006-10-13
> **TheWizzard said:**
> ok. so you have internet acces. 
is it an option to check kubuntu-desktop in synaptic? this is the standard way to install kde over ubuntu. 
synaptic can provide you with a full list of the needed deb files so you can download kubuntu in bits & pieces. 

hope this helps

it will take him all week to download all the pieces... i run edgy and if i wanted to install kubuntu-desktop, i would need those packages:
> adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apt-index-watcher ark arts bogofilter
  bogofilter-bdb bogofilter-common dcraw debtags digikam enscript gtk2-engines-gtk-qt gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm
  katapult kate kaudiocreator kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-systemsettings kdeadmin-kfile-plugins kdebase-bin
  kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview
  khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf
  knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita
  krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2
  libarts1-akode libarts1c2a libavahi-compat-libdnssd1 libavahi-qt3-1 libdbus-qt-1-1c2 libexif-dev libflac++5c2 libgpgme11 libgphoto2-2-dev libgsl0 libifp4
  libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1
  libkscan1 libksieve0 libktnef1 liblockdev1 libmagick++9c2a libmimelib1c2a libnss-mdns libopenexr2c2a libpoppler1-qt libpythonize0 libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libtdb1 libtunepimp3 libxcomposite1 openoffice.org-kde openoffice.org-style-crystal
  perl-suid poster psutils pykdeextensions python-elementtree python-kde3 python-qt3 python-qt4 python-sip4 python2.4-dev qca-tls qobex rdiff-backup ruby ruby1.8
  scim-qtimm skim speedcrunch wlassistant =138MB

if i only wanted kde:
> akregator amor ark arts artsbuilder atlantik atlantikdesigner blinken comerr-dev cvs dcoprss dirmngr edict enscript eyesapplet fifteenapplet gettext-kde
  gnupg-agent gnupg2 gpgsm hspell juk kaboodle kaddressbook kaddressbook-plugins kalarm kalzium kalzium-data kamera kanagram kandy kanjidic kappfinder karm
  kasteroids kate kate-plugins katomic kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc kcharselect kcoloredit kcontrol kcron kdat kde
  kde-amusements kde-core kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc
  kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase kdebase-bin kdebase-data kdebase-kio-plugins kdeedu kdeedu-data kdegames kdegames-card-data
  kdegraphics kdegraphics-kfile-plugins kdelibs kdelibs-data kdelibs4-dev kdelibs4c2a kdelirc kdemultimedia kdemultimedia-dev kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins
  kdepim-kresources kdepim-wizards kdeprint kdesdk-scripts kdesktop kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict kdnssd kdvi kedit keduca kenolaba kfax
  kfaxview kfilereplace kfind kfloppy kfouleggs kgamma kget kghostview kgoldrunner kgpg khangman khelpcenter khexedit kicker kicker-applets kiconedit kig
  kimagemapeditor kitchensync kiten kjots kjumpingcube klaptopdaemon klatin kleopatra klettres klettres-data klickety klines klinkstatus klipper kmag kmahjongg kmail
  kmailcvt kmenuedit kmid kmilo kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf knewsticker knewsticker-scripts knode knotes kodo kolf
  kolourpaint kommander konq-plugins konqueror konqueror-nsplugins konquest konsole konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpat kpdf
  kpercentage kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers
  kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash kstars kstars-data ksvg ksync ksysguard ksysguardd ksysv kteatime
  ktimer ktip ktnef ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin kwin4 kwordquiz
  kworldclock kxsldbg libacl1-dev libakode2 libart-2.0-dev libarts1-akode libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine libarts1c2a libartsc0-dev
  libasound2-dev libaspell-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 libavahi-qt3-1
  libavahi-qt3-dev libboost-python1.33.1 libbz2-dev libconvert-binhex-perl libcupsys2-dev libcvsservice0 libdb4.3++c2 libdbus-1-dev libdbus-qt-1-1c2 libesd0-dev
  libfinance-quote-perl libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libgpgme11 libhtml-tableextract-perl libidn11-dev libindex0
  libio-stringy-perl libjasper-1.701-dev libjasper-runtime libjpeg-progs libjpeg62-dev libkadm55 libkcal2b libkcddb1 libkdeedu3 libkdegames1 libkdepim1a libkgantt0
  libkiten1 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkrb5-dev libksba8 libkscan1 libksieve0 libktnef1 liblcms1-dev liblockdev1
  liblua50-dev liblualib50-dev liblzo-dev libmailtools-perl libmal1 libmime-perl libmimelib1c2a libmng-dev libnews-nntpclient-perl libnss-mdns libogg-dev
  libopencdk8-dev libopenexr-dev libopenexr2c2a libpcre3-dev libpcrecpp0 libpoppler1-qt libpopt-dev libpth20 libqt3-headers libqt3-mt-dev librss1 libsamplerate0
  libsasl2-dev libssl-dev libtasn1-3-dev libtidy-0.99-0 libtiff-tools libtiff4-dev libtiffxx0c2 libtimedate-perl libtunepimp-bin libtunepimp3 libvorbis-dev
  libxcomposite1 libxml2-dev libxslt1-dev lskat lua50 mesa-common-dev mpeglib networkstatus noatun noatun-plugins pinentry-qt poster psutils qt3-dev-tools quanta
  quanta-data secpolicy superkaramba tidy ttf-sjfonts
=205MB

...interesting ;)

---

### Post by TheWizzard on 2006-10-14
yes, this would be more then two nights of downloading.
eugene, do have acces to broadband internet somewhere? work or internet cafe? 
you can use synaptic to make a list like meborc did and write a (ms-dos) script to download the list.

---

### Post by Ptero-4 on 2006-12-15
Hey. for the guy that asked why the livecd doesn't have the packages the answer is this. Ubuntu (all of it's flavors) come in two types of CD's. Desktop and alternate. The desktop CD is the one you get on shipit, it's a combo LiveCD/installer, this CD contains a imaged install instead of the usual installtion stuff, that's why it doesn't show up in aptitude. The alternate CD is the one that works like the 5.10 and earlier install CD's and is the one you need if you want to use the cd as a repository.

---

