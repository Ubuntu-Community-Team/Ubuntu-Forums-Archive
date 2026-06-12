---
title: "[SOLVED] KDE and Ubuntu.."
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-06-22
HI,
do I have to get Kubuntu to run a KDE Desktop environment or is it possible to have KDE in a Ubuntu installation? I want to get used to the GNOME desktop but I would like to have the posibility to switch back and forth.
Thanks in advace
Juergen

---

### Post by aysiu on 2006-06-22
You can switch back and forth as you please. Instructions:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by user1397 on 2006-06-22
[quote=aysiu]You can switch back and forth as you please. Instructions:
[http://www.psychocats.net/ubuntu/kde.html]("http://www.psychocats.net/ubuntu/kde.html")[/quote]aysiu!  i'm surprised at you for the first time!  at the end of that guide, it says that if you want to rmove kde, you would go back to the terminal and type **sudo aptitude remove kubuntu-desktop**, but wouldn't you have to first do **sudo aptitude update**?

---

### Post by aysiu on 2006-06-22
I don't believe you do--that hasn't been my experience, anyway.

The *sudo aptitude update* is crucial before the *install* but not necessary before the *remove*.

---

### Post by user1397 on 2006-06-22
[quote=aysiu]I don't believe you do--that hasn't been my experience, anyway.

The *sudo aptitude update* is crucial before the *install* but not necessary before the *remove*.[/quote]ah i get it now...

---

### Post by Cariboo1938 on 2006-06-25
Thank you [COLOR="Magenta"]aysiu[/COLOR].
I checked the link and it explained all I wanted to know.....though,
I have another querstion: I have installed Libranet 3.0 and I want to switch to Ubuntu. When I installed Libranet, I partitioned my hard drive in that way that I created separate partitions for
/, Swap, Boot, Home, Usr and Var. I would like to do the same when I install Ubuntu. Or does the Ubuntu installer recognize these partitions?
Juergen:-k

---

### Post by sean_ on 2006-06-25
[QUOTE=Cariboo1938]HI,
do I have to get Kubuntu to run a KDE Desktop environment or is it possible to have KDE in a Ubuntu installation? I want to get used to the GNOME desktop but I would like to have the posibility to switch back and forth.
Thanks in advace
Juergen[/QUOTE]

No, you don't.

>  Other Desktop Environments
[edit]
How to install KDE

    * Read #General Notes
    * Read #How to add extra repositories
    * You may also look at some KDE Screenshots 

sudo apt-get install kubuntu-desktop

    Note: This installation will require ~400MB of disk space 

    * System -> Log Out -> Log Out
    * To log in to KDE click on Sessions and choose KDE 

[edit]
How to install XFCE

    * Read #General Notes
    * Read #How to add extra repositories
    * You may also look at some XFCE Screenshots 

sudo apt-get install xubuntu-desktop

    * System -> Log Out -> Log Out
    * To log in to XFCE click on Sessions and choose XFCE 

[edit]


[http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments](http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments) Is the full page.

---

### Post by aysiu on 2006-06-25
I would strongly recommend against using *apt-get* to install any desktop environment.

The proper commands would be ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` This allows for easy removal later, should you wish to do so.

---

### Post by thunderduck3141 on 2006-06-26
asiyu, when did you join the ubuntu community? Just wondering because it seems as if you have been here for quite some time. I joined at breezy

---

### Post by aysiu on 2006-06-26
[QUOTE=thunderduck3141]asiyu, when did you join the ubuntu community? Just wondering because it seems as if you have been here for quite some time. I joined at breezy[/QUOTE]
I joined at Hoary in May 2005. That's when I started using Ubuntu, and it was about a month after I started using Linux (Mepis was my first distro).

---

### Post by bruce89 on 2006-06-26
Funny though, as I started on the forums in April 2005, but wasn't very active in the forums 'til last month really.  I had used Warty for a few days, and decided to use Hoary (unstable at the time) to get my modem (Speedtouch) to work.

---

### Post by krokodil on 2006-06-26
[QUOTE=aysiu]I would strongly recommend against using *apt-get* to install any desktop environment.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` 
[/QUOTE]

What's the difference? I thought aptitude was just a front end for apt, same as synaptic.

---

### Post by aysiu on 2006-06-26
[QUOTE=krokodil]What's the difference? I thought aptitude was just a front end for apt, same as synaptic.[/QUOTE]
There is a big difference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by JonRohan on 2006-06-26
[QUOTE=aysiu]There is a big difference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)[/QUOTE]

