---
title: "desktop screwed"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2007-03-14
ok.. i was messing around with ubuntu,, n.. i think i updated it somehow.. (from the 6.06) cuz now it kinda looks all different.. the fonts r smaller and it looks cool :)
but.. everytime i open ubuntu.. i get an error abt some gnome-daemon something not loading..
now cuz of that.. i cant see my desktop (i get no icons) i cant used the natilus and i keep getting big buddy loading and i cant figure out a way to tell what the bug is.. and if i close bug buddy.. it comes back again..
what do i do? :(

---

### Post by AtrejuT on 2007-03-14
do you have internet access on that machine? Then I'd first try going to a terminal (Ctrl+Alt+F1), logging in and doing 

```

sudo apt-get update
sudo apt-get upgrade

```

also let me know what
```

uname -a

```
gives

atreju

---

### Post by MikeSz on 2007-03-14
Hi Nightwolf - I did a similar thing to mine last night - I installed the KDE environment, changed the font and downloaded some plug-ins for one of the web content programs (cant remember which)  Now, whenever I try to go into GNOME, it tells me that my trash applet is missing (and about 3 others for that matter) and nothing will open now.  When I click on firefox, the mouse timer just sits there for 30 seconds and nothing happens.  Looks like ive broken it!

---

### Post by j.miller565 on 2007-03-14
Hi MikeSz
I suggest creating another account just for GNOME and keep the other one as KDE, so that they don't interfere with each other. This should sort out that problem if you still want to use GNOME. Anyway, you will most likely  just end up using 1 or the other, so you will totally forget about using one of them.

---

### Post by MikeSz on 2007-03-14
Thanks for that J.Miller - I hadnt thought of that - I was going to do a fresh install from scratch for the 64 bit version as I only have the basic non-AMD64 version on at the mo (I have only been using Ubuntu for a week or two so havent really got anything on there I cant get back again fairly quickly - ive just been getting used to it really) but I imagine that will work just as well!  Wont that mean that all my files need moving from my home directory to the new one?

---

### Post by j.miller565 on 2007-03-14
yea that's the only problem. You could always create a link into another home directory by using 

```
sudo -s -H
``` (Now you are using root)

and then

```
nautilus or konqueror 
```    depending on what file manger you use. Firstly you have to type /home/ in thhe address/location bar to get you to the home directory. Then right click on the home directory you want to make a link to and then put it into your home directory you are using now. I hope this helps too :)

---

### Post by nightwolf2k5 on 2007-03-14
when i typed sudo apt-get update
```
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Get:2 http://archive.canonical.com edgy-commercial Release.gpg [191B]
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://www.getautomatix.com dapper Release
Hit http://archive.canonical.com edgy-commercial Release
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com edgy-commercial/main Packages
Get:4 http://archive.ubuntu.com edgy Release.gpg [191B]
Get:5 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial/main Packages
Get:6 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Get:7 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:8 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:9 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:10 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/universe Sources
Get:11 http://security.ubuntu.com edgy-security Release.gpg [191B]
Hit http://security.ubuntu.com edgy-security Release
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/multiverse Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Fetched 11B in 8s (1B/s)

```
when i typed sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  alacarte apt apt-utils aptitude at-spi bicyclerepair bluez-cups
  bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11 bug-buddy
  capplets-data contact-lookup-applet cupsys cupsys-bsd cupsys-client
  debianutils deskbar-applet ekiga evolution evolution-data-server
  evolution-exchange evolution-plugins evolution-webcal firefox
  firefox-gnome-support fontconfig gaim gaim-data gcj-4.1-base gedit
  gedit-common gij-4.1 gksu gnome-accessibility-themes gnome-app-install
  gnome-applets gnome-applets-data gnome-control-center gnome-doc-utils
  gnome-mag gnome-media gnome-menus gnome-panel gnome-panel-data
  gnome-panel-dbg gnome-pilot gnome-pilot-conduits gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-themes gnopernicus gok grub gs-esp
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8
  gucharmap hal-device-manager hpijs initramfs-tools initscripts irssi
  java-gcj-compat libatspi1.0-0 libcamel1.2-8 libdmx1 libedata-book1.2-2
  libedataserver1.2-7 libeel2-2 libeel2-data libfontconfig1 libgail-common
  libgcj-common libgcj7-jar libgl1-mesa-dri libglib-perl libgnome2-perl
  libgnome2-vfs-perl libgnomebt0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15
  libgtop2-7 libmetacity0 libperl5.8 libpisync0 libsexy2 libsnmp9
  libtext-charwidth-perl libtext-iconv-perl libvte-common libwxgtk2.6-0
  libx11-6 libxdmcp6 libxfixes3 libxft2 libxt6 linux-image-386
  linux-restricted-modules-386 locales metacity mozilla-firefox-locale-en-gb
  nautilus nautilus-cd-burner nautilus-sendto notification-daemon
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-math openoffice.org-writer parted pciutils perl perl-base
  perl-modules python python-adns python-apt python-cddb python-clientcookie
  python-crypto python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs
  python-examples python-gadfly python-gdbm python-genetic python-geoip
  python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnupginterface python-gst0.10 python-gtk2
  python-htmlgen python-htmltmpl python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-ldap python-libxml2 python-minimal
  python-mysqldb python-netcdf python-newt python-numeric python-pam
  python-parted python-pexpect python-pgsql python-pisock python-pylibacl
  python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-unit python-uno python-vte python-xdg
  python-xml python-xmpp python2.4 python2.4-dev python2.4-examples
  python2.4-minimal rhythmbox rhythmbox-dbg serpentine sound-juicer synaptic
  system-tools-backends sysvinit totem ubuntu-artwork udev update-manager
  whiptail x-window-system-core x11-common xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xfonts-utils xkeyboard-config xserver-xorg
  xserver-xorg-core xserver-xorg-driver-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xterm xutils
The following packages will be upgraded:
  hplip-data
1 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.
Need to get 6276kB of archives.
After unpacking 295kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main hplip-data 1.6.9-0ubuntu2 [6276kB]
Fetched 6276kB in 14m25s (7250B/s)
(Reading database ... 108370 files and directories currently installed.)
Preparing to replace hplip-data 0.9.7-4ubuntu1 (using .../hplip-data_1.6.9-0ubuntu2_all.deb) ...
Unpacking replacement hplip-data ...
Setting up hplip-data (1.6.9-0ubuntu2) ...

```

---

### Post by MikeSz on 2007-03-14
Thats great - thanks J.miller, il have a go with that tonight.

---

### Post by j.miller565 on 2007-03-14
No problems, always a pleasure to help :)

sorry nightwolf, I dunno what do to with your situation

---

### Post by nightwolf2k5 on 2007-03-14
somebody please help me :(

i just checked... n.. apparently i got ubuntu 6.10!! now don ask me how i ended up with ubuntu 6.10 from 6.06

---

### Post by MikeSz on 2007-03-14
Thanks J,Miller - your tip worked a treat!

---

### Post by nightwolf2k5 on 2007-03-15
problem sorted out..

---

### Post by MikeSz on 2007-03-15
what was it?

---

