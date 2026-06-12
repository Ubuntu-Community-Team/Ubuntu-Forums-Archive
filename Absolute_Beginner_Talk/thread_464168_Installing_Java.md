---
title: "Installing Java?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-04
I've tried almost everything, and I still cannot get Java installed.  
Java is for a game I wanted to play, It's an in browser game.  I was wondering, how do I install it?
I do not know the first thing to installing something.  That was the great thing with windows, easy installs, although it gave quite a risk, it saved time, and MUCH more user friendly.  Wouldn't that be great :) If you could download a file, drag it into a program and let that program install it for you :)!  Off subject.  I wanted to install Java, I've tried before and it never works.  People have suggested things, that do not work.  Im using Firefox, it is a in browser game.  and i know for a fact that people play it on Linux.  All I need, is to install Java.

Information:
1.  Kubuntu 6.10 ( KDE )
2.  FireFox
3.  Java Type?
4.  Command's to install. 
5.  What path? If it's on my desktop, Shouldn't it be like.. 

```

[COLOR="Red"]sudo aptitude-install /home/nic/Desktop/Downloads/FILENAME[/COLOR]

```

How do I do this? =[ I've posted this a few times and never had the problem solved, I thought I'd give more information this time, Thanks!

---

### Post by Kobalt on 2007-06-04
Head [this way]("https://help.ubuntu.com/community/Java") to learn how to install Java.

---

### Post by steeleyuk on 2007-06-04
It should just be a case of entering:

sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin

(the above will install from the repositories)

Edit: changed version numbers for Edgy

---

### Post by nereid on 2007-06-04
Normally java is allready installed, you can install the newest version of sun's java with the following command:

```

sudo aptitude install sun-java6-jre

```

To install the corresponding browser plugin

```

sudo aptitude install sun-java6-plugin

```

To choose the default java runtime use the following commands

```

sudo update-java-alternatives -s java-6-sun

```

This should get your java installation on the bleeding edge ;)

---

### Post by LollYouSuckZor on 2007-06-04
> **steeleyuk said:**
> It should just be a case of entering:

sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin

(the above will install from the repositories)

Edit: changed version numbers for Edgy

nic@nic-desktop:~$ sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java5-bin
nic@nic-desktop:~$

---

### Post by LollYouSuckZor on 2007-06-04
> **nereid said:**
> Normally java is allready installed, you can install the newest version of sun's java with the following command:

```

sudo aptitude install sun-java6-jre

```

To install the corresponding browser plugin

```

sudo aptitude install sun-java6-plugin

```

To choose the default java runtime use the following commands

```

sudo update-java-alternatives -s java-6-sun

```

This should get your java installation on the bleeding edge ;)