A very interesting article. Thanks. :KS

---

### Post by Cariboo1938 on 2006-08-16
> **aysiu said:**
> I would strongly recommend against using *apt-get* to install any desktop environment.
The proper commands would be ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` This allows for easy removal later, should you wish to do so.
Hello aysui,
maybe you remember, when I asked about changing desktop environments in Ubuntu. When I asked this I still had Libranet installed and there I was used to change desktops via the session button. Because of the unclear situation about Libranet I installed Ubuntu and I read your very detailed instructions at ([www.psychocats.net/ubuntu/kde.html](www.psychocats.net/ubuntu/kde.html)), how to get KDE to work with Ubuntu. I think I did every thing as you described. Here is the installed-list of packages concerning KDE:> 
kwin: The KDE window manager...
konsole: X terminal emulator for KDE...
konqueror: Konqueror is the file manager for the K Desktop Environment
klogd: The klogd daemon listens to kernel message sources...
klibc-utils: small statically-linked utilities built with klibc...
kicker: Kicker provides the KDE panel on your desktop...
kgohstview: KGhostview is KDE's PostScript viewer...
kfind: File/Directory-find utility for KDE...
kdesktop: Miscellaneous binaries and files for the KDE desktop...
kdemultimedia-kio-plugins: Enables the browsing of audio CDs under Konqueror...
kdelibs-data: Core shared data for all KDE applications...
kdelibs-bin: Core shared data for all KDE applications...
kdelibs4c2a: Core libraries for all KDE applications...
kdebase-kio-plugins: Core I/O slaves for KDE...
kdebase-data: Shared data files for the KDE base module...
kdebase-bin: Shared data files for the KDE base module...
kcontrol: The KDE Control Center provides you...
libkonk4: Core libraries for Konqueror...
libkcddb1: core libraries for Konqueror...
 Are some missing?..because KDE does not show up in the session menu. Do you have an idea, what could have gone wrong? Shall I do the same steps again? Would I have to uninstall these packages first? Thanks for taking time to read this! Any idea?
Cariboo

---

### Post by aysiu on 2006-08-17
So you're saying those are the only packages that got installed from the commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```?

---

### Post by Cariboo1938 on 2006-08-18
> **aysiu said:**
> So you're saying those are the only packages that got installed from the commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```?I'm saying, that I listed these packages, because all of them showed some kind of a hint towards KDE. Though, I'm not sure if these are the only packages I got when I used the above commands. If I got any other packages I would not have recognized them as a result of this update.

---

### Post by aysiu on 2006-08-18
Can you post the output (all of it) of those two commands?

---

### Post by Cariboo1938 on 2006-08-18
> **aysiu said:**
> Can you post the output (all of it) of those two commands?Hello aysiu, sorry for beeing late...here are the terminal printouts:
> owner@Owner-Desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Packages
Fetched 5B in 4s (1B/s)
Reading package lists... Done
and
> owner@Owner-Desktop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-ppp
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode libgadu3
  libgpgme11 libimlib2 libjpeg-progs libkcal2b libkdepim1a libkexif1
  libkipi0 libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1
  libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a liboggflac3
  libpoppler1-qt libpythonize0 libqt-perl librsync1 libruby1.8
  libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a
  libungif4g ncompress ocrad poster postfix procmail psutils
  pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex rdiff-backup resolvconf ruby ruby1.8
  scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant zoo
