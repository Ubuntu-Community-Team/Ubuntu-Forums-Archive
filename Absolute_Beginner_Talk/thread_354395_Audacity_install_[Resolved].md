---
title: "Audacity install [Resolved]"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by bullpen7979 on 2007-02-05
Let me know if I have this right. Fairly new (ok, real new) to linux, My issue with the OS in general was that it's hard to install programs. (K)ubuntu looked like it might be a bit easier...so I go to the ubuntu package page, and there's audacity. when I pull up the 
download page : [http://packages.ubuntu.com/edgy/sound/audacity](http://packages.ubuntu.com/edgy/sound/audacity), if I interpret what I see correctly, there are 13 dependencies and one suggested package to install. So, to properly install audacity, I have to download and install all 13 packages?? Am I missing something? Please if there's an easier way to install programs under Kubuntu, could somebody tell me what that would be? Thanks, and sorry for the terribly simplistic question....

---

### Post by punx45 on 2007-02-05
yeah, synaptic package manager...

there is a gui version (not sure where to find it in KDE, look in the menu for add and remove programs or something like that) you can open that up and then search for audacity and tell it to install it (and it will install all the dependencies on its own)

or in a terminal you can do:

```
sudo apt-get install audacity
```

which will do the same thing.

-------
PS

you will still have to get the LAME library in order to encode MP3, but that is easier, you just have to download it and tell audacity where it is.

---

### Post by closetpirate on 2007-02-05
K menu ->System->Adept Package Manager
type password

search audacity (watch your spelling)
request change to install and you have audacity!

---

### Post by bullpen7979 on 2007-02-06
ok, did what you said, but when i right click and request install, it does not change the status line......I right clicked and installed a menu editor, and that went fine, but for some reason, audacity isn't budging....any idea why this would be the case....

---

### Post by wildseven on 2007-02-06
sudo aptitude install audicity

that should work.



-seven

---

### Post by bullpen7979 on 2007-02-06
Either I'm completely remedial, or this OS is just too much of a pain to be useful. In konsole, I type 
sudo aptitude install audacity
(enter password) 
and I get this: 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for audacity
The following packages have been automatically kept back:
  kicker linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common
The following packages have been kept back:
  avahi-daemon bind9-host dbus dnsutils gnupg info kate kcontrol kdebase-bin kdebase-data
  kdebase-kio-plugins kdelibs-data kdelibs4c2a kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdeprint kdesktop kdm kdnssd kfind khelpcenter klipper kmenuedit koffice-data
  koffice-libs konqueror konqueror-nsplugins konsole kopete kpf kppp krdc krfb krita krita-data
  ksmserver ksplash ksysguard ksysguardd kwin language-pack-en language-pack-kde-en
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1
  libavahi-core4 libavahi-qt3-1 libbind9-0 libc6 libc6-dev libc6-i686 libdbus-1-3 libdns21
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1 libkonq4
  libkrb53 liblwres9 libmagick++9c2a libmagick9 libpng12-0 libpoppler1 libpoppler1-qt libpq4
  libruby1.8 libsmbclient libvolumeid0 libxine1 linux-headers-2.6.17-10
  linux-headers-2.6.17-10-generic linux-libc-dev openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde openoffice.org-math
  openoffice.org-style-crystal openoffice.org-style-default openoffice.org-writer poppler-utils
  python-uno ruby1.8 samba-common screen smbclient tar ttf-opensymbol tzdata udev volumeid w3m
  wlassistant x11-common xbase-clients xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-video-all xutils
0 packages upgraded, 0 newly installed, 0 to remove and 116 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Although having an admittedly untrained eye for this stuff, it still smells of failure to install. Tell me this OS gets easier, because right now, the learning curve looks pretty steep. 

Any suggestions here as to why this installing a simple program has taken 24 hours and 5 posts on a message board??? (Frustration leaking out......) thanks for assistance, list...

---

### Post by punx45 on 2007-02-06
audacity is in the universe repositories, which you may need to be enabled.

[see this guide]("http://www.psychocats.net/ubuntu/sources") for help on that.

then you should be able to install audacity with either method.

---

### Post by aysiu on 2007-02-06
After you follow punx45's instructions, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bullpen7979 on 2007-02-06
Outstanding. the "enable extra repositories" trick did it. Thanks to you folks, I'm going to stick with the Linux thing, I think.....

---

