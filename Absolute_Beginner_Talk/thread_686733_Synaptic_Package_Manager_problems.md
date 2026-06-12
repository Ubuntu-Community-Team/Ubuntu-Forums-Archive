---
title: "Synaptic Package Manager problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by spoonman1144 on 2008-02-03
I was trying to install the comix package, when i realized that if i try to install any package it says 
dpkg: cant mmap package info file '/var/lib/dpkg/available': no such device
E: sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

Im new at this, and totally lost.

---

### Post by SunnyRabbiera on 2008-02-03
this is usually easy to solve.
try sudo apt-get update in a terminal and see if you get any errors.

---

### Post by spoonman1144 on 2008-02-03
I didnt get any errors

---

### Post by jrusso2 on 2008-02-03
Try running this

sudo dpkg --clean-avail

Then

apt-get update

---

### Post by SunnyRabbiera on 2008-02-03
alright, this is normally nothing to worry about, give synaptic another shot and try installing comix again.
if you get errors please tell me.

> **jrusso2 said:**
> Try running this

sudo dpkg --clean-avail

Then

apt-get update


yes do try this if you get errors.

---

### Post by spoonman1144 on 2008-02-03
after sudo dpkg --clean-avail and sudo apt-get update i get errors
E: could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

i tried installing comix again, same errors

---

### Post by SunnyRabbiera on 2008-02-03
okay, try a restart of your computer...
I am sure we can fix this somehow, I see issues like this often but they are usually fixed quickly.

---

### Post by spoonman1144 on 2008-02-03
i rebooted the computer, tried it again, still the same errors

---

### Post by jan quark on 2008-02-03
try 
```

sudo apt-get -f install
```

this fixes would-be broken packages

---

### Post by SunnyRabbiera on 2008-02-03
okay, well it was worth a shot.
the next thing I can suggest trying is go into a terminal and put in
sudo apt-get upgrade
and see if more errors will crop up.
This kind of error usually comes up from updating, so might I ask did you do any updates before you got this error?

---

### Post by spoonman1144 on 2008-02-03
I did sudo apt-get upgrade:

max@laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data-commercial apt apt-utils avahi-autoipd avahi-daemon azureus
  bind9-host cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet
  dnsutils esound-common evolution-data-server evolution-data-server-common
  gdm ghostscript ghostscript-x gimp gimp-data gimp-python gnome-cards-data
  gnome-games gnome-games-data gs-common gs-esp gs-esp-x hpijs hplip
  hplip-data libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libbind9-30
  libcamel1.2-10 libcupsimage2 libcupsys2 libdb4.4 libdns32 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libesd-alsa0
  libexchange-storage1.2-3 libgimp2.0 libgs8 libisc32 libisccc30 libisccfg30
  liblwres30 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libsnmp-base libsnmp10 libxfont1 libxml2 libxml2-utils
  linux-ubuntu-modules-2.6.22-14-generic network-manager-gnome
  openoffice.org-filter-mobiledev openssh-client python-libxml2
  ssh-askpass-gnome tomboy update-manager update-manager-core
  xserver-xorg-core xserver-xorg-video-intel
78 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.1MB/63.9MB of archives.
After unpacking 3342kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.38 [3056kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main apt 0.7.6ubuntu14.1 [1494kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main apt-utils 0.7.6ubuntu14.1 [199kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main update-manager 1:0.81.2 [885kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main update-manager-core 1:0.81.2 [30.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main app-install-data-commercial 8.4 [13.6kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main esound-common 0.2.38-0ubuntu4.1 [42.3kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gdm 2.20.1-0ubuntu2 [1867kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-games 1:2.20.3-0ubuntu1 [1553kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-games-data 1:2.20.3-0ubuntu1 [11.4MB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-cards-data 1:2.20.3-0ubuntu1 [340kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main network-manager-gnome 0.6.5-0ubuntu11~7.10.0 [138kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main tomboy 0.8.1-0ubuntu1 [2392kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1 [178kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main libesd-alsa0 0.2.38-0ubuntu4.1 [21.9kB]
Fetched 31.1MB in 1m22s (376kB/s)                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by SunnyRabbiera on 2008-02-03
> **spoonman1144 said:**
> I did sudo apt-get upgrade:

max@laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data-commercial apt apt-utils avahi-autoipd avahi-daemon azureus
  bind9-host cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet
  dnsutils esound-common evolution-data-server evolution-data-server-common
  gdm ghostscript ghostscript-x gimp gimp-data gimp-python gnome-cards-data
  gnome-games gnome-games-data gs-common gs-esp gs-esp-x hpijs hplip
  hplip-data libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libbind9-30
  libcamel1.2-10 libcupsimage2 libcupsys2 libdb4.4 libdns32 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libesd-alsa0
  libexchange-storage1.2-3 libgimp2.0 libgs8 libisc32 libisccc30 libisccfg30
  liblwres30 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libsnmp-base libsnmp10 libxfont1 libxml2 libxml2-utils
  linux-ubuntu-modules-2.6.22-14-generic network-manager-gnome
  openoffice.org-filter-mobiledev openssh-client python-libxml2
  ssh-askpass-gnome tomboy update-manager update-manager-core
  xserver-xorg-core xserver-xorg-video-intel
78 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.1MB/63.9MB of archives.
After unpacking 3342kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.38 [3056kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main apt 0.7.6ubuntu14.1 [1494kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main apt-utils 0.7.6ubuntu14.1 [199kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main update-manager 1:0.81.2 [885kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main update-manager-core 1:0.81.2 [30.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main app-install-data-commercial 8.4 [13.6kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main esound-common 0.2.38-0ubuntu4.1 [42.3kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gdm 2.20.1-0ubuntu2 [1867kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-games 1:2.20.3-0ubuntu1 [1553kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-games-data 1:2.20.3-0ubuntu1 [11.4MB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main gnome-cards-data 1:2.20.3-0ubuntu1 [340kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main network-manager-gnome 0.6.5-0ubuntu11~7.10.0 [138kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main tomboy 0.8.1-0ubuntu1 [2392kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1 [178kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main libesd-alsa0 0.2.38-0ubuntu4.1 [21.9kB]
Fetched 31.1MB in 1m22s (376kB/s)                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)

yeh there is a lot of stuff coughed up there.

---

### Post by spoonman1144 on 2008-02-03
basically it ended up giving me the same error that ive been getting

---

### Post by SunnyRabbiera on 2008-02-03
yeh, well keep patient and hopefully you will get some answers.
I can understand this can be frustrating though, but I personally never had to do all kinds of crazy things to get my lists working again

---

### Post by jan quark on 2008-02-03
pls post the result of 

```
cat /etc/apt/sources.list
```

---

### Post by spoonman1144 on 2008-02-03
max@laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main

---