**[COLOR="Purple"]The following packages have been kept back:[/COLOR]**
  imagemagick libkrb53 libmagick9
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libgadu3 libgpgme11 libimlib2 libjpeg-progs libkcal2b
  libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1
  libmimelib1c2a liboggflac3 libpoppler1-qt libpythonize0 libqt-perl
  librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1
  libtdb1 libtunepimp2c2a libungif4g ncompress ocrad poster postfix
  procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup resolvconf
  ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools
  wlassistant zoo
0 packages upgraded, 150 newly installed, 0 to remove and 3 not upgraded.
Need to get 120MB/121MB of archives. After unpacking 401MB will be used.

[B][COLOR="Purple"]The following packages have unmet dependencies:
  gnome-ppp: Conflicts: resolvconf but 1.34ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:[/COLOR][/B]

Install the following packages:
fetchmail [6.3.2-2ubuntu2 (dapper)]

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
postfix [Not Installed]
resolvconf [Not Installed]

Score is -7

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  imagemagick libkrb53 libmagick9
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
owner@Owner-Desktop:~$
I got [COLOR="DarkOrchid"]**the highlighted mesages**[/COLOR], when I for the first time did the update and install.

---

### Post by aysiu on 2006-08-18
Dependency/conflicting package problems usually stem from conflicting repositories.

Can you [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources) and then try again?

---

### Post by teet on 2006-08-19
> **aysiu said:**
> I would strongly recommend against using *apt-get* to install any desktop environment.

The proper commands would be ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` This allows for easy removal later, should you wish to do so.

THANK YOU!  Sorry for this semi-random post.  I just happened to be browsing through the forums when I stumbled upon this thread.  I never knew that there was a difference between aptitude and apt-get.  I had noticed that a few members always used 'aptitude' isntead of 'apt-get' when posting install instructions and I always thought they were just being a bit pompous (no seriously, I did...doesn't 'aptitude' seem so much more haughty than 'apt-get'?).  But I digress.  I always hated how when I wanted to test out a new program that required a bunch of dependencies (e.g. a KDE program that requires 100mb worth of KDE libraries) I always had to manually uninstall the dependencies if I decided to remove the program.

I am by no means a new Ubuntu or Linux user.  I've been toying around with linux since Redhat 9 and have installed every version of Ubuntu since warty (I didn't use warty or hoary that much however).  Why has it taken me this long to stumble upon this fact?  I assume most other people don't know about this either...maybe it could be publicized better somehow?

-teet

---

### Post by chadwick359 on 2006-08-19
I think that article on aptitude vs apt-get was a bit unfair. The command sudo apt-get remove --purge command would also remove deps of the package.
A bit off topic, but I am trying to sort out KDE hijacking Gnome settings on a hybrid install.

---

### Post by aysiu on 2006-08-19
> **chadwick359 said:**
> I think that article on aptitude vs apt-get was a bit unfair. The command sudo apt-get remove --purge command would also remove deps of the package.
A bit off topic, but I am trying to sort out KDE hijacking Gnome settings on a hybrid install.
Actually, it doesn't. *apt-get remove --purge* just gets rid of the configuration files. Nice try, though. ```
username@ubuntu:~$ man apt-get
Reformatting apt-get(8), please wait...
username@ubuntu:~$ sudo apt-get update && sudo apt-get install kword
Password:
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://packages.freecontrib.org dapper Release.gpg
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://packages.freecontrib.org dapper Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Ign http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Ign http://packages.freecontrib.org dapper/non-free Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 5B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  koffice-data koffice-libs kspread kword-data libruby1.8 libwv2-1c2
Suggested packages:
  koffice-doc-html wordnet tetex-extra
Recommended packages:
  openoffice.org-mimelnk kghostview latex-xft-fonts ruby
