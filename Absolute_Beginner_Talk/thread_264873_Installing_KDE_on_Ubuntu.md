---
title: "Installing KDE on Ubuntu"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-09-25
Is it as simple as an apt-get install <kdepackage>?  I don't want to reinstall kubuntu - I have enough work into this install to have it where I want it.  After it is installed, how to have it start KDE instead of gnome when Linux starts?

---

### Post by deadgobby on 2006-09-25
Very easy and not painful at all
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by Danni on 2006-09-25
You could just type in sudo apt-get install kubuntu-desktop.

This will install KDE without changing your ubuntu installation. At startup you are able to choose between KDE and Gnome, and can set KDE as default if you wish.

---

### Post by Arisna on 2006-09-25
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

aptitude handles dependencies better than apt-get.  After installation, you'll be able to choose KDE from the graphical login (gdm/kdm) screen.

---

### Post by crokett on 2006-09-25
Cool.  sounds easy enough. I will work on that tonight

---

### Post by mostwanted on 2006-09-25
> **Arisna said:**
> ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

aptitude handles dependencies better than apt-get.  After installation, you'll be able to choose KDE from the graphical login (gdm/kdm) screen.

**Differently**, not **better**.

---

### Post by aysiu on 2006-09-25
In the case of desktop environments, it's definitely better. I don't see how you could think the inability to remove a desktop environment later is in any way "better" than the ability to do so.

Install with *aptitude*, there.
Remove with *aptitude*, not there any more.

Install with *apt-get*, there.
Remove with *apt-get*, still there.

---

