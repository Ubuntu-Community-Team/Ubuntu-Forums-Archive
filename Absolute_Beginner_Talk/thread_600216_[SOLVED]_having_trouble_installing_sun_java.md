---
title: "[SOLVED] having trouble installing sun java"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-02
how can i install sun java?

i want frostwire, but i cant get it because i dont have sun java, 
and when i want to install it using the synaptic package manager, it says
"Please insert the disk labeled:
Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)
in drive /cdrom/"

i dont have a disk.
is there a way around this?
i just want to be able to install some programs!! ahhhh

---

### Post by Inxsible on 2007-11-02
have you enabled the universe and multiverse repos ?

you probably only need jre and not the jdk.open a terminal and type in```
sudo aptitude install sun-java6-bin
```

---

### Post by dylondadank on 2007-11-02
> **Inxsible said:**
> have you enabled the universe and multiverse repos ?

no, how do i do that?

---

### Post by Inxsible on 2007-11-02
> **dylondadank said:**
> no, how do i do that?
System --> Administration --> Software Sources. Check mark the boxes for universe and multiverse.

---

### Post by Maestro23 on 2007-11-02
> **dylondadank said:**
> no, how do i do that?

System>>Admin>>Software Sources

Make sure Universe and Multiverse are enabled.

---

### Post by dylondadank on 2007-11-02
> **Maestro23 said:**
> System>>Admin>>Software Sources

Make sure Universe and Multiverse are enabled.

they were both checked.

---

### Post by Inxsible on 2007-11-02
> **dylondadank said:**
> they were both checked.and what happens when you enter the command i gave in the terminal?

---

### Post by dylondadank on 2007-11-02
> **Inxsible said:**
> and what happens when you enter the command i gave in the terminal?

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Inxsible on 2007-11-02
make sure you close the synaptic and the add/remove when you use the command. it won't install anything when some other installer is running.

This is so that you don't accidentally install conflicting packages from two different install methods.

---

### Post by dylondadank on 2007-11-02
> **Inxsible said:**
> make sure you close the synaptic and the add/remove when you use the command. it won't install anything when some other installer is running.

This is so that you don't accidentally install conflicting packages from two different install methods.

alright, i closed the package manager, retried it, and it showed this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  file libfreetype6 libgl1-mesa-glx libmagic1 libpng12-0 
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic mesa-utils 
The following NEW packages will be automatically installed:
  gsfonts-x11 sun-java6-jre 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  bsdutils capplets-data dbus dbus-1-utils dnsutils evolution-data-server 
  evolution-data-server-common firefox firefox-gnome-support gimp gimp-data 
  gimp-python gnome-app-install gnome-control-center gnome-panel 
  gnome-panel-data hpijs hplip hplip-data hwdb-client-common 
  hwdb-client-gnome iptables language-pack-en language-pack-gnome-en 
  libbind9-0 libcamel1.2-10 libcurl3 libdbus-1-3 libdns22 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libexif12 libgimp2.0 libgl1-mesa-dri libglu1-mesa 
  libgnome-window-settings1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1 
  libkrb53 liblwres9 libmagick9 libmetacity0 libnspr4 libnss3 
  libpanel-applet2-0 libpoppler1 libpoppler1-glib libslab0 libsmbclient 
  libsndfile1 libssl0.9.8 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 
  linux-generic linux-headers-generic metacity metacity-common mount 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-filter-mobiledev 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer openssl poppler-utils python python-apport 
  python-gdbm python-launchpad-bugs python-minimal python-problem-report 
  python-uno python2.5 python2.5-minimal rdesktop rsync samba-common 
  smbclient sun-java5-bin tar tcpdump ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core util-linux 
  util-linux-locales vim-common vim-tiny xscreensaver-data xscreensaver-gl 
The following NEW packages will be installed:
  gsfonts-x11 sun-java6-bin sun-java6-jre 
0 packages upgraded, 3 newly installed, 0 to remove and 126 not upgraded.
Need to get 0B of archives. After unpacking 93.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by dylondadank on 2007-11-02
alright, i figured it all out.

and i got frostwire to install, but now i cant find where it installed too

---

### Post by Inxsible on 2007-11-02
did you use sudo in front of the command ?

```
sudo aptitude install sun-java6-bin
```

---

### Post by Inxsible on 2007-11-02
> **dylondadank said:**
> alright, i figured it all out.

and i got frostwire to install, but now i cant find where it installed too

you mean how to start it up ?
It should have gone into Applications>>Internet>>Frostwire.

If not, you can create a shortcut and it will be under /usr/bin/

Keep in mind, that this is NOT Windows, and it does not have a application specific install folder or anything like that.

---