The following NEW packages will be installed:
  koffice-data koffice-libs kspread kword kword-data libruby1.8 libwv2-1c2
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.1MB of archives.
After unpacking 34.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com dapper-security/main libruby1.8 1.8.4-1ubuntu1.1 [1420kB]
Get:2 http://archive.ubuntu.com dapper/main koffice-data 1:1.5.0-0ubuntu9 [748kB]
Get:3 http://archive.ubuntu.com dapper/main koffice-libs 1:1.5.0-0ubuntu9 [2315kB]
Get:4 http://security.ubuntu.com dapper-security/main libwv2-1c2 0.2.2-5ubuntu0.1 [225kB]
Get:5 http://archive.ubuntu.com dapper/main kspread 1:1.5.0-0ubuntu9 [2276kB]
Get:6 http://archive.ubuntu.com dapper/main kword-data 1:1.5.0-0ubuntu9 [1590kB]
Get:7 http://archive.ubuntu.com dapper/main kword 1:1.5.0-0ubuntu9 [2522kB]
Fetched 11.1MB in 1m16s (145kB/s)
Selecting previously deselected package koffice-data.
(Reading database ... 100599 files and directories currently installed.)
Unpacking koffice-data (from .../koffice-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package libruby1.8.
Unpacking libruby1.8 (from .../libruby1.8_1.8.4-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package koffice-libs.
Unpacking koffice-libs (from .../koffice-libs_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package kspread.
Unpacking kspread (from .../kspread_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5ubuntu0.1_i386.deb) ...
Selecting previously deselected package kword-data.
Unpacking kword-data (from .../kword-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.5.0-0ubuntu9_i386.deb) ...
Setting up koffice-data (1.5.0-0ubuntu9) ...

Setting up libruby1.8 (1.8.4-1ubuntu1.1) ...

Setting up koffice-libs (1.5.0-0ubuntu9) ...

Setting up kspread (1.5.0-0ubuntu9) ...

Setting up libwv2-1c2 (0.2.2-5ubuntu0.1) ...

Setting up kword-data (1.5.0-0ubuntu9) ...

Setting up kword (1.5.0-0ubuntu9) ...

username@ubuntu:~$ sudo apt-get remove --purge kword
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  kword*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 7000kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102370 files and directories currently installed.)
Removing kword ...
Purging configuration files for kword ...
username@ubuntu:~$
```

---

### Post by Cariboo1938 on 2006-08-19
> **aysiu said:**
> Dependency/conflicting package problems usually stem from conflicting repositories.

Can you [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources) and then try again?I got a fresh sources.list but when I went back to the terminal I found this warning:
> owner@Owner-Desktop:~$  gksudo gedit /etc/apt/sources.list

(gedit:8590): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
owner@Owner-Desktop:~$
How serious is it? Can I go on to update and install??

---

### Post by aysiu on 2006-08-19
It's not serious at all unless Gedit didn't open:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Cariboo1938 on 2006-08-21
> **aysiu said:**
> It's not serious at all unless Gedit didn't open:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)Hello aysiu,
gedit did open and I certainly have a new soures.list, Thank you so far. I tried ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```again 
and unfortunately I still have [COLOR="DarkOrchid"]**a gzip error, a broken package and  this dependency conflict**[/COLOR] as you can see in the terminal printout:
> owner@Owner-Desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper 
.
.
.
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [108kB]
[COLOR="DarkOrchid"][B]99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 1m2s (0B/s)
Reading package lists... Done[/B][/COLOR]
owner@Owner-Desktop:~$

owner@Owner-Desktop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

[COLOR="DarkOrchid"][B]The following packages are BROKEN:
  gnome-ppp
[/B][/COLOR]
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags flac gtk2-engines-gtk-qt
  gwenview kaddressbook kaffeine kaffeine-xine karm katapult kate kaudiocreator kcron
  kde-guidance kde-style-lipstik kde-systemsettings.....
.
.
.
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags flac gtk2-engines-gtk-qt
  gwenview kaddressbook kaffeine kaffeine-xine karm katapult kate kaudiocreator kcron
  kde-guidance kde-style-lipstik kde-systemsettings.....
.
.
.
  skim speedcrunch ssl-cert vorbis-tools wlassistant zoo
0 packages upgraded, 150 newly installed, 0 to remove and 0 not upgraded.
Need to get 120MB/121MB of archives. After unpacking 401MB will be used.

[COLOR="DarkOrchid"][B]The following packages have unmet dependencies:
  gnome-ppp: Conflicts: resolvconf but 1.34ubuntu2 is to be installed.
Resolving dependencies...[/B][/COLOR]

The following actions will resolve these dependencies:
Install the following packages:
fetchmail [6.3.2-2ubuntu2 (dapper)]

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
postfix [Not Installed]
resolvconf [Not Installed]

Score is -7

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
owner@Owner-Desktop:~$Do you still have the patience to help again? I always appreciate your excellent informations!:KS

---

### Post by dabbner on 2006-08-21
> **aysiu said:**
> I would strongly recommend against using *apt-get* to install any desktop environment.

The proper commands would be ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` This allows for easy removal later, should you wish to do so.

What's the difference between aptitude and apt-get? sorry if that's a silly question... still gettin over my noobness...

---

### Post by Cariboo1938 on 2006-08-21
> **dabbner said:**
> What's the difference between aptitude and apt-get? sorry if that's a silly question... still gettin over my noobness...Hi dabbner,
somebody asked this question already in this thread and the answer you can find here:```
Originally Posted by **aysiu**
There is a big difference:
http://www.psychocats.net/ubuntu/aptitude
```

---

### Post by aysiu on 2006-08-21
> **dabbner said:**
> What's the difference between aptitude and apt-get? sorry if that's a silly question... still gettin over my noobness...
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Cariboo1938 on 2006-08-22
> **Cariboo1938 said:**
> Hello aysiu,
gedit did open and I certainly have a new soures.list, Thank you so far. I tried ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```again 
and unfortunately I still have [COLOR="DarkOrchid"]**a gzip error, a broken package and  this dependency conflict**[/COLOR] as you can see in the terminal printout:
Do you still have the patience to help again? I always appreciate your excellent informations!:KSHello aysiu, 
I'm still not able to run KDE desktop. After your last reply I tried it again whith a new sources.list but it didn't work. You can see the details in a terminal printout on page #26 of  this thread. 
I'm worried that something is wrong whith my installation. 
I hope the issue didn't escape your attention!? 
Cariboo

---

### Post by aysiu on 2006-08-22
I don't really know what that gzip error is, and it seems weird that after a fresh sources.list you'd still get a dependency error.

Did you manually install *gnome-ppp*, or is that from the regular Dapper repositories?

---

### Post by Cariboo1938 on 2006-08-23
> **aysiu said:**
> I don't really know what that gzip error is, and it seems weird that after a fresh sources.list you'd still get a dependency error.

Did you manually install *gnome-ppp*, or is that from the regular Dapper repositories?I had to install gnome-ppp manually. It took me a while until I got my hardware Modem (Topic Chipset) working. I found gnome-ppp and kppp in Synaptic Package Manager, selected it there to install it. First I tried kppp, but this was so terribly slow, so that I uninstalled it. From the connection point of view, gnome-ppp works fine.

---

### Post by Cariboo1938 on 2006-08-24
> **aysiu said:**
> I don't really know what that gzip error is, and it seems weird that after a fresh sources.list you'd still get a dependency error.
Did you manually install *gnome-ppp*, or is that from the regular Dapper repositories?Hello aysiu, 
I didn't hear from after my post #32, but I don't know, who else could help me with this KDE/Ubuntu issue, when not you!
Do you want to see the fresh sources.list? 
Is there a special Forum for interpretaion of error messages? 
Shall I open a new thread?

---

### Post by aysiu on 2006-08-24
Well, the reason I asked if you installed *gnome-ppp* manually is that you may have installed too new a version, and that's where you're getting your dependency problems from.

The only way it could work, I think, is that you install the repositories version of *gnome-ppp* instead of what you've got now, but do you need *gnome-ppp* in order to connect to the internet?

P.S. There are plenty of people here who can help. I'm actually just a beginner myself!

---

### Post by Cariboo1938 on 2006-08-24
> **aysiu said:**
> The only way it could work, I think, is that you install the repositories version of *gnome-ppp* instead of what you've got now, but do you need *gnome-ppp* in order to connect to the internet?
I only have a Dial-Up connection, so I think I really need any Peer-to Peer- Protocol. What other possibility would I have to connect to the Internet? Where would I find the repositories of gnome-ppp?
> **aysiu said:**
> Well, the reason I asked if you installed *gnome-ppp* manually is that you may have installed too new a version, and that's where you're getting your dependency problems from. This was the only version  which was available. I had installed kppp, but this was an unacceptable slow  connection. 
> **aysiu said:**
> P.S. There are plenty of people here who can help. I'm actually just a beginner myself! I guess so, but they didn't check in here. So how can I reach them? You certainly are a very advanced and reliable "beginner"; you are the only person who took care of my issue so far. Thank you for that!

---

### Post by aysiu on 2006-08-24
Unfortunately, we've reached the end of my knowledge applicable to this situation. If no one picks up where I left off, please bump this thread again after a day.

---

### Post by Cariboo1938 on 2006-08-24
> **aysiu said:**
> Unfortunately, we've reached the end of my knowledge applicable to this situation. If no one picks up where I left off, please bump this thread again after a day.Thank you a lot for your patience and support!:)

---

### Post by lowey23 on 2006-08-25
Hi, Cariboo1938,

Certainly no expert, but a couple of thoughts I had.

Try using Synaptic. Do the reload, mark all upgrades and apply. If it tells you there are broken packages, there is a "fix broken packages" under "edit".

Second thought, if that doesn't work, perhaps there is still a problem with your sources.list. Fairly unlikely, but maybe you could post it and we can discount that theory.

Cheers

Lowey

---

### Post by Cariboo1938 on 2006-08-25
> **lowey23 said:**
> Hi, Cariboo1938,
Certainly no expert, but a couple of thoughts I had.
Try using Synaptic. Do the reload, mark all upgrades and apply. If it tells you there are broken packages, there is a "fix broken packages" under "edit". Second thought, if that doesn't work, perhaps there is still a problem with your sources.list. Fairly unlikely, but maybe you could post it and we can discount that theory.
Cheers
LoweyHello Lowey, and thanks for checking in! You won't believe it, but I got it running. Not knowing about the possibility you mentioned about "fix broken packages"...(maybe I need more info on that later)...I removed the graphical gnome-ppp and use "pon/poff" in a terminal to connect to the internet. Then I followed aysiu's instructions```
sudo aptitude update
```Here I got the message:> gzip error:
99% [12 Packages gzip 0] [Waiting for headers]                         156B/s 0sgzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
which I ignored and continued with
```
sudo aptitude install kubuntu-desktop
```This time KDE was installed without further errors. After restart I found the KDe Desktop in the " Session Menu". Here is my sources.list wich I used: > ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
I'm still worried about the brocken package 'gnome-ppp' because I would like to have a graphical Dial-Up tool.

---

### Post by lowey23 on 2006-08-25
YAHOO! Good on you for getting it going. It's been a long time coming, hasn't it.

If you don't already have it, I would suggest you install the synaptic package manager.(sudo aptitude install synaptic)

Then use it to uninstall your gnome-ppp app and then reinstall it. If you get the broken package thing again, you may be able to use the broken package feature I mentioned before.

Other than that, I'm out of ideas. Your sources.list looks good, too.

Good luck and cheers

Lowey

---