```

Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java5-bin
nic@nic-desktop:~$ sudo aptitude install sun-java6-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java6-jre"
The following packages have been automatically kept back:
  kicker linux-image-2.6.17-10-generic linux-image-generic
  linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common linux-restricted-modules-generic
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater avahi-daemon bind9-host dbus digikam
  dnsutils file gnupg info kate kcontrol kdebase-bin kdebase-data
  kdebase-kio-plugins kdelibs-data kdelibs4c2a kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdeprint kdesktop kdm kdnssd kfind
  khelpcenter klipper kmenuedit koffice-data koffice-libs konqueror
  konqueror-nsplugins konsole kopete kpf kppp krdc krfb krita krita-data
  ksmserver ksplash ksysguard ksysguardd ktorrent kwin language-pack-en
  language-pack-kde-en libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1
  libbind9-0 libc6 libc6-dev libc6-i686 libcurl3 libcurl3-gnutls
  libdbus-1-3 libdns21 libfreetype6 libgpgme11 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1 libkonq4
  libkrb53 liblwres9 libmagic1 libmagick++9c2a libmagick9
  libmysqlclient15off libpng12-0 libpq4 libqt3-mt libruby1.8 libsmbclient
  libvolumeid0 libwpd8c2a libx11-6 libx11-data libxfont1 libxine1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic linux-libc-dev mysql-common openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-math openoffice.org-writer
  poppler-utils popularity-contest python-kde3 python-uno ruby1.8
  samba-common screen slocate smbclient tcpdump ttf-opensymbol tzdata udev
  vim-common vim-tiny volumeid w3m wlassistant x11-common xbase-clients
  xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xutils
0 packages upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
nic@nic-desktop:~$ sudo aptitude install sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java6-plugin"
The following packages have been automatically kept back:
  kicker linux-image-2.6.17-10-generic linux-image-generic
  linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common linux-restricted-modules-generic
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater avahi-daemon bind9-host dbus digikam
  dnsutils file gnupg info kate kcontrol kdebase-bin kdebase-data
  kdebase-kio-plugins kdelibs-data kdelibs4c2a kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdeprint kdesktop kdm kdnssd kfind
  khelpcenter klipper kmenuedit koffice-data koffice-libs konqueror
  konqueror-nsplugins konsole kopete kpf kppp krdc krfb krita krita-data
  ksmserver ksplash ksysguard ksysguardd ktorrent kwin language-pack-en
  language-pack-kde-en libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1
  libbind9-0 libc6 libc6-dev libc6-i686 libcurl3 libcurl3-gnutls
  libdbus-1-3 libdns21 libfreetype6 libgpgme11 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1 libkonq4
  libkrb53 liblwres9 libmagic1 libmagick++9c2a libmagick9
  libmysqlclient15off libpng12-0 libpq4 libqt3-mt libruby1.8 libsmbclient
  libvolumeid0 libwpd8c2a libx11-6 libx11-data libxfont1 libxine1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic linux-libc-dev mysql-common openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-math openoffice.org-writer
  poppler-utils popularity-contest python-kde3 python-uno ruby1.8
  samba-common screen slocate smbclient tcpdump ttf-opensymbol tzdata udev
  vim-common vim-tiny volumeid w3m wlassistant x11-common xbase-clients
  xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xutils
0 packages upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
nic@nic-desktop:~$ sudo update-java-alternatives -s java-6-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
nic@nic-desktop:~$      

```

?....

---

### Post by dhruva023 on 2007-06-04
use automatix

---

### Post by LollYouSuckZor on 2007-06-04
I'd try too, but im not sure how..  I dont know what automatix is.

---

### Post by LollYouSuckZor on 2007-06-04
Nevermind :) Installing 

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_i386.29)


Last step of installation.  :) Hope this works.

---

### Post by lazyart on 2007-06-04
Before you use automatix, check that you have the multiverse respository enabled.

System>Administration>Synaptic Package Manager>Settings>Repositories

Multiverse is the fourth selection (you're using Feisty, correct?).

---

### Post by LollYouSuckZor on 2007-06-04
> **lazyart said:**
> Before you use automatix, check that you have the multiverse respository enabled.

System>Administration>Synaptic Package Manager>Settings>Repositories

Multiverse is the fourth selection (you're using Feisty, correct?).

No im not.  Im using Kubuntu Egdy 6.10...
I dont have any of the System>Admin thing.  I gave up on the GNOME desktop after it crashed my computer.

---

### Post by LollYouSuckZor on 2007-06-04
Im dieing to play my game =[

---

### Post by LollYouSuckZor on 2007-06-04
Anyone... =[

---

### Post by aldreis on 2007-06-04
> **LollYouSuckZor said:**
> No im not.  Im using Kubuntu Egdy 6.10...

Look for **Adept** ( instead of Synaptic ) and check what lazyart asked of you.

---

### Post by santy_kushwaha on 2007-06-04
their is another way easier 

go to the java website and instal the file and follow the instructions carefully ( file name given in instruction is different from the download file ) login as root then do that it will be easier.

i did tried the suggestion given by others but didn't work well so i tried the instructions given on java site and it works like a charm 

hope u will be able to do that

---

### Post by nereid on 2007-06-05
Sorry, but I overread that you still use 6.10.

---

### Post by LollYouSuckZor on 2007-06-05
Thanks :) I got it working.

---

