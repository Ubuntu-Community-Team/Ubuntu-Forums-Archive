---
title: "Install Java? &amp; Flash?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-03
Im using Kubuntu edgy.  I wanted to install Flash player 9, and Java.

Java: [http://java.com/en/download/index.jsp](http://java.com/en/download/index.jsp)

Im not sure which to download, or how to install it, and anytime I type, Su in the console, I get it says that I could not be authenticated..?

---

### Post by jfinkels on 2007-06-03
> **LollYouSuckZor said:**
> Im using Kubuntu edgy.  I wanted to install Flash player 9, and Java.

Java: [http://java.com/en/download/index.jsp](http://java.com/en/download/index.jsp)

Im not sure which to download, or how to install it, and anytime I type, Su in the console, I get it says that I could not be authenticated..?

You can just install them like this:
```
sudo aptitude install sun-java6-jre flashplugin-nonfree
```

---

### Post by LollYouSuckZor on 2007-06-03
That did not work =[

```


Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "flashplugin-nonfree"
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
  samba-common screen slocate smbclient tar tcpdump ttf-opensymbol tzdata
  udev vim-common vim-tiny volumeid w3m wlassistant x11-common
  xbase-clients xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xutils
0 packages upgraded, 0 newly installed, 0 to remove and 144 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
nic@nic-desktop:~$     

```

---

### Post by jfinkels on 2007-06-03
> **LollYouSuckZor said:**
> That did not work =[

```


Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "flashplugin-nonfree"
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
  samba-common screen slocate smbclient tar tcpdump ttf-opensymbol tzdata
  udev vim-common vim-tiny volumeid w3m wlassistant x11-common
  xbase-clients xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xutils
0 packages upgraded, 0 newly installed, 0 to remove and 144 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
nic@nic-desktop:~$     

```

First, run ```
sudo aptitude update && sudo aptitude upgrade
``` to make sure your system is up-to-date.

Second, have you enabled the multiverse and universe repositories? I don't know about **K**ubuntu, but in GNOME Ubuntu, it's under System > Administration > Software Sources. (Or I can help you enable it from the terminal if you need help).

---

### Post by LollYouSuckZor on 2007-06-03
See, I needed the Java for a game.  Last time I did a update like that it completly ruined my computer.  Im lucky I got it fixed.

---

### Post by Inxsible on 2007-06-03
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

```
sudo aptitude install sun-java6-jre
```

---

### Post by LollYouSuckZor on 2007-06-03
Okay, So i've done all of that.  And yet, NOPE.

I go back to the game, and I get the screen from firefox asking me to download the plugin or whatever...

How do I get this to go away so I can play =[

---

### Post by Inxsible on 2007-06-03
Try this.

After your JRE is installed, open a terminal, change to your Mozilla Firefox plugins directory, and issue the following command:
```

ln -s /usr/java/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

```

If you are not using Sun JRE 1.5.0_09, and/or you installed your JRE at a different location, you will need to modify the command accordingly. Do not copy the plugin, otherwise Firefox will crash if you try viewing a page containing a Java applet.

---

### Post by Inxsible on 2007-06-03
For Flash :
Download Macromedia Flash Player 9. Packages are available for many distributions. Once downloaded, copy libflashplayer.so and flashplayer.xpt to your browser's plugins directory. 


[Download Flash Player 9]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4")
[Download Flash Player Packages]("http://macromedia.mplug.org/")

Hope that helps !

---

### Post by jfinkels on 2007-06-04
Did you do ```
sudo aptitude install flashplugin-nonfree
```? If you did and it's still not working, follow the advice given by Inxsible above :D

---