### Post by Drakkor on 2006-09-25
Ok,did the aptitude thing.......
> This will install KDE without changing your ubuntu installation. At startup you are able to choose between KDE and Gnome, and can set KDE as default if you wish. How ?? :confused: 
Logged Out>Went to Select Session>Kubuntu is not there ! :(

---

### Post by coffeecat on 2006-09-25
> **Drakkor said:**
> Went to Select Session>Kubuntu is not there ! :(

But KDE will be.

---

### Post by aysiu on 2006-09-25
So you don't see this?

---

### Post by Drakkor on 2006-09-25
Nope,exactly the same except for 3. XGL

---

### Post by Drakkor on 2006-09-25
I don't know,maybe I didn't configure it properly on installation, I just OK'd all the default settings,and it installed. :confused:

---

### Post by Drakkor on 2006-09-25
*bump*

---

### Post by patslap on 2006-09-25
I tried the aptitude installation too, and went to login screen, but KDE does not appear. When installing I selected 'no configuration' option. Should I choose another option such as local install?

---

### Post by aysiu on 2006-09-25
I have no idea why it's not appearing in your sessions menu, but I think we can force it to.

Try this: ```
gksudo gedit /usr/share/xsessions/kde.desktop
``` Then paste this into the text file: ```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE
Name[hi]=&#2325;&#2375;&#2337;&#2368;&#2312;
Name[mn]=&#1050;&#1044;&#1069;
Name[ta]=K&#2959;±Í±•Í •¾µ²©Í
Name[xh]=iKDE
Name[xx]=xxKDExx
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
Comment[bs]=K Desktop Environment. Mo&#263;an grafi&#269;ki desktop otvorenog izvornog koda
Comment[ca]=L'entorn d'escriptori K. Un poderós entorn d'escriptori gràfic de Codi Font Obert
Comment[cy]=Yr Amgylchedd Penbwrdd K.  Amgylchedd penbwrdd graffegol pwerus, sy'n gôd-agored.
Comment[da]=K Skrivebordsmiljøet. Et kraftigt, åbent, grafisk skrivebordsmiljø
Comment[de]=Das K Desktop Environment. Eine mächtige, graphische Arbeitsumgebung und Open Source / Freie Software
Comment[el]=¤¿ K Desktop Environment. &#904;½± À±½¯ÃÇÅÁ¿ µ»µÍ¸µÁ·Â ÀÁ¿*»µÅÃ·Â ³Á±Æ¹ºÌ ÀµÁ¹²¬»»¿½ µÀ¹Æ¬½µ¹±Â µÁ³±Ã¯±Â
Comment[es]=El Entorno de Escritorio K, un potente entorno de escritorio gráfico realizado de código abierto
Comment[et]=K töölaua keskkond on võimas vaba tarkvara graafiline töölaua keskkond
Comment[fi]=KDE-työpöytäympäristö (K Desktop Environment) on tehokas avoimen lähdekoodin graafinen työpöytäympäristö
Comment[fr]=The K Desktop Environment. Un environnement de bureau graphique, puissant et Open Source
Comment[he]=The K Desktop Environment. áÑÙÑê âÑÕÓÔ ÒèäÙê, ÑâÜê-âÕæÞÔ ÑçÕÓ äêÕ×
Comment[hi]=&#2325;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;. &#2319;&#2325; &#2358;&#2325;&#2381;&#2340;&#2367;&#2358;&#2366;&#2354;&#2368;, &#2323;&#2346;&#2344; &#2360;&#2379;&#2352;&#2381;&#2360; &#2330;&#2367;&#2340;&#2381;&#2352;&#2350;&#2351; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;
Comment[hu]=A KDE grafikus munkakörnyezet, egy szabad forráskódú grafikus ablakkezel&#337; környezet
Comment[it]=L'ambiente desktop KDE. Un potente ambiente desktop grafico Open Source
Comment[mn]=The K Desktop Environment. &#1061;¯&#1095;&#1080;&#1088;&#1093;&#1101;&#1075; &#1085;&#1101;&#1101;&#1083;&#1090;&#1090;&#1101;&#1081; &#1101;&#1093; &#1082;&#1086;&#1076; &#1073;¯&#1093;&#1080;&#1081; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1076;&#1101;&#1083;&#1075;&#1101;&#1094;&#1080;&#1081;&#1085; &#1086;&#1088;&#1095;&#1080;&#1085;
Comment[nb]=K Desktop Environment. Et kraftig grafisk skrivebordsmiljø med åpen kildekode.
Comment[nl]=De K Desktop Environment, een krachtige open source grafische desktop environment
Comment[nn]=K Desktop Environment. Eit kraftig grafisk skrivebordsmiljø med open kjeldekode.
Comment[pl]=&#346;rodowisko KDE. Pot&#281;&#380;ne &#347;rodowisko graficzne Wolnego Oprogramowania.
Comment[pt]=O K Desktop Environment. Um ambiente gráfico open source poderoso
Comment[pt_BR]=Acrônimo para K Desktop Environment (ou Ambiente de Trabalho K). Um poderoso ambiente de trabalho gráfico de código aberto
Comment[ro]=K Desktop Environment. Un mediu grafic cu surse deschise, foarte puternic
Comment[sk]=The K Desktop Environment. Výkonné, vo&#318;ne &#353;írite&#318;né grafické pracovné prostredie
Comment[sl]=Namizno okolje K. Zmogljivo grafi&#269;no namizno okolje odprte kode
Comment[sr]=K Desktop Environment (KDE). &#1052;&#1086;&#1115;&#1085;&#1086; &#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1082;&#1086; &#1088;&#1072;&#1076;&#1085;&#1086; &#1086;&#1082;&#1088;&#1091;&#1078;&#1077;&#1114;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1086;&#1075; &#1082;&#1086;&#1076;&#1072;
Comment[sv]=K-skrivbordsmiljön. En kraftfull grafisk skrivbordsmiljö med öppen källkod
Comment[ta]= K®Ç²Í®ÇšÈ šÂ´²Í. š•Í¤¿µ¾¯Í¨Í¤ ¤¿±¨Í¤ &#2950;£È®Â² š¿¤Í¤¿° µ•È ®Ç²Í®ÇšÈ šÂ´²Í
Comment[tr]=KDE Masaüstü Yöneticisi. Güçlü bir grafiksel masaüstü ortam&#305;
Comment[uk]=The K Desktop Environment. &#1055;&#1086;&#1090;&#1091;&#1078;&#1085;&#1077; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1077; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1077; &#1079; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080;
Comment[uz]=KDE (K Desktop Environment) - &#1082;&#1091;&#1095;&#1083;&#1080; Open Source &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1080;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080; &#1084;&#1091;³&#1080;&#1090;&#1080;
Comment[vi]=môi tr°Ýng desktop K, môi tr°Ýng desktop &#273;Ó ho¡ mã nguÓn mß r¥t m¡nh
Comment[xx]=xxThe K Desktop Environment. A powerful Open Source graphical desktop environmentxx
Comment[zh_CN]=K &#26700;&#38754;¯&#22659;&#12290;&#24378;&#22823;&#30340;&#24320;&#25918;&#28304;&#20195;&#30721;&#22270;&#24418;&#26700;&#38754;&#29615;&#22659;
``` Save it and then log out. KDE should appear as a session.

---

### Post by patslap on 2006-09-25
that didn;t work. After typing ```
gksudo gedit /usr/share/xsessions/kde.desktop
```
I got
```
(gedit:6400): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

I pasted text into a the blank kde.desktop file, saved it, then logged out. In sesion select window on login screen I had a new option called 'foo'. I selected this but it came up with a long error message and booted into gnome instead.

---

### Post by aysiu on 2006-09-25
That warning's a [bug.](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917) You can ignore that.

I don't know why it appeared as *foo* instead of KDE. That's weird.

Can you post the output of these commands? ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
cd /usr/share/xsessions
ls
cat kde.desktop
``` I'm just wondering if there's some piece we lost along the way or if there were encoding issues with the text I had you copy and paste.

---

### Post by Drakkor on 2006-09-25
aysiu  , that text did have some wierd characters ! Anyways, I got the same
foo deal,and some kind of error about "/usr/bin/startkde" not found.

---

### Post by aysiu on 2006-09-25
Can you post the output of those commands?

---

### Post by Drakkor on 2006-09-25
Here's part of it ,the kde-desktop install seems screwed up !!

drakkor@drakkor:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
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
Fetched 6B in 1s (4B/s)
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
  adept akregator ark arts artsbuilder dcraw debtags gtk2-engines-gtk-qt
  gwenview kaffeine kaffeine-xine karm katapult kate kaudiocreator kcron
  kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt libakode2 libarts1-akode libgadu3 libkexif1 libkipi0
  libkpimexchange1 libkscan1 liblockdev1 libpythonize0 libqt-perl librsync1
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 ncompress ocrad
  openoffice.org-kde poster psutils pykdeextensions python-kde3
  python2.4-dev python2.4-kde3 qca-tls qobex rdiff-backup scim-qtimm skim
  speedcrunch wlassistant zoo
The following NEW packages will be installed:
  adept akregator ark arts artsbuilder dcraw debtags gtk2-engines-gtk-qt
  gwenview kaffeine kaffeine-xine karm katapult kate kaudiocreator kcron
  kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins
  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt libakode2 libarts1-akode libgadu3
  libkexif1 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libpythonize0
  libqt-perl librsync1 libsamplerate0 libsensors3 libskim0 libsmokeqt1
  libtdb1 ncompress ocrad openoffice.org-kde poster psutils pykdeextensions
  python-kde3 python2.4-dev python2.4-kde3 qca-tls qobex rdiff-backup
  scim-qtimm skim speedcrunch wlassistant zoo
0 packages upgraded, 120 newly installed, 0 to remove and 0 not upgraded.
Need to get 95.3MB of archives. After unpacking 301MB will be used.
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

---

### Post by patslap on 2006-09-25
Aysiu - here's the output of those commands:

sudo aptitude update
```
pat@pat-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://gb.archive.ubuntu.com dapper-updates Release
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Get:6 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Get:7 http://gb.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Get:8 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Get:9 http://gb.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
99% [9 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectingbzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages - open (2 No such file or directory)
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Get:10 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://archive.ubuntu.com dapper-updates/main Sources
Get:11 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:12 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
Get:13 http://security.ubuntu.com dapper-security/multiverse Packages [2185B]
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:14 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
99% [12 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
99% [13 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
99% [14 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:15 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:16 http://security.ubuntu.com dapper-security/multiverse Packages [2185B]
Hit http://security.ubuntu.com dapper-security/main Packages
99% [16 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Get:17 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:18 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
99% [18 Packages bzip2 0] [Waiting for headers] [Connecting to archive.canonicalbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:19 http://security.ubuntu.com dapper-security/multiverse Packages [2185B]
99% [19 Packages bzip2 0] [Connecting to archive.canonical.com]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:20 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Fetched 124B in 4s (29B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```


Remainder to follow as too much text to put in one post...

---

### Post by patslap on 2006-09-25
...continued from previous post:

sudo aptitude install kubuntu-desktop
```
pat@pat-desktop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm
  katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libflac++5c2 libgadu3 libifp4 libimlib2 libiso9660-4 libjpeg-progs
  libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1 liblockdev1
  libpoppler1-qt libpythonize0 libqt-perl librsync1 libruby1.8
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp3
  libvcdinfo0 libvisual-0.4-0 ncompress ocrad poster psutils
  pykdeextensions python-kde3 python-qt3 python2.4-dev python2.4-kde3
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8
  scim-qtimm skim speedcrunch vcdimager wlassistant zoo
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm
  katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libflac++5c2 libgadu3 libifp4 libimlib2 libiso9660-4
  libjpeg-progs libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1
  liblockdev1 libpoppler1-qt libpythonize0 libqt-perl librsync1 libruby1.8
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp3
  libvcdinfo0 libvisual-0.4-0 ncompress ocrad poster psutils
  pykdeextensions python-kde3 python-qt3 python2.4-dev python2.4-kde3
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8
  scim-qtimm skim speedcrunch vcdimager wlassistant zoo
0 packages upgraded, 140 newly installed, 0 to remove and 0 not upgraded.
Need to get 127MB of archives. After unpacking 404MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://security.ubuntu.com dapper-security/main libruby1.8 1.8.4-1ubuntu1. 1 [1506kB]
Get:2 http://archive.ubuntu.com dapper/main libtdb1 1.0.6-13 [17.5kB]
Get:3 http://archive.ubuntu.com dapper/main debtags 1.5.2ubuntu8 [1971kB]
Get:4 http://security.ubuntu.com dapper-security/main ruby1.8 1.8.4-1ubuntu1.1 [ 189kB]
Get:5 http://security.ubuntu.com dapper-security/main kate 4:3.5.2-0ubuntu27 [80 7kB]
Get:6 http://security.ubuntu.com dapper-security/main kdepasswd 4:3.5.2-0ubuntu2 7 [246kB]
Get:7 http://security.ubuntu.com dapper-security/main kdeprint 4:3.5.2-0ubuntu27  [1307kB]
Get:8 http://archive.ubuntu.com dapper-updates/main adept 2.0ubuntu2 [3844kB]
Get:9 http://security.ubuntu.com dapper-security/main kdm 4:3.5.2-0ubuntu27 [659 kB]
Get:10 http://security.ubuntu.com dapper-security/main khelpcenter 4:3.5.2-0ubun tu27 [2020kB]
Get:11 http://security.ubuntu.com dapper-security/main klipper 4:3.5.2-0ubuntu27  [287kB]
Get:12 http://archive.ubuntu.com dapper/main akregator 4:3.5.2-0ubuntu6 [753kB]
Get:13 http://security.ubuntu.com dapper-security/main kmenuedit 4:3.5.2-0ubuntu 27 [388kB]
Get:14 http://security.ubuntu.com dapper-security/main konqueror-nsplugins 4:3.5 .2-0ubuntu27 [153kB]
Get:15 http://archive.ubuntu.com dapper-backports/main amarok-xine 2:1.4.3-0ubun tu6~dapper1 [61.9kB]
Get:16 http://security.ubuntu.com dapper-security/main kpersonalizer 4:3.5.2-0ub untu27 [495kB]
Get:17 http://archive.ubuntu.com dapper/main ruby 1.8.2-1 [19.0kB]
Get:18 http://archive.ubuntu.com dapper/main python2.4-sip4-qt3 4.3.2-0ubuntu2 [ 74.8kB]
Get:19 http://archive.ubuntu.com dapper/main python2.4-qt3 3.15.1-0ubuntu3 [2769 kB]
Get:20 http://security.ubuntu.com dapper-security/main ksmserver 4:3.5.2-0ubuntu 27 [163kB]
Get:21 http://security.ubuntu.com dapper-security/main ksplash 4:3.5.2-0ubuntu27  [720kB]
Get:22 http://security.ubuntu.com dapper-security/main ksysguardd 4:3.5.2-0ubunt u27 [74.0kB]
Get:23 http://security.ubuntu.com dapper-security/main ksysguard 4:3.5.2-0ubuntu 27 [528kB]
Get:24 http://archive.ubuntu.com dapper/main python-qt3 3.15.1-0ubuntu3 [44.2kB]
Get:25 http://archive.ubuntu.com dapper/universe libifp4 1.0.0.2-2 [37.2kB]
Get:26 http://archive.ubuntu.com dapper-backports/main libtunepimp3 0.4.2-3ubunt u3~dapper1 [243kB]
Get:27 http://archive.ubuntu.com dapper-backports/main libvisual-0.4-0 0.4.0-1~d apper1 [141kB]
Get:28 http://archive.ubuntu.com dapper-backports/main amarok 2:1.4.3-0ubuntu6~d apper1 [15.0MB]
Get:29 http://archive.ubuntu.com dapper/main ark 4:3.5.2-0ubuntu8 [308kB]
Get:30 http://archive.ubuntu.com dapper/main arts 1.5.2-0ubuntu1 [6062B]
Get:31 http://archive.ubuntu.com dapper/main artsbuilder 4:3.5.2-0ubuntu3 [2310k B]
Get:32 http://archive.ubuntu.com dapper/main flac 1.1.2-3ubuntu1 [131kB]
Get:33 http://archive.ubuntu.com dapper/main gtk2-engines-gtk-qt 0.60-1.1ubuntu7  [79.4kB]
Get:34 http://archive.ubuntu.com dapper/main libkipi0 0.1.2-2ubuntu6 [114kB]
Get:35 http://archive.ubuntu.com dapper/main gwenview 1.3.1-0ubuntu5 [2082kB]
Get:36 http://archive.ubuntu.com dapper/main libflac++5c2 1.1.2-3ubuntu1 [40.1kB ]
Get:37 http://archive.ubuntu.com dapper-backports/main libk3b2 0.12.17-1ubuntu3~ dapper1 [1023kB]
Get:38 http://archive.ubuntu.com dapper-backports/main k3b 0.12.17-1ubuntu3~dapp er1 [4132kB]
Get:39 http://archive.ubuntu.com dapper/main kaffeine-xine 0.7.1-1.3ubuntu10 [18 8kB]
Get:40 http://archive.ubuntu.com dapper/main kaffeine 0.7.1-1.3ubuntu10 [1585kB]
Get:41 http://archive.ubuntu.com dapper/main karm 4:3.5.2-0ubuntu6 [466kB]
Get:42 http://archive.ubuntu.com dapper/main katapult 0.3.1.2-0ubuntu4 [298kB]
Get:43 http://archive.ubuntu.com dapper/main kaudiocreator 4:3.5.2-0ubuntu3 [171 kB]
Get:44 http://archive.ubuntu.com dapper/main kcron 4:3.5.2-0ubuntu8 [199kB]
Get:45 http://archive.ubuntu.com dapper/main python2.4-dev 2.4.3-0ubuntu4 [1633k B]
Get:46 http://archive.ubuntu.com dapper/main libpythonize0 0.4.0-0ubuntu3 [7706B ]
Get:47 http://archive.ubuntu.com dapper/main pykdeextensions 0.4.0-0ubuntu3 [113 kB]
Get:48 http://archive.ubuntu.com dapper/main python2.4-kde3 3.15.1+snapshot20060 118-0ubuntu1 [7952kB]
Get:49 http://archive.ubuntu.com dapper/main python-kde3 3.15.1+snapshot20060118 -0ubuntu1 [3654B]
Get:50 http://archive.ubuntu.com dapper-updates/main kde-guidance 0.6.7-0ubuntu5  [684kB]
Get:51 http://archive.ubuntu.com dapper/main kde-style-lipstik 2.1-1build1 [89.6 kB]
Get:52 http://archive.ubuntu.com dapper/main kde-systemsettings 0.0svn20060512-0 ubuntu1 [93.0kB]
Get:53 http://archive.ubuntu.com dapper/main kdeadmin-kfile-plugins 4:3.5.2-0ubu ntu8 [39.0kB]
Get:54 http://archive.ubuntu.com dapper/main liblockdev1 1.0.2-1 [12.4kB]
Get:55 http://archive.ubuntu.com dapper/main qobex 0.99+1.0beta1-6ubuntu8 [130kB ]
Get:56 http://archive.ubuntu.com dapper/main kdebluetooth 0.99+1.0beta1-6ubuntu8  [1446kB]
Get:57 http://archive.ubuntu.com dapper/main libpoppler1-qt 0.5.1-0ubuntu7 [42.3 kB]
Get:58 http://archive.ubuntu.com dapper/main kdegraphics-kfile-plugins 4:3.5.2-0 ubuntu6 [298kB]
Get:59 http://archive.ubuntu.com dapper/main kdemultimedia-kfile-plugins 4:3.5.2 -0ubuntu3 [155kB]
Get:60 http://archive.ubuntu.com dapper-updates/main kdenetwork-filesharing 4:3. 5.2-0ubuntu6.2 [657kB]
Get:61 http://archive.ubuntu.com dapper-updates/main kdenetwork-kfile-plugins 4: 3.5.2-0ubuntu6.2 [49.8kB]
Get:62 http://archive.ubuntu.com dapper/main kdepim-kresources 4:3.5.2-0ubuntu6 [2212kB]
Get:63 http://archive.ubuntu.com dapper/main kdepim-wizards 4:3.5.2-0ubuntu6 [17 2kB]
Get:64 http://archive.ubuntu.com dapper/main poster 20020830-3 [22.0kB]
Get:65 http://archive.ubuntu.com dapper/main psutils 1.17-21ubuntu1 [92.0kB]
Get:66 http://archive.ubuntu.com dapper-updates/main kdnssd 4:3.5.2-0ubuntu6.2 [ 61.4kB]
Get:67 http://archive.ubuntu.com dapper/main librsync1 0.9.7-1 [38.0kB]
Get:68 http://archive.ubuntu.com dapper/main rdiff-backup 1.1.5-1 [175kB]
Get:69 http://archive.ubuntu.com dapper/main keep 0.3.0-0ubuntu1 [225kB]
Get:70 http://archive.ubuntu.com dapper/main kio-apt 0.13-0ubuntu2 [77.7kB]
Get:71 http://archive.ubuntu.com dapper/main kio-locate 0.4.4-1ubuntu1 [105kB]
Get:72 http://archive.ubuntu.com dapper/main libimlib2 1.2.1-2 [214kB]
Get:73 http://archive.ubuntu.com dapper/universe libkexif1 0.2.2-2ubuntu2 [51.8k B]
Get:74 http://archive.ubuntu.com dapper/universe kipi-plugins 0.1+rc1-1ubuntu2 [ 4202kB]
Get:75 http://archive.ubuntu.com dapper/main kitchensync 4:3.5.2-0ubuntu6 [888kB ]
Get:76 http://archive.ubuntu.com dapper/main klaptopdaemon 4:3.5.2-0ubuntu8 [262 kB]
Get:77 http://archive.ubuntu.com dapper/main kmailcvt 4:3.5.2-0ubuntu6 [130kB]
Get:78 http://archive.ubuntu.com dapper/main kmilo 4:3.5.2-0ubuntu8 [161kB]
Get:79 http://archive.ubuntu.com dapper/main kmix 4:3.5.2-0ubuntu3 [401kB]
Get:80 http://archive.ubuntu.com dapper/main kmplayer-base 0.9.1.99+0.9.2-rc1-0u buntu1 [507kB]
Get:81 http://archive.ubuntu.com dapper/main kmplayer-konq-plugins 0.9.1.99+0.9. 2-rc1-0ubuntu1 [68.0kB]
Get:82 http://archive.ubuntu.com dapper/main knetworkconf 4:3.5.2-0ubuntu8 [605k B]
Get:83 http://archive.ubuntu.com dapper/universe knode 4:3.5.2-0ubuntu6 [1266kB]
Get:84 http://archive.ubuntu.com dapper/main knotes 4:3.5.2-0ubuntu6 [257kB]
Get:85 http://archive.ubuntu.com dapper/main koffice-data 1:1.5.0-0ubuntu9 [748k B]
Get:86 http://archive.ubuntu.com dapper/main koffice-libs 1:1.5.0-0ubuntu9 [2564 kB]
Get:87 http://archive.ubuntu.com dapper/main libjpeg-progs 6b-11 [81.4kB]
Get:88 http://archive.ubuntu.com dapper/main konq-plugins 4:3.5.2-0ubuntu4 [1197 kB]
Get:89 http://archive.ubuntu.com dapper/main kontact 4:3.5.2-0ubuntu6 [1661kB]
Get:90 http://archive.ubuntu.com dapper/main konversation 0.19-0ubuntu4 [5071kB]
Get:91 http://archive.ubuntu.com dapper/main libkscan1 4:3.5.2-0ubuntu6 [145kB]
Get:92 http://archive.ubuntu.com dapper/main kooka 4:3.5.2-0ubuntu6 [769kB]
Get:93 http://archive.ubuntu.com dapper/main libgadu3 1:1.6+20051103-1ubuntu1 [6 7.8kB]
Get:94 http://archive.ubuntu.com dapper-updates/main kopete 4:3.5.2-0ubuntu6.2 [ 5760kB]
Get:95 http://archive.ubuntu.com dapper/main libkpimexchange1 4:3.5.2-0ubuntu6 [ 117kB]
Get:96 http://archive.ubuntu.com dapper/main korganizer 4:3.5.2-0ubuntu6 [1640kB ]
Get:97 http://archive.ubuntu.com dapper/main kpdf 4:3.5.2-0ubuntu6 [338kB]
Get:98 http://archive.ubuntu.com dapper-updates/main kpf 4:3.5.2-0ubuntu6.2 [210 kB]
Get:99 http://archive.ubuntu.com dapper-updates/main kppp 4:3.5.2-0ubuntu6.2 [71 0kB]
Get:100 http://archive.ubuntu.com dapper-updates/main krdc 4:3.5.2-0ubuntu6.2 [5 20kB]
Get:101 http://archive.ubuntu.com dapper/universe kregexpeditor 4:3.5.2-0ubuntu8  [305kB]
Get:102 http://archive.ubuntu.com dapper-updates/main krfb 4:3.5.2-0ubuntu6.2 [9 62kB]
Get:103 http://archive.ubuntu.com dapper/main krita-data 1:1.5.0-0ubuntu9 [9816k B]
Get:104 http://archive.ubuntu.com dapper/main krita 1:1.5.0-0ubuntu9 [2914kB]
Get:105 http://archive.ubuntu.com dapper/main kscd 4:3.5.2-0ubuntu3 [434kB]
Get:106 http://archive.ubuntu.com dapper/main kscreensaver 4:3.5.2-0ubuntu4 [852 kB]
Get:107 http://archive.ubuntu.com dapper/main kscreensaver-xsavers 4:3.5.2-0ubun tu4 [117kB]
Get:108 http://archive.ubuntu.com dapper/main ksnapshot 4:3.5.2-0ubuntu6 [155kB]
Get:109 http://archive.ubuntu.com dapper/main ksplash-engine-moodin 0.4.2-0ubunt u7 [681kB]
Get:110 http://archive.ubuntu.com dapper/main ksvg 4:3.5.2-0ubuntu6 [1214kB]
Get:111 http://archive.ubuntu.com dapper/main libsensors3 1:2.9.2-5ubuntu3 [90.6 kB]
Get:112 http://archive.ubuntu.com dapper/main ksystemlog 0.3.2-0ubuntu4 [218kB]
Get:113 http://archive.ubuntu.com dapper-backports/main ktorrent 2.0.1-0ubuntu1~ dapper1 [1766kB]
Get:114 http://archive.ubuntu.com dapper-updates/main kubuntu-artwork-usplash 1: 6.06-22 [17.5kB]
Get:115 http://archive.ubuntu.com dapper/main kwin-style-crystal 0.9.9-0ubuntu4 [128kB]
Get:116 http://archive.ubuntu.com dapper-updates/main kubuntu-default-settings 1 :6.06-22 [2018kB]
Get:117 http://archive.ubuntu.com dapper-updates/main kubuntu-docs 6.06-12 [4653 kB]
Get:118 http://archive.ubuntu.com dapper/main kubuntu-konqueror-shortcuts 0.3-0u buntu1 [3288B]
Get:119 http://archive.ubuntu.com dapper/main kwalletmanager 4:3.5.2-0ubuntu8 [3 55kB]
Get:120 http://archive.ubuntu.com dapper-updates/main language-selector-qt 0.1.2 0.1 [9612B]
Get:121 http://archive.ubuntu.com dapper/main libsamplerate0 0.1.2-2 [109kB]
Get:122 http://archive.ubuntu.com dapper/main libakode2 2.0-0ubuntu3 [95.5kB]
Get:123 http://archive.ubuntu.com dapper/main libarts1-akode 4:3.5.2-0ubuntu3 [1 90kB]
Get:124 http://archive.ubuntu.com dapper/main qca-tls 1.0-3 [30.3kB]
Get:125 http://archive.ubuntu.com dapper/main scim-qtimm 0.9.4-0ubuntu4 [56.7kB]
Get:126 http://archive.ubuntu.com dapper/main libskim0 1.4.4-0ubuntu7 [240kB]
Get:127 http://archive.ubuntu.com dapper/main skim 1.4.4-0ubuntu7 [1271kB]
Get:128 http://archive.ubuntu.com dapper/main speedcrunch 0.6beta2-0ubuntu1 [178 kB]
Get:129 http://archive.ubuntu.com dapper/main wlassistant 0.5.5-0ubuntu2 [147kB]
Get:130 http://archive.ubuntu.com dapper-updates/main kubuntu-desktop 0.86 [12.0 kB]
Get:131 http://archive.ubuntu.com dapper/universe libiso9660-4 0.76-1ubuntu1 [96 .1kB]
Get:132 http://archive.ubuntu.com dapper/main libsmokeqt1 4:3.5.2-0ubuntu2 [1399 kB]
Get:133 http://archive.ubuntu.com dapper/main libqt-perl 3.008-1.4 [361kB]
Get:134 http://archive.ubuntu.com dapper/universe libvcdinfo0 0.7.23-1ubuntu1 [1 32kB]
Get:135 http://archive.ubuntu.com dapper/universe ncompress 4.2.4-15 [22.7kB]
Get:136 http://archive.ubuntu.com dapper/universe ocrad 0.13-1 [127kB]
Get:137 http://archive.ubuntu.com dapper/universe vcdimager 0.7.23-1ubuntu1 [558 kB]
Get:138 http://archive.ubuntu.com dapper/universe zoo 2.10-17 [67.7kB]
Get:139 http://archive.ubuntu.com dapper/universe dcraw 7.94-1ubuntu1 [117kB]
Get:140 http://archive.ubuntu.com dapper/main latex-xft-fonts 0.1-5 [95.3kB]
Fetched 127MB in 35m22s (59.7kB/s)
Extract templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package libtdb1.
(Reading database ... 109279 files and directories currently installed.)
Unpacking libtdb1 (from .../libtdb1_1.0.6-13_amd64.deb) ...
Selecting previously deselected package debtags.
Unpacking debtags (from .../debtags_1.5.2ubuntu8_amd64.deb) ...
Selecting previously deselected package adept.
Unpacking adept (from .../adept_2.0ubuntu2_amd64.deb) ...
Selecting previously deselected package akregator.
Unpacking akregator (from .../akregator_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package amarok-xine.
Unpacking amarok-xine (from .../amarok-xine_2%3a1.4.3-0ubuntu6~dapper1_amd64.deb ) ...
Selecting previously deselected package libruby1.8.
Unpacking libruby1.8 (from .../libruby1.8_1.8.4-1ubuntu1.1_amd64.deb) ...
Selecting previously deselected package ruby1.8.
Unpacking ruby1.8 (from .../ruby1.8_1.8.4-1ubuntu1.1_amd64.deb) ...
Selecting previously deselected package ruby.
Unpacking ruby (from .../archives/ruby_1.8.2-1_all.deb) ...
Selecting previously deselected package python2.4-sip4-qt3.
Unpacking python2.4-sip4-qt3 (from .../python2.4-sip4-qt3_4.3.2-0ubuntu2_amd64.d eb) ...
Selecting previously deselected package python2.4-qt3.
Unpacking python2.4-qt3 (from .../python2.4-qt3_3.15.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package python-qt3.
Unpacking python-qt3 (from .../python-qt3_3.15.1-0ubuntu3_all.deb) ...
Selecting previously deselected package libifp4.
Unpacking libifp4 (from .../libifp4_1.0.0.2-2_amd64.deb) ...
Selecting previously deselected package libtunepimp3.
Unpacking libtunepimp3 (from .../libtunepimp3_0.4.2-3ubuntu3~dapper1_amd64.deb) ...
Selecting previously deselected package libvisual-0.4-0.
Unpacking libvisual-0.4-0 (from .../libvisual-0.4-0_0.4.0-1~dapper1_amd64.deb) . ..
Selecting previously deselected package amarok.
Unpacking amarok (from .../amarok_2%3a1.4.3-0ubuntu6~dapper1_amd64.deb) ...
Selecting previously deselected package ark.
Unpacking ark (from .../ark_4%3a3.5.2-0ubuntu8_amd64.deb) ...
Selecting previously deselected package arts.
Unpacking arts (from .../arts_1.5.2-0ubuntu1_all.deb) ...
Selecting previously deselected package artsbuilder.
Unpacking artsbuilder (from .../artsbuilder_4%3a3.5.2-0ubuntu3_amd64.deb) ...
Selecting previously deselected package flac.
Unpacking flac (from .../flac_1.1.2-3ubuntu1_amd64.deb) ...
Selecting previously deselected package gtk2-engines-gtk-qt.
Unpacking gtk2-engines-gtk-qt (from .../gtk2-engines-gtk-qt_0.60-1.1ubuntu7_amd6 4.deb) ...
Selecting previously deselected package libkipi0.
Unpacking libkipi0 (from .../libkipi0_0.1.2-2ubuntu6_amd64.deb) ...
Selecting previously deselected package gwenview.
Unpacking gwenview (from .../gwenview_1.3.1-0ubuntu5_amd64.deb) ...
Selecting previously deselected package libflac++5c2.
Unpacking libflac++5c2 (from .../libflac++5c2_1.1.2-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libk3b2.
Unpacking libk3b2 (from .../libk3b2_0.12.17-1ubuntu3~dapper1_amd64.deb) ...
Selecting previously deselected package k3b.
Unpacking k3b (from .../k3b_0.12.17-1ubuntu3~dapper1_amd64.deb) ...
Selecting previously deselected package kaffeine-xine.
Unpacking kaffeine-xine (from .../kaffeine-xine_0.7.1-1.3ubuntu10_amd64.deb) ...
Selecting previously deselected package kaffeine.
Unpacking kaffeine (from .../kaffeine_0.7.1-1.3ubuntu10_amd64.deb) ...
Selecting previously deselected package karm.
Unpacking karm (from .../karm_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package katapult.
Unpacking katapult (from .../katapult_0.3.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package kate.
Unpacking kate (from .../kate_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kaudiocreator.
Unpacking kaudiocreator (from .../kaudiocreator_4%3a3.5.2-0ubuntu3_amd64.deb) .. .
Selecting previously deselected package kcron.
Unpacking kcron (from .../kcron_4%3a3.5.2-0ubuntu8_amd64.deb) ...
Selecting previously deselected package python2.4-dev.
Unpacking python2.4-dev (from .../python2.4-dev_2.4.3-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libpythonize0.
Unpacking libpythonize0 (from .../libpythonize0_0.4.0-0ubuntu3_amd64.deb) ...
Selecting previously deselected package pykdeextensions.
Unpacking pykdeextensions (from .../pykdeextensions_0.4.0-0ubuntu3_amd64.deb) .. .
Selecting previously deselected package python2.4-kde3.
Unpacking python2.4-kde3 (from .../python2.4-kde3_3.15.1+snapshot20060118-0ubunt u1_amd64.deb) ...
Selecting previously deselected package python-kde3.
Unpacking python-kde3 (from .../python-kde3_3.15.1+snapshot20060118-0ubuntu1_all .deb) ...
Selecting previously deselected package kde-guidance.
Unpacking kde-guidance (from .../kde-guidance_0.6.7-0ubuntu5_amd64.deb) ...
Selecting previously deselected package kde-style-lipstik.
Unpacking kde-style-lipstik (from .../kde-style-lipstik_2.1-1build1_amd64.deb) . ..
Selecting previously deselected package kde-systemsettings.
Unpacking kde-systemsettings (from .../kde-systemsettings_0.0svn20060512-0ubuntu 1_amd64.deb) ...
Selecting previously deselected package kdeadmin-kfile-plugins.
Unpacking kdeadmin-kfile-plugins (from .../kdeadmin-kfile-plugins_4%3a3.5.2-0ubu ntu8_amd64.deb) ...
Selecting previously deselected package liblockdev1.
Unpacking liblockdev1 (from .../liblockdev1_1.0.2-1_amd64.deb) ...
Selecting previously deselected package qobex.
Unpacking qobex (from .../qobex_0.99+1.0beta1-6ubuntu8_amd64.deb) ...
Selecting previously deselected package kdebluetooth.
Unpacking kdebluetooth (from .../kdebluetooth_0.99+1.0beta1-6ubuntu8_amd64.deb) ...
Selecting previously deselected package libpoppler1-qt.
Unpacking libpoppler1-qt (from .../libpoppler1-qt_0.5.1-0ubuntu7_amd64.deb) ...
Selecting previously deselected package kdegraphics-kfile-plugins.
Unpacking kdegraphics-kfile-plugins (from .../kdegraphics-kfile-plugins_4%3a3.5. 2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package kdemultimedia-kfile-plugins.
Unpacking kdemultimedia-kfile-plugins (from .../kdemultimedia-kfile-plugins_4%3a 3.5.2-0ubuntu3_amd64.deb) ...
Selecting previously deselected package kdenetwork-filesharing.
Unpacking kdenetwork-filesharing (from .../kdenetwork-filesharing_4%3a3.5.2-0ubu ntu6.2_amd64.deb) ...
Selecting previously deselected package kdenetwork-kfile-plugins.
Unpacking kdenetwork-kfile-plugins (from .../kdenetwork-kfile-plugins_4%3a3.5.2- 0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package kdepasswd.
Unpacking kdepasswd (from .../kdepasswd_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kdepim-kresources.
Unpacking kdepim-kresources (from .../kdepim-kresources_4%3a3.5.2-0ubuntu6_amd64 .deb) ...
Selecting previously deselected package kdepim-wizards.
Unpacking kdepim-wizards (from .../kdepim-wizards_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package poster.
Unpacking poster (from .../poster_20020830-3_amd64.deb) ...
Selecting previously deselected package psutils.
Unpacking psutils (from .../psutils_1.17-21ubuntu1_amd64.deb) ...
Selecting previously deselected package kdeprint.
Unpacking kdeprint (from .../kdeprint_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kdm.
Unpacking kdm (from .../kdm_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kdnssd.
Unpacking kdnssd (from .../kdnssd_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package librsync1.
Unpacking librsync1 (from .../librsync1_0.9.7-1_amd64.deb) ...
Selecting previously deselected package rdiff-backup.
Unpacking rdiff-backup (from .../rdiff-backup_1.1.5-1_amd64.deb) ...
Selecting previously deselected package keep.
Unpacking keep (from .../keep_0.3.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package khelpcenter.
Unpacking khelpcenter (from .../khelpcenter_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kio-apt.
Unpacking kio-apt (from .../kio-apt_0.13-0ubuntu2_amd64.deb) ...
Selecting previously deselected package kio-locate.
Unpacking kio-locate (from .../kio-locate_0.4.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.2.1-2_amd64.deb) ...
Selecting previously deselected package libkexif1.
Unpacking libkexif1 (from .../libkexif1_0.2.2-2ubuntu2_amd64.deb) ...
Selecting previously deselected package kipi-plugins.
Unpacking kipi-plugins (from .../kipi-plugins_0.1+rc1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package kitchensync.
Unpacking kitchensync (from .../kitchensync_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package klaptopdaemon.
Unpacking klaptopdaemon (from .../klaptopdaemon_4%3a3.5.2-0ubuntu8_amd64.deb) .. .
Selecting previously deselected package klipper.
Unpacking klipper (from .../klipper_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kmailcvt.
Unpacking kmailcvt (from .../kmailcvt_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package kmenuedit.
Unpacking kmenuedit (from .../kmenuedit_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package kmilo.
Unpacking kmilo (from .../kmilo_4%3a3.5.2-0ubuntu8_amd64.deb) ...
Selecting previously deselected package kmix.
Unpacking kmix (from .../kmix_4%3a3.5.2-0ubuntu3_amd64.deb) ...
Selecting previously deselected package kmplayer-base.
Unpacking kmplayer-base (from .../kmplayer-base_0.9.1.99+0.9.2-rc1-0ubuntu1_amd6 4.deb) ...
Selecting previously deselected package kmplayer-konq-plugins.
Unpacking kmplayer-konq-plugins (from .../kmplayer-konq-plugins_0.9.1.99+0.9.2-r c1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package knetworkconf.
Unpacking knetworkconf (from .../knetworkconf_4%3a3.5.2-0ubuntu8_amd64.deb) ...
Selecting previously deselected package knode.
Unpacking knode (from .../knode_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package knotes.
Unpacking knotes (from .../knotes_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package koffice-data.
Unpacking koffice-data (from .../koffice-data_1%3a1.5.0-0ubuntu9_all.deb) ...

```

continued in next post....

---

### Post by patslap on 2006-09-25
...continued from previous post:


```

Selecting previously deselected package koffice-libs.
Unpacking koffice-libs (from .../koffice-libs_1%3a1.5.0-0ubuntu9_amd64.deb) ...
Selecting previously deselected package libjpeg-progs.
Unpacking libjpeg-progs (from .../libjpeg-progs_6b-11_amd64.deb) ...
Selecting previously deselected package konq-plugins.
Unpacking konq-plugins (from .../konq-plugins_4%3a3.5.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package konqueror-nsplugins.
Unpacking konqueror-nsplugins (from .../konqueror-nsplugins_4%3a3.5.2-0ubuntu27_ amd64.deb) ...
Selecting previously deselected package kontact.
Unpacking kontact (from .../kontact_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package konversation.
Unpacking konversation (from .../konversation_0.19-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkscan1.
Unpacking libkscan1 (from .../libkscan1_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package kooka.
Unpacking kooka (from .../kooka_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package libgadu3.
Unpacking libgadu3 (from .../libgadu3_1%3a1.6+20051103-1ubuntu1_amd64.deb) ...
Selecting previously deselected package kopete.
Unpacking kopete (from .../kopete_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libkpimexchange1.
Unpacking libkpimexchange1 (from .../libkpimexchange1_4%3a3.5.2-0ubuntu6_amd64.d eb) ...
Selecting previously deselected package korganizer.
Unpacking korganizer (from .../korganizer_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package kpdf.
Unpacking kpdf (from .../kpdf_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package kpersonalizer.
Unpacking kpersonalizer (from .../kpersonalizer_4%3a3.5.2-0ubuntu27_amd64.deb) . ..
Selecting previously deselected package kpf.
Unpacking kpf (from .../kpf_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package kppp.
Unpacking kppp (from .../kppp_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package krdc.
Unpacking krdc (from .../krdc_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package kregexpeditor.
Unpacking kregexpeditor (from .../kregexpeditor_4%3a3.5.2-0ubuntu8_amd64.deb) .. .
Selecting previously deselected package krfb.
Unpacking krfb (from .../krfb_4%3a3.5.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package krita-data.
Unpacking krita-data (from .../krita-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package krita.
Unpacking krita (from .../krita_1%3a1.5.0-0ubuntu9_amd64.deb) ...
Selecting previously deselected package kscd.
Unpacking kscd (from .../kscd_4%3a3.5.2-0ubuntu3_amd64.deb) ...
Selecting previously deselected package kscreensaver.
Unpacking kscreensaver (from .../kscreensaver_4%3a3.5.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package kscreensaver-xsavers.
Unpacking kscreensaver-xsavers (from .../kscreensaver-xsavers_4%3a3.5.2-0ubuntu4 _amd64.deb) ...
Selecting previously deselected package ksmserver.
Unpacking ksmserver (from .../ksmserver_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package ksnapshot.
Unpacking ksnapshot (from .../ksnapshot_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package ksplash.
Unpacking ksplash (from .../ksplash_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package ksplash-engine-moodin.
Unpacking ksplash-engine-moodin (from .../ksplash-engine-moodin_0.4.2-0ubuntu7_a md64.deb) ...
Selecting previously deselected package ksvg.
Unpacking ksvg (from .../ksvg_4%3a3.5.2-0ubuntu6_amd64.deb) ...
Selecting previously deselected package libsensors3.
Unpacking libsensors3 (from .../libsensors3_1%3a2.9.2-5ubuntu3_amd64.deb) ...
Selecting previously deselected package ksysguardd.
Unpacking ksysguardd (from .../ksysguardd_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package ksysguard.
Unpacking ksysguard (from .../ksysguard_4%3a3.5.2-0ubuntu27_amd64.deb) ...
Selecting previously deselected package ksystemlog.
Unpacking ksystemlog (from .../ksystemlog_0.3.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package ktorrent.
Unpacking ktorrent (from .../ktorrent_2.0.1-0ubuntu1~dapper1_amd64.deb) ...
Selecting previously deselected package kubuntu-artwork-usplash.
Unpacking kubuntu-artwork-usplash (from .../kubuntu-artwork-usplash_1%3a6.06-22_ amd64.deb) ...
Selecting previously deselected package kwin-style-crystal.
Unpacking kwin-style-crystal (from .../kwin-style-crystal_0.9.9-0ubuntu4_amd64.d eb) ...
Selecting previously deselected package kubuntu-default-settings.
Unpacking kubuntu-default-settings (from .../kubuntu-default-settings_1%3a6.06-2 2_all.deb) ...
Selecting previously deselected package kubuntu-docs.
Unpacking kubuntu-docs (from .../kubuntu-docs_6.06-12_all.deb) ...
Selecting previously deselected package kubuntu-konqueror-shortcuts.
Unpacking kubuntu-konqueror-shortcuts (from .../kubuntu-konqueror-shortcuts_0.3- 0ubuntu1_all.deb) ...
Selecting previously deselected package kwalletmanager.
Unpacking kwalletmanager (from .../kwalletmanager_4%3a3.5.2-0ubuntu8_amd64.deb) ...
Selecting previously deselected package language-selector-qt.
Unpacking language-selector-qt (from .../language-selector-qt_0.1.20.1_all.deb) ...
Selecting previously deselected package libsamplerate0.
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.2-2_amd64.deb) ...
Selecting previously deselected package libakode2.
Unpacking libakode2 (from .../libakode2_2.0-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libarts1-akode.
Unpacking libarts1-akode (from .../libarts1-akode_4%3a3.5.2-0ubuntu3_amd64.deb) ...
Selecting previously deselected package qca-tls.
Unpacking qca-tls (from .../qca-tls_1.0-3_amd64.deb) ...
Selecting previously deselected package scim-qtimm.
Unpacking scim-qtimm (from .../scim-qtimm_0.9.4-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libskim0.
Unpacking libskim0 (from .../libskim0_1.4.4-0ubuntu7_amd64.deb) ...
Selecting previously deselected package skim.
Unpacking skim (from .../skim_1.4.4-0ubuntu7_amd64.deb) ...
Selecting previously deselected package speedcrunch.
Unpacking speedcrunch (from .../speedcrunch_0.6beta2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package wlassistant.
Unpacking wlassistant (from .../wlassistant_0.5.5-0ubuntu2_amd64.deb) ...
Selecting previously deselected package kubuntu-desktop.
Unpacking kubuntu-desktop (from .../kubuntu-desktop_0.86_amd64.deb) ...
Selecting previously deselected package libiso9660-4.
Unpacking libiso9660-4 (from .../libiso9660-4_0.76-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libsmokeqt1.
Unpacking libsmokeqt1 (from .../libsmokeqt1_4%3a3.5.2-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libqt-perl.
Unpacking libqt-perl (from .../libqt-perl_3.008-1.4_amd64.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-1ubuntu1_amd64.deb) ...
Selecting previously deselected package ncompress.
Unpacking ncompress (from .../ncompress_4.2.4-15_amd64.deb) ...
Selecting previously deselected package ocrad.
Unpacking ocrad (from .../ocrad_0.13-1_amd64.deb) ...
Selecting previously deselected package vcdimager.
Unpacking vcdimager (from .../vcdimager_0.7.23-1ubuntu1_amd64.deb) ...
Selecting previously deselected package zoo.
Unpacking zoo (from .../archives/zoo_2.10-17_amd64.deb) ...
Selecting previously deselected package dcraw.
Unpacking dcraw (from .../dcraw_7.94-1ubuntu1_amd64.deb) ...
Selecting previously deselected package latex-xft-fonts.
Unpacking latex-xft-fonts (from .../latex-xft-fonts_0.1-5_all.deb) ...
Setting up libtdb1 (1.0.6-13) ...

Setting up debtags (1.5.2ubuntu8) ...

Setting up adept (2.0ubuntu2) ...

Setting up akregator (3.5.2-0ubuntu6) ...

Setting up libruby1.8 (1.8.4-1ubuntu1.1) ...

Setting up ruby1.8 (1.8.4-1ubuntu1.1) ...
Setting up ruby (1.8.2-1) ...
Setting up python2.4-sip4-qt3 (4.3.2-0ubuntu2) ...

Setting up python2.4-qt3 (3.15.1-0ubuntu3) ...

Setting up python-qt3 (3.15.1-0ubuntu3) ...
Setting up libifp4 (1.0.0.2-2) ...

Setting up libtunepimp3 (0.4.2-3ubuntu3~dapper1) ...

Setting up libvisual-0.4-0 (0.4.0-1~dapper1) ...

Setting up ark (3.5.2-0ubuntu8) ...

Setting up arts (1.5.2-0ubuntu1) ...
Setting up artsbuilder (3.5.2-0ubuntu3) ...

Setting up flac (1.1.2-3ubuntu1) ...
Setting up gtk2-engines-gtk-qt (0.60-1.1ubuntu7) ...
Setting up libkipi0 (0.1.2-2ubuntu6) ...

Setting up gwenview (1.3.1-0ubuntu5) ...

Setting up libflac++5c2 (1.1.2-3ubuntu1) ...
Setting up libk3b2 (0.12.17-1ubuntu3~dapper1) ...

Setting up k3b (0.12.17-1ubuntu3~dapper1) ...

Setting up karm (3.5.2-0ubuntu6) ...

Setting up katapult (0.3.1.2-0ubuntu4) ...

Setting up kate (3.5.2-0ubuntu27) ...

Setting up kaudiocreator (3.5.2-0ubuntu3) ...

Setting up kcron (3.5.2-0ubuntu8) ...

Setting up python2.4-dev (2.4.3-0ubuntu4) ...

Setting up libpythonize0 (0.4.0-0ubuntu3) ...

Setting up pykdeextensions (0.4.0-0ubuntu3) ...

Setting up python2.4-kde3 (3.15.1+snapshot20060118-0ubuntu1) ...

Setting up python-kde3 (3.15.1+snapshot20060118-0ubuntu1) ...
Setting up kde-guidance (0.6.7-0ubuntu5) ...
 Adding system startup for /etc/init.d/displayconfig-hwprobe.py ...
   /etc/rcS.d/S60displayconfig-hwprobe.py -> ../init.d/displayconfig-hwprobe.py

Setting up kde-style-lipstik (2.1-1build1) ...
Setting up kde-systemsettings (0.0svn20060512-0ubuntu1) ...
Setting up kdeadmin-kfile-plugins (3.5.2-0ubuntu8) ...
Setting up liblockdev1 (1.0.2-1) ...

Setting up qobex (0.99+1.0beta1-6ubuntu8) ...

Setting up kdebluetooth (0.99+1.0beta1-6ubuntu8) ...

Setting up libpoppler1-qt (0.5.1-0ubuntu7) ...

Setting up kdegraphics-kfile-plugins (3.5.2-0ubuntu6) ...
Setting up kdemultimedia-kfile-plugins (3.5.2-0ubuntu3) ...
Setting up kdenetwork-filesharing (3.5.2-0ubuntu6.2) ...

Setting up kdenetwork-kfile-plugins (3.5.2-0ubuntu6.2) ...
Setting up kdepasswd (3.5.2-0ubuntu27) ...

Setting up kdepim-kresources (3.5.2-0ubuntu6) ...

Setting up kdepim-wizards (3.5.2-0ubuntu6) ...

Setting up poster (20020830-3) ...
Setting up psutils (1.17-21ubuntu1) ...
Setting up kdeprint (3.5.2-0ubuntu27) ...

Setting up kdm (3.5.2-0ubuntu27) ...

Setting up kdnssd (3.5.2-0ubuntu6.2) ...
Setting up librsync1 (0.9.7-1) ...

Setting up rdiff-backup (1.1.5-1) ...

Setting up keep (0.3.0-0ubuntu1) ...
Setting up khelpcenter (3.5.2-0ubuntu27) ...

Setting up kio-apt (0.13-0ubuntu2) ...
Setting up kio-locate (0.4.4-1ubuntu1) ...
Setting up libimlib2 (1.2.1-2) ...

Setting up libkexif1 (0.2.2-2ubuntu2) ...

Setting up kipi-plugins (0.1+rc1-1ubuntu2) ...
Setting up kitchensync (3.5.2-0ubuntu6) ...

Setting up klaptopdaemon (3.5.2-0ubuntu8) ...

Setting up klipper (3.5.2-0ubuntu27) ...

Setting up kmailcvt (3.5.2-0ubuntu6) ...

Setting up kmenuedit (3.5.2-0ubuntu27) ...

Setting up kmilo (3.5.2-0ubuntu8) ...

Setting up kmix (3.5.2-0ubuntu3) ...

Setting up kmplayer-base (0.9.1.99+0.9.2-rc1-0ubuntu1) ...
Setting up kmplayer-konq-plugins (0.9.1.99+0.9.2-rc1-0ubuntu1) ...
Setting up knetworkconf (3.5.2-0ubuntu8) ...

Setting up knode (3.5.2-0ubuntu6) ...

Setting up knotes (3.5.2-0ubuntu6) ...

Setting up koffice-data (1.5.0-0ubuntu9) ...

Setting up koffice-libs (1.5.0-0ubuntu9) ...

Setting up libjpeg-progs (6b-11) ...
Setting up konq-plugins (3.5.2-0ubuntu4) ...

Setting up konqueror-nsplugins (3.5.2-0ubuntu27) ...

Setting up kontact (3.5.2-0ubuntu6) ...

Setting up konversation (0.19-0ubuntu4) ...

Setting up libkscan1 (3.5.2-0ubuntu6) ...

Setting up kooka (3.5.2-0ubuntu6) ...

Setting up libgadu3 (1.6+20051103-1ubuntu1) ...

Setting up kopete (3.5.2-0ubuntu6.2) ...

Setting up libkpimexchange1 (3.5.2-0ubuntu6) ...

Setting up korganizer (3.5.2-0ubuntu6) ...

Setting up kpdf (3.5.2-0ubuntu6) ...

Setting up kpersonalizer (3.5.2-0ubuntu27) ...

Setting up kpf (3.5.2-0ubuntu6.2) ...

Setting up kppp (3.5.2-0ubuntu6.2) ...

Setting up krdc (3.5.2-0ubuntu6.2) ...

Setting up kregexpeditor (3.5.2-0ubuntu8) ...

Setting up krfb (3.5.2-0ubuntu6.2) ...

Setting up krita-data (1.5.0-0ubuntu9) ...

Setting up krita (1.5.0-0ubuntu9) ...

Setting up kscd (3.5.2-0ubuntu3) ...

Setting up kscreensaver (3.5.2-0ubuntu4) ...
Setting up kscreensaver-xsavers (3.5.2-0ubuntu4) ...
Setting up ksmserver (3.5.2-0ubuntu27) ...

Setting up ksnapshot (3.5.2-0ubuntu6) ...

Setting up ksplash (3.5.2-0ubuntu27) ...

Setting up ksplash-engine-moodin (0.4.2-0ubuntu7) ...
Setting up ksvg (3.5.2-0ubuntu6) ...

Setting up libsensors3 (2.9.2-5ubuntu3) ...

Setting up ksysguardd (3.5.2-0ubuntu27) ...
Setting up ksysguard (3.5.2-0ubuntu27) ...

Setting up ksystemlog (0.3.2-0ubuntu4) ...

Setting up ktorrent (2.0.1-0ubuntu1~dapper1) ...

Setting up kubuntu-artwork-usplash (6.06-22) ...

Setting up kwin-style-crystal (0.9.9-0ubuntu4) ...
Setting up kubuntu-default-settings (6.06-22) ...
Setting default mouse cursor theme to Kubuntu ...
KDM theme customised or already enabled, not touching kdmrc ...

Setting up kubuntu-docs (6.06-12) ...

Setting up kubuntu-konqueror-shortcuts (0.3-0ubuntu1) ...
Setting up kwalletmanager (3.5.2-0ubuntu8) ...

Setting up language-selector-qt (0.1.20.1) ...

Setting up libsamplerate0 (0.1.2-2) ...

Setting up libakode2 (2.0-0ubuntu3) ...

Setting up libarts1-akode (3.5.2-0ubuntu3) ...
Setting up qca-tls (1.0-3) ...
Setting up scim-qtimm (0.9.4-0ubuntu4) ...
Setting up libskim0 (1.4.4-0ubuntu7) ...

Setting up skim (1.4.4-0ubuntu7) ...
Setting up speedcrunch (0.6beta2-0ubuntu1) ...
Setting up wlassistant (0.5.5-0ubuntu2) ...
Setting up libiso9660-4 (0.76-1ubuntu1) ...

Setting up libsmokeqt1 (3.5.2-0ubuntu2) ...

Setting up libqt-perl (3.008-1.4) ...
Setting up libvcdinfo0 (0.7.23-1ubuntu1) ...

Setting up ncompress (4.2.4-15) ...
Setting up ocrad (0.13-1) ...

Setting up vcdimager (0.7.23-1ubuntu1) ...

Setting up zoo (2.10-17) ...
Setting up dcraw (7.94-1ubuntu1) ...
Setting up latex-xft-fonts (0.1-5) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Regenerating fonts cache...done.

Setting up amarok-xine (1.4.3-0ubuntu6~dapper1) ...
Setting up amarok (1.4.3-0ubuntu6~dapper1) ...

Setting up kaffeine-xine (0.7.1-1.3ubuntu10) ...
Setting up kubuntu-desktop (0.86) ...
Setting up kaffeine (0.7.1-1.3ubuntu10) ...

```



cd /usr/share/xsessions
ls
cat kde.desktop
```
pat@pat-desktop:~$ cd /usr/share/xsessions
pat@pat-desktop:/usr/share/xsessions$ ls
gnome.desktop  kde.desktop  xgl.desktop
pat@pat-desktop:/usr/share/xsessions$ cat kde.desktop
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE
Name[hi]=&#2325;&#2375;&#2337;&#2368;&#2312;
Name[mn]=&#1050;&#1044;&#1069;
Name[ta]=K&#2959;&#2993;&#3021;&#2993;&#2965;&#3021; &#2965;&#3006;&#2997;&#2994;&#2985;&#3021;
Name[xh]=iKDE
Name[xx]=xxKDExx
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
Comment[bs]=K Desktop Environment. Mo&#263;an grafi&#269;ki desktop otvorenog izvornog koda
Comment[ca]=L'entorn d'escriptori K. Un poderós entorn d'escriptori gràfic de Codi Font Obert
Comment[cy]=Yr Amgylchedd Penbwrdd K.  Amgylchedd penbwrdd graffegol pwerus, sy'n gôd-agored.
Comment[da]=K Skrivebordsmiljøet. Et kraftigt, åbent, grafisk skrivebordsmiljø
Comment[de]=Das K Desktop Environment. Eine mächtige, graphische Arbeitsumgebung und Open Source / Freie Software
Comment[el]=&#932;&#959; K Desktop Environment. &#904;&#957;&#945; &#960;&#945;&#957;&#943;&#963;&#967;&#965;&#961;&#959; &#949;&#955;&#949;&#973;&#952;&#949;&#961;&#951;&#962; &#960;&#961;&#959;&#941;&#955;&#949;&#965;&#963;&#951;&#962; &#947;&#961;&#945;&#966;&#953;&#954;&#972; &#960;&#949;&#961;&#953;&#946;&#940;&#955;&#955;&#959;&#957; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[es]=El Entorno de Escritorio K, un potente entorno de escritorio gráfico realizado de código abierto
Comment[et]=K töölaua keskkond on võimas vaba tarkvara graafiline töölaua keskkond
Comment[fi]=KDE-työpöytäympäristö (K Desktop Environment) on tehokas avoimen lähdekoodin graafinen työpöytäympäristö
Comment[fr]=The K Desktop Environment. Un environnement de bureau graphique, puissant et Open Source
Comment[he]=The K Desktop Environment. &#1505;&#1489;&#1497;&#1489;&#1514; &#1506;&#1489;&#1493;&#1491;&#1492; &#1490;&#1512;&#1508;&#1497;&#1514;, &#1489;&#1506;&#1500;&#1514;-&#1506;&#1493;&#1510;&#1502;&#1492; &#1489;&#1511;&#1493;&#1491; &#1508;&#1514;&#1493;&#1495;
Comment[hi]=&#2325;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;. &#2319;&#2325; &#2358;&#2325;&#2381;&#2340;&#2367;&#2358;&#2366;&#2354;&#2368;, &#2323;&#2346;&#2344; &#2360;&#2379;&#2352;&#2381;&#2360; &#2330;&#2367;&#2340;&#2381;&#2352;&#2350;&#2351; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;
Comment[hu]=A KDE grafikus munkakörnyezet, egy szabad forráskódú grafikus ablakkezel&#337; környezet
Comment[it]=L'ambiente desktop KDE. Un potente ambiente desktop grafico Open Source
Comment[mn]=The K Desktop Environment. &#1061;&#1199;&#1095;&#1080;&#1088;&#1093;&#1101;&#1075; &#1085;&#1101;&#1101;&#1083;&#1090;&#1090;&#1101;&#1081; &#1101;&#1093; &#1082;&#1086;&#1076; &#1073;&#1199;&#1093;&#1080;&#1081; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1076;&#1101;&#1083;&#1075;&#1101;&#1094;&#1080;&#1081;&#1085; &#1086;&#1088;&#1095;&#1080;&#1085;
Comment[nb]=K Desktop Environment. Et kraftig grafisk skrivebordsmiljø med åpen kildekode.
Comment[nl]=De K Desktop Environment, een krachtige open source grafische desktop environment
Comment[nn]=K Desktop Environment. Eit kraftig grafisk skrivebordsmiljø med open kjeldekode.
Comment[pl]=&#346;rodowisko KDE. Pot&#281;&#380;ne &#347;rodowisko graficzne Wolnego Oprogramowania.Comment[pt]=O K Desktop Environment. Um ambiente gráfico open source poderoso
Comment[pt_BR]=Acrônimo para K Desktop Environment (ou Ambiente de Trabalho K). Um poderoso ambiente de trabalho gráfico de código aberto
Comment[ro]=K Desktop Environment. Un mediu grafic cu surse deschise, foarte puternic
Comment[sk]=The K Desktop Environment. Výkonné, vo&#318;ne šírite&#318;né grafické pracovné prostredie
Comment[sl]=Namizno okolje K. Zmogljivo grafi&#269;no namizno okolje odprte kode
Comment[sr]=K Desktop Environment (KDE). &#1052;&#1086;&#1115;&#1085;&#1086; &#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1082;&#1086; &#1088;&#1072;&#1076;&#1085;&#1086; &#1086;&#1082;&#1088;&#1091;&#1078;&#1077;&#1114;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1086;&#1075; &#1082;&#1086;&#1076;&#1072;
Comment[sv]=K-skrivbordsmiljön. En kraftfull grafisk skrivbordsmiljö med öppen källkod
Comment[ta]= K&#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;. &#2970;&#2965;&#3021;&#2980;&#3007;&#2997;&#3006;&#2991;&#3021;&#2984;&#3021;&#2980; &#2980;&#3007;&#2993;&#2984;&#3021;&#2980; &#2950;&#2979;&#3016;&#2990;&#3010;&#2994; &#2970;&#3007;&#2980;&#3021;&#2980;&#3007;&#2992; &#2997;&#2965;&#3016; &#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;
Comment[tr]=KDE Masaüstü Yöneticisi. Güçlü bir grafiksel masaüstü ortam&#305;
Comment[uk]=The K Desktop Environment. &#1055;&#1086;&#1090;&#1091;&#1078;&#1085;&#1077; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1077; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1077; &#1079; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080;
Comment[uz]=KDE (K Desktop Environment) - &#1082;&#1091;&#1095;&#1083;&#1080; Open Source &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1080;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080; &#1084;&#1091;&#1203;&#1080;&#1090;&#1080;
Comment[vi]=môi tr&#432;&#7901;ng desktop K, môi tr&#432;&#7901;ng desktop &#273;&#7891; ho&#7841; mã ngu&#7891;n m&#7903; r&#7845;t m&#7841;nhComment[xx]=xxThe K Desktop Environment. A powerful Open Source graphical desktop environmentxx
Comment[zh_CN]=K &#26700;&#38754;&#29615;&#22659;&#12290;&#24378;&#22823;&#30340;&#24320;&#25918;&#28304;&#20195;&#30721;&#22270;&#24418;&#26700;&#38754;&#29615;&#22659;
pat@pat-desktop:/usr/share/xsessions$

```

---

### Post by aysiu on 2006-09-25
```
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
``` This is problematic. You should get a fresh sources.list and try again.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by patslap on 2006-09-26
I've followed the howto at [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources), to the part where I update aptitude, which outputs this:

```

pat@pat-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:2 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Ign http://packages.freecontrib.org dapper Release.gpg
Hit http://archive.canonical.com dapper-commercial Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://gb.archive.ubuntu.com dapper-updates Release
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:7 http://packages.freecontrib.org dapper Release [5736B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Get:8 http://packages.freecontrib.org dapper/free Packages [1616B]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Get:9 http://packages.freecontrib.org dapper/non-free Packages [1092B]
Get:10 http://packages.freecontrib.org dapper/free Sources [808B]
Get:11 http://packages.freecontrib.org dapper/non-free Sources [772B]
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Get:12 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:13 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
99% [Waiting for headers] [11 Sources 178/772B 23%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:14 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
99% [14 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [11 Sourcebzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:15 http://security.ubuntu.com dapper-security/multiverse Packages [2185B]
Hit http://security.ubuntu.com dapper-security/main Packages
99% [15 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Get:16 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://archive.ubuntu.com dapper-updates/main Sources
Get:17 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:18 http://security.ubuntu.com dapper-security/universe Packages [18.8kB]
99% [18 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com dapper-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:19 http://gb.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Get:20 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Get:21 http://gb.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
Get:22 http://security.ubuntu.com dapper-security/multiverse Packages [2185B]
99% [21 Packages bzip2 0] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages - open (2 No such file or directory)
99% [22 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:23 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Fetched 10.1kB in 0s (11.4kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
pat@pat-desktop:~$
```

I'm not sure whther to follow the next part in the howto:> Apparently, some people have been experiencing errors even after following this tutorial. There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

Back up the sources.list you got from this tutorial with this command: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

Then edit the sources.list by typing sudo nano /etc/apt/sources.list and delete everything.

sudo aptitude update with your empty repositories list.

Finally, sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update

as I dont't know what a GPG signature error is, and besides, this looks like an error related to bzip2. Should I follow this, too?

---

### Post by aysiu on 2006-09-26
I'm seeing a gb.archive.ubuntu.com and duplicate sources warning, which means that you're **adding** to your sources.list instead of **replacing** your sources.list.

You have to erase everything you already have... and *then* paste in the sources specified.

---

### Post by patslap on 2006-09-26
Nope -I definitely deleted the sources.list and pasted into blank document.

Here's a copy of my current sources.list
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```

I double checked by following the howto a second time, but the error was recreated.

---

### Post by aysiu on 2006-09-26
That's weird.

Maybe you should try that workaround at the bottom of the page--clear out lingering repository information.

---

### Post by patslap on 2006-09-26
Woohoo! Got KDE up-and-running. It's so much more satisfying when you have had to struggle at something for a while before getting it working!

I followed the workaround for clearing out lingering repository information in the sources.list as described at [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources"), but still got error messages about duplicates, so I typed: ```
sudo apt-get update
```and then followed the information described at [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)[]("http://www.psychocats.net/ubuntu/kde.html") and hey presto! When I logged out KDE was available in the session manager!

I have experienced a glitch in KDE desktop when i moved mouse pointer to right-hand side of desktop and about one inch of the right-hand side of the screen corrupted. When i pushed the mouse pointer into the corrupted area, the desktop returned to normal. I haven't replicated this error but will post back if I do.

Thanks for your help and advice, aysiu. :KS 

patslap.

---

### Post by crokett on 2006-09-27
I decided I don't need KDE all that much.  I followed the how-to at psychocats.  Started the install and during the install my machine hung.  Twice.  So then each time had to run dpkg to reconfigure the repositories because they were all whacked out.

---

### Post by patslap on 2006-09-27
Crokett - did you try following, as per [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

> Apparently, some people have been experiencing errors even after following this tutorial. There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

Back up the sources.list you got from this tutorial with this command: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

Then edit the sources.list by typing sudo nano /etc/apt/sources.list and delete everything.

sudo aptitude update with your empty repositories list.

Finally, sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update 

and then 
```
sudo apt-get update
```

because this worked fine for me

---

