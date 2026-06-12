---
title: "how do i do this then?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-20
How about booting from a live cd, mounting your old root partition on /media/oldroot and doing:
sudo chroot /media/oldroot
then sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

and try sudo dpkg --configure -a

i've mounted my hard drive with my home dir on and my install of 6.10 that screwed up when updating to 7.0.4... so how do i fix that install with the above?
what is meant by "mounting your old root partition" does that mean just the hard drive or the root dir etc?
im so comfused.
im i try the above i get as far as apt-get dist-upgrade then i get
```
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# sudo chroot /media/oldroot
root@ubuntu:/# sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:2 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty/main Translation-en_US
Get:3 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_US
Get:4 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:5 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Hit http://gb.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages
Get:6 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US
Hit http://gb.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Packages
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/main Sources
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-security Release
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty Release
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Fetched 7B in 0s (10B/s)
Reading package lists... Done
root@ubuntu:/# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bluez-pcmcia-support: Depends: bluez-utils (= 3.9-0ubuntu4) but 3.7-1ubuntu4 is installed
  libopenalpp-cvs1: Depends: libopenthreads4 (>= 1.2.0) but it is not installed
E: Unmet dependencies. Try using -f.
root@ubuntu:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bluez-utils libopenthreads4
Suggested packages:
  bluez-firmware
Recommended packages:
  bluez-gnome
The following packages will be REMOVED:
  libopenthreads3
The following NEW packages will be installed:
  libopenthreads4
The following packages will be upgraded:
  bluez-utils
1 upgraded, 1 newly installed, 1 to remove and 389 not upgraded.
311 not fully installed or removed.
Need to get 0B/303kB of archives.
After unpacking 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142036 files and directories currently installed.)
Preparing to replace bluez-utils 3.7-1ubuntu4 (using .../bluez-utils_3.9-0ubuntu4_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libopenthreads3
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins dcraw
  desktop-effects dpatch espeak feisty-gdm-themes feisty-session-splashes
  feisty-wallpapers gdebi-core genisoimage gnome-orca gs-esp-x icedax
  libapache2-mod-php5 libclamav2 libdecoration0 libnss-mdns libopenobex1
  libopenthreads4 libusplash0 libxcomposite1 libxine1-ffmpeg
  linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic
  linux-headers-generic linux-image-2.6.20-15-386
  linux-restricted-modules-2.6.20-15-386 mscompress onboard openprinting-ppds
  php5 php5-common python-at-spi python-numarray python-orca-brlapi
  python-software-properties python-virtkey restricted-manager
  scim-modules-table scim-tables-additional software-properties-gtk wodim
The following packages will be upgraded:
  bluez-pin bluez-utils brltty brltty-x11 bug-buddy bum cdda2wav cdparanoia
  cdrdao cdrecord checkgmail clamav clamav-base clamav-daemon clamav-docs
  clamav-freshclam clamtk contact-lookup-applet cupsys-bsd cupsys-client
  cupsys-driver-gutenprint d4x d4x-common dbconfig-common dbus-1-utils dc
  debconf-utils devede dh-make discover1 discover1-data doc-base dvd+rw-tools
  dvd-slideshow dvdauthor dvdrip dvgrab easytag edgy-community-wallpapers
  edgy-gdm-themes edgy-session-splashes edgy-wallpapers eog evince evms
  evms-ncurses evolution-plugins evolution-webcal example-content f-spot
  fakeroot ffmpeg fglrx-kernel-source file-roller foo2zjs
  foomatic-db-gutenprint foomatic-db-hpijs fortune-mod fortunes-min g++ gaim
  gaim-data gcalctool gcc gconf-editor gdebi gdm gedit gedit-common gftp
  gftp-common gftp-gtk gftp-text gimp gimp-data gimp-print
  gnome-accessibility-themes gnome-app-install gnome-btdownload
  gnome-cups-manager gnome-keyring-manager gnome-mag gnome-netstatus-applet
  gnome-nettool gnome-pilot gnome-pilot-conduits gnome-spell
  gnome-system-monitor gnome-system-tools gnome-themes gnomebaker gnopernicus
  gnupod-tools gocr gparted grub gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnonlin
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-sdl gstreamer0.10-tools
  gstreamer0.10-x gstreamer0.8-a52dec gstreamer0.8-mpeg2dec gthumb
  gtk2-engines gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8
  gtkpod-aac gucharmap hal-device-manager hfsplus hfsutils hotkey-setup hpijs
  hwdata hwdb-client-gnome imagemagick ipod iso-codes jfsutils kdelibs-data
  kdelibs4c2a ktorrent lame language-selector language-selector-common lftp
  lha libadns1 libarchive-tar-perl libarchive1 libavahi-qt3-1
  libbit-vector-perl libboost-date-time1.33.1 libboost-filesystem1.33.1
  libboost-program-options1.33.1 libboost-python1.33.1 libboost-regex1.33.1
  libboost-thread1.33.1 libbrlapi1 libbtctl4 libcairo-perl libcairomm-1.0-1
  libcarp-clan-perl libcompfaceg1 libcompress-zlib-perl libcurl3-gnutls
  libdate-calc-perl libdbd-mysql-perl libdbi-perl libdiscover1 libdjvulibre15
  libevms-2.5 libfile-find-rule-perl libflac++5c2 libfreezethaw-perl libfs6
  libgadu3 libgail-gnome-module libgeoip1 libglib-perl libglib2.0-data
  libglibmm-2.4-1c2a libglide2 libgmime-2.0-2 libgmime2.2-cil libgmp3c2
  libgnome-mag2 libgnome2-canvas-perl libgnomebt0 libgnomecupsui1.0-1c2a
  libgnomevfs2-bin libgnucrypto-java libgpod-common libgsf-1-114
  libgsf-1-common libgtk-perl libgtk2-gladexml-perl libgtk2-perl libgtkhtml2-0
  libgtkhtml3.8-15 libgtkmm-2.4-1c2a libgutenprintui2-1 libhfsp0
  libhtml-parser-perl libieee1284-3 libimlib2 libjline-java libkpathsea4
  liblog4j1.2-java liblua50 liblualib50 libmac-ipod-gnupod-perl libmatchbox1
  libmono-sqlite1.0-cil libmp3-info-perl libmp4-info-perl libmyspell3c2
  libmysqlclient15off libnetpbm10 libnetpbm9 libnss3-0d libnumber-compare-perl
  libopenexr2c2a libphp-adodb libpng3 libpq4 libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0 librecode0
  libruby1.8 libscim8c2a libsmjs1 libstlport4.6c2 libtext-glob-perl
  libuniconf4.2 libwmf0.2-7 libwvstreams4.2-base libwvstreams4.2-extras
  libxine-extracodecs libxine-main1 libxml-libxml-perl
  libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl libxml1
  libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxmuu1 libxul-common libxul0d
  libzzip-0-12 linux-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common m4 mdadm mencoder menu min12xxw mkisofs
  module-assistant mozilla-mplayer mpeg2dec mysql-client mysql-client-5.0
  mysql-common nautilus-cd-burner nautilus-sendto netpbm p7zip pdmenu pnm2ppa
  powernowd python-adns python-crypto python-egenix-mxdatetime
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-gadfly python-gdbm python-geoip
  python-gst0.10 python-gtkhtml2 python-htmlgen python-imaging
  python-imaging-sane python-jabber python-launchpad-integration python-ldap
  python-libxslt1 python-mysqldb python-notify python-pam python-pycurl
  python-pylibacl python-pyogg python-pyopenssl python-pyvorbis python-pyxattr
  python-soappy python-sqlite python-syck python-tk python-unit
  python2.4-examples rar rdesktop readahead reiser4progs reportbug rss-glx
  samba-common sbackup scim scim-gtk2-immodule scim-modules-socket serpentine
  slocate smbclient ssh-askpass-gnome supertux supertux-data
  tangerine-icon-theme tango-icon-theme tango-icon-theme-common tcpd tomboy
  torrentflux totem totem-mozilla tsclient ttf-arphic-ukai ttf-bengali-fonts
  ttf-devanagari-fonts ttf-dustin ttf-gentium ttf-gujarati-fonts
  ttf-indic-fonts ttf-kannada-fonts ttf-malayalam-fonts ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg
  ubuntu-artwork ubuntu-desktop ubuntu-sounds unace unattended-upgrades unrar
  unzip unzoo update-notifier usplash usplash-theme-ubuntu vino
  vlc-plugin-alsa vlc-plugin-arts vlc-plugin-ggi vlc-plugin-glide
  vlc-plugin-sdl vorbis-tools whois wvdial wxvlc x-ttcidfont-conf
  x-window-system-core xcdroast xcursor-themes xfonts-100dpi xfonts-75dpi
  xfonts-artwiz xfonts-base xfonts-scalable xfsprogs xkeyboard-config xorg
  xresprobe xscreensaver-data xscreensaver-gl xserver-xorg-dev zenity
390 upgraded, 46 newly installed, 1 to remove and 0 not upgraded.
311 not fully installed or removed.
Need to get 0B/318MB of archives.
After unpacking 250MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
pcilib: Cannot open /proc/bus/pci
(Reading database ... 142036 files and directories currently installed.)
Preparing to replace bluez-utils 3.7-1ubuntu4 (using .../bluez-utils_3.9-0ubuntu4_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

```

HOW do i fix this!!!

---

### Post by bwhite82 on 2007-04-20
Hmmm....seems its having problems replacing the older bluetooth package with the new one. Try simply removing the offending package first, and then go through the steps that you've already tried, again.
> 
sudo aptitude remove bluez-utils

---

### Post by keef247 on 2007-04-20
:( btw i had automatix installed aswell if thats caused hassle and i have a feeling i installed a bluetooth utility on that...

```
Preparing to replace python2.4-examples 2.4.4~c1-0ubuntu1 (using .../python2.4-examples_2.4.4-2ubuntu7_all.deb) ...
Unpacking replacement python2.4-examples ...
Preparing to replace rar 1:3.6.0-0ubuntu1~edgy1 (using .../rar_1%3a3.7b1-2_i386.deb) ...
Unpacking replacement rar ...
Preparing to replace rdesktop 1.5.0-1build1~edgy1 (using .../rdesktop_1.5.0-1build1_i386.deb) ...
Unpacking replacement rdesktop ...
Preparing to replace readahead 1:0.20050517.0220-0ubuntu7 (using .../readahead_1%3a0.20050517.0220-0ubuntu9_i386.deb) ...
Unpacking replacement readahead ...
Preparing to replace reiser4progs 1.0.5-1 (using .../reiser4progs_1.0.5-2build1_i386.deb) ...
Unpacking replacement reiser4progs ...
Preparing to replace reportbug 3.21.2ubuntu1 (using .../reportbug_3.31ubuntu1_all.deb) ...
Unpacking replacement reportbug ...
Selecting previously deselected package restricted-manager.
Unpacking restricted-manager (from .../restricted-manager_0.20_all.deb) ...
Preparing to replace rss-glx 0.8.1-3ubuntu2 (using .../rss-glx_0.8.1-3ubuntu3_i386.deb) ...
Unpacking replacement rss-glx ...
Preparing to replace smbclient 3.0.22-1ubuntu4.1 (using .../smbclient_3.0.24-2ubuntu1_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 3.0.22-1ubuntu4.1 (using .../samba-common_3.0.24-2ubuntu1_i386.deb) ...
Unpacking replacement samba-common ...
Preparing to replace sbackup 0.10.3 (using .../sbackup_0.10.3-0.1_all.deb) ...
Unpacking replacement sbackup ...
Preparing to replace scim-gtk2-immodule 1.4.4-4ubuntu6 (using .../scim-gtk2-immodule_1.4.4-7ubuntu1_i386.deb) ...
Unpacking replacement scim-gtk2-immodule ...
Preparing to replace scim-modules-socket 1.4.4-4ubuntu6 (using .../scim-modules-socket_1.4.4-7ubuntu1_i386.deb) ...
Unpacking replacement scim-modules-socket ...
Preparing to replace scim 1.4.4-4ubuntu6 (using .../scim_1.4.4-7ubuntu1_i386.deb) ...
Unpacking replacement scim ...
Selecting previously deselected package scim-modules-table.
Unpacking scim-modules-table (from .../scim-modules-table_0.5.6-2_i386.deb) ...
Selecting previously deselected package scim-tables-additional.
Unpacking scim-tables-additional (from .../scim-tables-additional_0.5.6-2_all.deb) ...
Preparing to replace serpentine 0.6.91-0ubuntu4 (using .../serpentine_0.7-4ubuntu3_all.deb) ...
Unpacking replacement serpentine ...
Preparing to replace ssh-askpass-gnome 1:4.3p2-5ubuntu1 (using .../ssh-askpass-gnome_1%3a4.3p2-8ubuntu1_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Preparing to replace supertux-data 0.3.0-0ubuntu1~edgy1 (using .../supertux-data_0.3.0-0ubuntu2_all.deb) ...
Unpacking replacement supertux-data ...
Preparing to replace supertux 0.3.0-0ubuntu1~edgy1 (using .../supertux_0.3.0-0ubuntu2_i386.deb) ...
Unpacking replacement supertux ...
Preparing to replace tango-icon-theme-common 0.5-0ubuntu1 (using .../tango-icon-theme-common_0.7-0ubuntu1_all.deb) ...
Unpacking replacement tango-icon-theme-common ...
Preparing to replace tango-icon-theme 0.7.2+cvs06.07.31-0ubuntu3 (using .../tango-icon-theme_0.7.2+cvs07.02.06-0ubuntu1_all.deb) ...
Unpacking replacement tango-icon-theme ...
Preparing to replace tangerine-icon-theme 0.14-0ubuntu1 (using .../tangerine-icon-theme_0.20-0ubuntu1_all.deb) ...
Unpacking replacement tangerine-icon-theme ...
Preparing to replace tcpd 7.6.dbs-9 (using .../tcpd_7.6.dbs-11build1_i386.deb) ...
Unpacking replacement tcpd ...
Preparing to replace tomboy 0.4.1-0ubuntu3 (using .../tomboy_0.6.3-0ubuntu1_i386.deb) ...
Unpacking replacement tomboy ...
Selecting previously deselected package torrentflux.
Preparing to replace torrentflux 2.1-1ubuntu0.1 (using .../torrentflux_2.1-7_all.deb) ...
Unpacking replacement torrentflux ...
Preparing to replace totem 2.16.2-0ubuntu3 (using .../totem_2.18.1-0ubuntu3_all.deb) ...
Unpacking replacement totem ...
Preparing to replace totem-mozilla 2.16.2-0ubuntu3 (using .../totem-mozilla_2.18.1-0ubuntu3_all.deb) ...
Unpacking replacement totem-mozilla ...
Preparing to replace tsclient 0.148-1ubuntu4 (using .../tsclient_0.148-2ubuntu3_i386.deb) ...
Unpacking replacement tsclient ...
Preparing to replace ttf-arphic-ukai 0.1.20060513-1 (using .../ttf-arphic-ukai_0.1.20060928-2_all.deb) ...
Unpacking replacement ttf-arphic-ukai ...
Preparing to replace ttf-bengali-fonts 1:0.4.7.1 (using .../ttf-bengali-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-bengali-fonts ...
Preparing to replace ttf-devanagari-fonts 1:0.4.7.1 (using .../ttf-devanagari-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-devanagari-fonts ...
Preparing to replace ttf-dustin 20030517-1ubuntu1 (using .../ttf-dustin_20030517-4_all.deb) ...
Unpacking replacement ttf-dustin ...
Preparing to replace ttf-gentium 1.02-2ubuntu1 (using .../ttf-gentium_1.02-2ubuntu2_all.deb) ...
Unpacking replacement ttf-gentium ...
Preparing to replace ttf-gujarati-fonts 1:0.4.7.1 (using .../ttf-gujarati-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-gujarati-fonts ...
Preparing to replace ttf-kannada-fonts 1:0.4.7.1 (using .../ttf-kannada-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-kannada-fonts ...
Preparing to replace ttf-malayalam-fonts 1:0.4.7.1 (using .../ttf-malayalam-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-malayalam-fonts ...
Preparing to replace ttf-oriya-fonts 1:0.4.7.1 (using .../ttf-oriya-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-oriya-fonts ...
Preparing to replace ttf-punjabi-fonts 1:0.4.7.1 (using .../ttf-punjabi-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-punjabi-fonts ...
Preparing to replace ttf-tamil-fonts 1:0.4.7.1 (using .../ttf-tamil-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-tamil-fonts ...
Preparing to replace ttf-telugu-fonts 1:0.4.7.1 (using .../ttf-telugu-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-telugu-fonts ...
Preparing to replace ttf-indic-fonts 1:0.4.7.1 (using .../ttf-indic-fonts_1%3a0.4.7.3_all.deb) ...
Unpacking replacement ttf-indic-fonts ...
Preparing to replace x-ttcidfont-conf 24ubuntu1 (using .../x-ttcidfont-conf_25_all.deb) ...
Cleaning up font configuration of x-ttcidfont-conf...
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
opendir: No such file or directory
Unpacking replacement x-ttcidfont-conf ...
Preparing to replace ttf-thai-tlwg 0.4.4-0ubuntu1 (using .../ttf-thai-tlwg_1%3a0.4.5-3_all.deb) ...
Unpacking replacement ttf-thai-tlwg ...
Preparing to replace ubuntu-artwork 31 (using .../ubuntu-artwork_36_all.deb) ...Unpacking replacement ubuntu-artwork ...
Selecting previously deselected package dcraw.
Unpacking dcraw (from .../archives/dcraw_8.39-1_i386.deb) ...
Preparing to replace gnome-pilot 2.0.14-0ubuntu2 (using .../gnome-pilot_2.0.15-0.1ubuntu1_i386.deb) ...
Unpacking replacement gnome-pilot ...
Preparing to replace gnome-pilot-conduits 2.0.14-0ubuntu1 (using .../gnome-pilot-conduits_2.0.15-0.1ubuntu1_i386.deb) ...
Unpacking replacement gnome-pilot-conduits ...
Preparing to replace gnome-system-tools 2.15.5-0ubuntu5 (using .../gnome-system-tools_2.18.1-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-system-tools ...
Preparing to replace slocate 3.1-1ubuntu0.1 (using .../slocate_3.1-1ubuntu1_i386.deb) ...
Removing `diversion of /usr/bin/locate to /usr/bin/locate.notslocate by slocate'Removing `diversion of /usr/bin/updatedb to /usr/bin/updatedb.notslocate by slocate'
Removing `diversion of /usr/share/man/man1/updatedb.1.gz to /usr/share/man/man1/updatedb.notslocate.1.gz by slocate'
Removing `diversion of /usr/share/man/man1/locate.1.gz to /usr/share/man/man1/locate.notslocate.1.gz by slocate'
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
Adding `diversion of /usr/bin/locate to /usr/bin/locate.notslocate by slocate'
Adding `diversion of /usr/bin/updatedb to /usr/bin/updatedb.notslocate by slocate'
Adding `diversion of /usr/share/man/man1/locate.1.gz to /usr/share/man/man1/locate.notslocate.1.gz by slocate'
Adding `diversion of /usr/share/man/man1/updatedb.1.gz to /usr/share/man/man1/updatedb.notslocate.1.gz by slocate'
Adding `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
Unpacking replacement slocate ...
Preparing to replace ubuntu-sounds 0.5 (using .../ubuntu-sounds_0.6_all.deb) ...Unpacking replacement ubuntu-sounds ...
Preparing to replace update-notifier 0.43.4 (using .../update-notifier_0.56.3_i386.deb) ...
Unpacking replacement update-notifier ...
Preparing to replace usplash 0.4-33 (using .../usplash_0.4-44_i386.deb) ...
Unpacking replacement usplash ...
Preparing to replace usplash-theme-ubuntu 0.6 (using .../usplash-theme-ubuntu_0.14_i386.deb) ...
Unpacking replacement usplash-theme-ubuntu ...
Preparing to replace vino 2.16.0-0ubuntu2.4 (using .../vino_2.18.1-0ubuntu1_i386.deb) ...
Unpacking replacement vino ...
Preparing to replace wvdial 1.56-1ubuntu1 (using .../wvdial_1.56-1.1ubuntu2_i386.deb) ...
Unpacking replacement wvdial ...
Preparing to replace xfonts-base 1:1.0.0-3ubuntu1 (using .../xfonts-base_1%3a1.0.0-4_all.deb) ...
Unpacking replacement xfonts-base ...
Preparing to replace xfonts-100dpi 1:1.0.0-2ubuntu1 (using .../xfonts-100dpi_1%3a1.0.0-3_all.deb) ...
Unpacking replacement xfonts-100dpi ...
dpkg: warning - unable to delete old directory `/etc/X11/fonts/X11R7/100dpi': Directory not empty
Preparing to replace xfonts-75dpi 1:1.0.0-2ubuntu1 (using .../xfonts-75dpi_1%3a1.0.0-3_all.deb) ...
Unpacking replacement xfonts-75dpi ...
dpkg: warning - unable to delete old directory `/etc/X11/fonts/X11R7/75dpi': Directory not empty
Preparing to replace xfonts-scalable 1:1.0.0-4ubuntu1 (using .../xfonts-scalable_1%3a1.0.0-6_all.deb) ...
Unpacking replacement xfonts-scalable ...
dpkg: warning - unable to delete old directory `/etc/X11/fonts/X11R7/Type1': Directory not empty
Preparing to replace xorg 1:7.1.1ubuntu6.2 (using .../xorg_1%3a7.2-0ubuntu11_i386.deb) ...
Unpacking replacement xorg ...
Preparing to replace xscreensaver-data 4.24-4ubuntu2 (using .../xscreensaver-data_4.24-5ubuntu2_i386.deb) ...
Unpacking replacement xscreensaver-data ...
Preparing to replace xscreensaver-gl 4.24-4ubuntu2 (using .../xscreensaver-gl_4.24-5ubuntu2_i386.deb) ...
Unpacking replacement xscreensaver-gl ...
Preparing to replace zenity 2.16.1-0ubuntu1 (using .../zenity_2.18.1-0ubuntu1_i386.deb) ...
Unpacking replacement zenity ...
Preparing to replace ubuntu-desktop 1.30 (using .../ubuntu-desktop_1.43_i386.deb) ...
Unpacking replacement ubuntu-desktop ...
Preparing to replace unace 1.2b-3 (using .../archives/unace_1.2b-4_i386.deb) ...Unpacking replacement unace ...
Preparing to replace unrar 1:3.7.3-1~edgy1 (using .../unrar_1%3a3.7.3-1_i386.deb) ...
Unpacking replacement unrar ...
Preparing to replace vlc-plugin-alsa 0.8.6.release-0ubuntu1~edgy1 (using .../vlc-plugin-alsa_0.8.6.release-0ubuntu4_all.deb) ...
Unpacking replacement vlc-plugin-alsa ...
Preparing to replace vlc-plugin-arts 0.8.6.release-0ubuntu1~edgy1 (using .../vlc-plugin-arts_0.8.6.release-0ubuntu4_i386.deb) ...
Unpacking replacement vlc-plugin-arts ...
Preparing to replace vlc-plugin-ggi 0.8.6.release-0ubuntu1~edgy1 (using .../vlc-plugin-ggi_0.8.6.release-0ubuntu4_i386.deb) ...
Unpacking replacement vlc-plugin-ggi ...
Preparing to replace vlc-plugin-glide 0.8.6.release-0ubuntu1~edgy1 (using .../vlc-plugin-glide_0.8.6.release-0ubuntu4_i386.deb) ...
Unpacking replacement vlc-plugin-glide ...
Preparing to replace vlc-plugin-sdl 0.8.6.release-0ubuntu1~edgy1 (using .../vlc-plugin-sdl_0.8.6.release-0ubuntu4_i386.deb) ...
Unpacking replacement vlc-plugin-sdl ...
Preparing to replace vorbis-tools 1.1.1-5 (using .../vorbis-tools_1.1.1-6build1_i386.deb) ...
Unpacking replacement vorbis-tools ...
Preparing to replace wxvlc 0.8.6.release-0ubuntu1~edgy1 (using .../wxvlc_0.8.6.release-0ubuntu4_all.deb) ...
Unpacking replacement wxvlc ...
Preparing to replace x-window-system-core 1:7.1.1ubuntu6.2 (using .../x-window-system-core_1%3a7.2-0ubuntu11_all.deb) ...
Unpacking replacement x-window-system-core ...
Preparing to replace xcursor-themes 1.0.1-4build1 (using .../xcursor-themes_1.0.1-5ubuntu1_all.deb) ...
Unpacking replacement xcursor-themes ...
Preparing to replace xfonts-artwiz 1:1.3-2ubuntu1 (using .../xfonts-artwiz_1%3a1.3-5_all.deb) ...
Unpacking replacement xfonts-artwiz ...
dpkg: warning - unable to delete old directory `/usr/share/X11/fonts/misc': Directory not empty
Preparing to replace xfsprogs 2.8.10-1 (using .../xfsprogs_2.8.18-1build1_i386.deb) ...
Unpacking replacement xfsprogs ...
Preparing to replace xresprobe 0.4.24 (using .../xresprobe_0.4.24ubuntu3_i386.deb) ...
Unpacking replacement xresprobe ...
Preparing to replace xserver-xorg-dev 1:1.1.1-0ubuntu12.2 (using .../xserver-xorg-dev_2%3a1.2.0-3ubuntu8_i386.deb) ...
Unpacking replacement xserver-xorg-dev ...
Preparing to replace brltty-x11 3.7.2-3.1ubuntu3 (using .../brltty-x11_3.7.2-7ubuntu3_i386.deb) ...
Unpacking replacement brltty-x11 ...
Preparing to replace brltty 3.7.2-3.1ubuntu3 (using .../brltty_3.7.2-7ubuntu3_i386.deb) ...
Unpacking replacement brltty ...
Preparing to replace dvgrab 1.8-3build1 (using .../archives/dvgrab_1.8-4_i386.deb) ...
Unpacking replacement dvgrab ...
Preparing to replace gtkpod-aac 0.99.4-0ubuntu1 (using .../gtkpod-aac_0.99.8-0ubuntu2_i386.deb) ...
Unpacking replacement gtkpod-aac ...
Preparing to replace python-pycurl 7.15.4-1build1 (using .../python-pycurl_7.15.5-1ubuntu1_i386.deb) ...
Unpacking replacement python-pycurl ...
Preparing to replace unzoo 4.4-4 (using .../archives/unzoo_4.4-5_i386.deb) ...
Unpacking replacement unzoo ...
Preparing to replace xkeyboard-config 0.8-7ubuntu2 (using .../xkeyboard-config_0.9-4ubuntu1_all.deb) ...
Unpacking replacement xkeyboard-config ...
Errors were encountered while processing:
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# sudo aptitude remove bluez-utils-utils_3.9-0ubuntu4_i386.deb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "bluez-utils-utils_3.9-0ubuntu4_i386.deb"
The following packages have been kept back:
  bluez-utils powernowd
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the powernowd package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@ubuntu:/# chroot /media/oldroot
chroot: cannot change root directory to /media/oldroot: No such file or directory
root@ubuntu:/# sudo aptitude remove powernowd_0.97- lubuntu7_i386.deb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "powernowd_0.97"
Couldn't find any package whose name or description matched "lubuntu7_i386.deb"
The following packages have been kept back:
  bluez-utils powernowd
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the powernowd package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@ubuntu:/# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bluez-utils powernowd
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
687 not fully installed or removed.
Need to get 0B/312kB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 159591 files and directories currently installed.)
Preparing to replace powernowd 0.97-1ubuntu6 (using .../powernowd_0.97-1ubuntu7_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace bluez-utils 3.7-1ubuntu4 (using .../bluez-utils_3.9-0ubuntu4_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libalut0 libopenthreads3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  powernowd
The following packages will be upgraded:
  powernowd
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
687 not fully installed or removed.
Need to get 0B/24.8kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 159591 files and directories currently installed.)
Preparing to replace powernowd 0.97-1ubuntu6 (using .../powernowd_0.97-1ubuntu7_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get -f dist-uprgrade
E: Invalid operation dist-uprgrade
root@ubuntu:/# apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bluez-utils powernowd
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
687 not fully installed or removed.
Need to get 0B/312kB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 159591 files and directories currently installed.)
Preparing to replace powernowd 0.97-1ubuntu6 (using .../powernowd_0.97-1ubuntu7_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace bluez-utils 3.7-1ubuntu4 (using .../bluez-utils_3.9-0ubuntu4_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

```

---

### Post by keef247 on 2007-04-20
tired dpkg --configure -a
```
Regenerating fonts cache... done.

Setting up libmyspell3c2 (3.1-18build1) ...

Setting up libscim8c2a (1.4.4-7ubuntu1) ...

Setting up liblualib50 (5.0.3-2build1) ...

Setting up libsmjs1 (1.8.0.10-3ubuntu1) ...
Setting up unrar (3.7.3-1) ...
Setting up unattended-upgrades (0.22ubuntu2) ...
Installing new version of config file /etc/apt/apt.conf.d/50unattended-upgrades ...
Setting up libfs6 (1.0.0-4ubuntu2) ...

Setting up libxmlsec1-nss (1.2.9-5ubuntu1) ...

Setting up gstreamer0.8-a52dec (0.8.12-6ubuntu3) ...

Setting up libboost-python1.33.1 (1.33.1-9ubuntu3) ...

Setting up php5-common (5.2.1-0ubuntu1) ...
Setting up python-libxslt1 (1.1.20-0ubuntu2) ...

Setting up xfonts-75dpi (1.0.0-3) ...
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory

Setting up libimlib2 (1.3.0.0debian1-4build1) ...

Setting up supertux-data (0.3.0-0ubuntu2) ...
Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.5-2) ...
Setting up libusplash0 (0.4-44) ...
Setting up libadns1 (1.4-0.1build1) ...

dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
Setting up python-jabber (0.5.0-1.4) ...

Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20060515-1ubuntu1) ...
Setting up python-gadfly (1.0.0-11) ...

Setting up rdesktop (1.5.0-1build1) ...
Setting up ttf-malayalam-fonts (0.4.7.3) ...
Regenerating fonts cache... done.

Setting up libnetpbm9 (10.0-11) ...

dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Setting up libglibmm-2.4-1c2a (2.13.3-0ubuntu1) ...

Setting up libgnucrypto-java (2.1.0-2) ...

dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.14-19 (>= 3.14.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up hotkey-setup (0.1-17ubuntu9) ...
Installing new version of config file /etc/init.d/hotkey-setup ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------

Setting up libbrlapi1 (3.7.2-7ubuntu3) ...

Setting up gstreamer0.10-gnonlin (0.10.7-1) ...
Setting up reiser4progs (1.0.5-2build1) ...
Setting up supertux (0.3.0-0ubuntu2) ...

dpkg: dependency problems prevent configuration of libgail-gnome-module:
 libgail-gnome-module depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgail-gnome-module (--configure):
 dependency problems - leaving unconfigured
Setting up xresprobe (0.4.24ubuntu3) ...
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up python-pyopenssl (0.6-2.3ubuntu1) ...

Setting up iso-codes (1.0-1) ...
Setting up x-ttcidfont-conf (25) ...
Updating font configuration of x-ttcidfont-conf...
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Updating category truetype..
Updating category cid..
Updating category cmap..

dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
Setting up python-pam (0.4.2-10.4ubuntu2) ...

Setting up rss-glx (0.8.1-3ubuntu3) ...
Setting up python-gst0.10 (0.10.6-1ubuntu3) ...

Setting up reportbug (3.31ubuntu1) ...

Setting up discover1 (1.7.20ubuntu1) ...
Installing new version of config file /etc/discover.conf ...

Setting up kdelibs-data (3.5.6-0ubuntu14) ...

Setting up min12xxw (0.0.9-1build1) ...
dpkg: dependency problems prevent configuration of dbus-1-utils:
 dbus-1-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-1-utils (--configure):
 dependency problems - leaving unconfigured
Setting up python-crypto (2.0.1+dfsg1-1.2ubuntu1) ...

Setting up evms-ncurses (2.5.5-18ubuntu4) ...
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
 network-manager depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.14-19 (>= 3.14.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
 evolution depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
Setting up python-virtkey (0.41ubuntu1) ...

dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-tools:
 gnome-system-tools depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-system-tools depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing gnome-system-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgucharmap6:
 libgucharmap6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgucharmap6 (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-core (4.2.3-0ubuntu3) ...

Setting up xserver-xorg-dev (1.2.0-3ubuntu8) ...
Setting up python-imaging (1.1.6-0ubuntu3) ...

dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
Setting up libarchive1 (1.3.1-1) ...

dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
Setting up python-htmlgen (2.2.2-11) ...

dpkg: dependency problems prevent configuration of gnome-spell:
 gnome-spell depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-spell depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-spell (--configure):
 dependency problems - leaving unconfigured
Setting up dcraw (8.39-1) ...
dpkg: dependency problems prevent configuration of libipoddevice0:
 libipoddevice0 depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
dpkg: error processing libipoddevice0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-applets depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-applets depends on libgucharmap6; however:
  Package libgucharmap6 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up libopenobex1 (1.3-3) ...

dpkg: dependency problems prevent configuration of libipod-cil:
 libipod-cil depends on libipoddevice0 (>= 0.5.3); however:
  Package libipoddevice0 is not configured yet.
dpkg: error processing libipod-cil (--configure):
 dependency problems - leaving unconfigured
Setting up xfonts-artwiz (1.3-5) ...
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

dpkg: dependency problems prevent configuration of libgnomevfs2-bin:
 libgnomevfs2-bin depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-bin (--configure):
 dependency problems - leaving unconfigured
Setting up language-selector-common (0.2.6) ...

Setting up libglide2 (2002.04.10-14) ...
pcilib: Cannot open /proc/bus/pci

dpkg: dependency problems prevent configuration of libgnomecupsui1.0-1c2a:
 libgnomecupsui1.0-1c2a depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnomecupsui1.0-1c2a depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomecupsui1.0-1c2a (--configure):
 dependency problems - leaving unconfigured
Setting up python-egenix-mxtexttools (2.0.6ubuntu1-5ubuntu1) ...
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:170: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:191: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:195: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:206: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:225: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:231: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:244: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:249: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:261: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:557: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:559: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:562: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:566: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:574: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:582: Warning: 'with' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/mx/TextTools/TextTools.py:590: Warning: 'with' will become a reserved keyword in Python 2.6

dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
Setting up slocate (3.1-1ubuntu1) ...

dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 compiz-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
Setting up libgnome-mag2 (0.14.3-0ubuntu1) ...

dpkg: error processing powernowd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up lame (3.96.1-2ubuntu1) ...

Setting up gstreamer0.10-x (0.10.12-0ubuntu1) ...
Setting up m4 (1.4.8-1build1) ...

dpkg: dependency problems prevent configuration of totem-xine:
 totem-xine depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 totem-xine depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 totem-xine depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing totem-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 network-manager-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 network-manager-gnome depends on network-manager (= 0.6.4-6ubuntu7); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 nautilus-sendto depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 nautilus-sendto depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
Setting up libmono-sqlite1.0-cil (1.2.3.1-1ubuntu1) ...
Setting up python-egenix-mxstack (2.0.6ubuntu1-5ubuntu1) ...

Setting up libflac++5c2 (1.1.2-5ubuntu2) ...

Setting up gstreamer0.10-tools (0.10.12-0ubuntu2) ...
Setting up libgmime-2.0-2 (2.2.3-3ubuntu1) ...

Setting up libraptor1 (1.4.13-1build1) ...

Setting up mpeg2dec (0.4.1-1) ...
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
Setting up python-orca-brlapi (2.18.1-0ubuntu1) ...
Setting up p7zip (4.43~dfsg.1-1) ...
Setting up python-pyogg (1.3-1.1ubuntu4) ...

Setting up ttf-bengali-fonts (0.4.7.3) ...
Regenerating fonts cache... done.

Setting up libbtctl4 (0.8.2-0ubuntu6) ...

dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-power-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-terminal depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firestarter:
 firestarter depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 firestarter depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 firestarter depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firestarter (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 rhythmbox
 totem-mozilla
 hal
 gnome-mount
 dhcdbd
 gnome-volume-manager
 at
 update-notifier
 libgnomevfs2-0
 nautilus
 libgtkhtml3.14-19
 evolution-plugins
 libgail-gnome-module
 ubuntu-desktop
 firefox-gnome-support
 gnome-utils
 dbus-1-utils
 libedata-book1.2-2
 libnautilus-extension1
 gthumb
 network-manager
 evolution
 gnome-screensaver
 gnome-system-tools
 libgucharmap6
 libgtkhtml3.8-15
 f-spot
 libedata-cal1.2-6
 libgnome2-0
 gnome-spell
 libipoddevice0
 gnome-applets
 libipod-cil
 libgnomevfs2-bin
 libgnomecupsui1.0-1c2a
 gnome-about
 hal-device-manager
 compiz-gnome
 ekiga
 powernowd
 avahi-daemon
 totem-xine
 network-manager-gnome
 nautilus-sendto
 python-gnome2-extras
 gnome-power-manager
 libbonoboui2-0
 python-gnome2
 gnome-terminal
 firestarter
Processing was halted because there were too many errors.
root@ubuntu:/#

```

---

### Post by keef247 on 2007-04-20
seems powernowd is a problem aswell whatever that is.no matter if i reinstall/remove -f powernowd/bluezutils it doesn't do the action it just errors...
```
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get install powernowd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libalut0 libopenthreads3
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  powernowd
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
514 not fully installed or removed.
Need to get 0B/24.8kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 159591 files and directories currently installed.)
Preparing to replace powernowd 0.97-1ubuntu6 (using .../powernowd_0.97-1ubuntu7_i386.deb) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/powernowd_0.97-1ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# dpkg -f --configure -a
dpkg: conflicting actions -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@ubuntu:/# dpkg --configure -a
Setting up linux-headers-2.6.20-15-generic (2.6.20-15.27) ...
Setting up libqt4-gui (4.2.3-0ubuntu3) ...

Setting up python-geoip (1.2.1-2ubuntu1) ...

Setting up libuniconf4.2 (4.2.2-2.2ubuntu2) ...

Setting up python-egenix-mxproxy (2.0.6ubuntu1-5ubuntu1) ...

Setting up ttf-thai-tlwg (0.4.5-3) ...
Installing new version of config file /etc/defoma/hints/ttf-thai-tlwg.hints ...

Setting up python-software-properties (0.59.4) ...

Setting up libmysqlclient15off (5.0.38-0ubuntu1) ...

Setting up dbus (1.0.2-1ubuntu3) ...
Fixing up startup script priorities...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
Setting up libgsf-1-114 (1.14.3-1ubuntu2) ...

Setting up python-adns (1.1.0-2ubuntu2) ...

dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.60-1); however:
  Package dbus is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
Setting up python-imaging-sane (1.1.6-0ubuntu3) ...

dpkg: dependency problems prevent configuration of dhcdbd:
 dhcdbd depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing dhcdbd (--configure):
 dependency problems - leaving unconfigured
Setting up python-pyvorbis (1.3-1.2ubuntu2) ...

Setting up scim-modules-socket (1.4.4-7ubuntu1) ...
Setting up gftp-text (2.0.18-16ubuntu2) ...

dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
Setting up at (3.1.10ubuntu4) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
Setting up libgmime2.2-cil (2.2.3-3ubuntu1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
E: installing Assembly /usr/lib/cli/gmime-sharp-2.2/gmime-sharp.dll failed

dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.14-19 (>= 3.14.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-gnome-module:
 libgail-gnome-module depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgail-gnome-module (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-1-utils:
 dbus-1-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-1-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
 network-manager depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.14-19 (>= 3.14.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
 evolution depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-tools:
 gnome-system-tools depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-system-tools depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing gnome-system-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgucharmap6:
 libgucharmap6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgucharmap6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
Setting up librasqal0 (0.9.13-1build1) ...

dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-spell:
 gnome-spell depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-spell depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-spell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libipoddevice0:
 libipoddevice0 depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
dpkg: error processing libipoddevice0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-applets depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-applets depends on libgucharmap6; however:
  Package libgucharmap6 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-generic (2.6.20.15.14) ...
dpkg: dependency problems prevent configuration of libipod-cil:
 libipod-cil depends on libipoddevice0 (>= 0.5.3); however:
  Package libipoddevice0 is not configured yet.
dpkg: error processing libipod-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-bin:
 libgnomevfs2-bin depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-bin (--configure):
 dependency problems - leaving unconfigured
Setting up wvdial (1.56-1.1ubuntu2) ...

Sorry.  You can retry the autodetection at any time by running "wvdialconf".
   (Or you can create /etc/wvdial.conf yourself.)

dpkg: dependency problems prevent configuration of libgnomecupsui1.0-1c2a:
 libgnomecupsui1.0-1c2a depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnomecupsui1.0-1c2a depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomecupsui1.0-1c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 compiz-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing powernowd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up ttf-indic-fonts (0.4.7.3) ...
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-xine:
 totem-xine depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 totem-xine depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 totem-xine depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing totem-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 network-manager-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 network-manager-gnome depends on network-manager (= 0.6.4-6ubuntu7); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 nautilus-sendto depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 nautilus-sendto depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-power-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-terminal depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firestarter:
 firestarter depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 firestarter depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 firestarter depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firestarter (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 rhythmbox
 totem-mozilla
 hal
 gnome-mount
 dhcdbd
 gnome-volume-manager
 at
 update-notifier
 libgnomevfs2-0
 nautilus
 libgtkhtml3.14-19
 evolution-plugins
 libgail-gnome-module
 ubuntu-desktop
 firefox-gnome-support
 gnome-utils
 dbus-1-utils
 libedata-book1.2-2
 libnautilus-extension1
 gthumb
 network-manager
 evolution
 gnome-screensaver
 gnome-system-tools
 libgucharmap6
 libgtkhtml3.8-15
 f-spot
 libedata-cal1.2-6
 libgnome2-0
 gnome-spell
 libipoddevice0
 gnome-applets
 libipod-cil
 libgnomevfs2-bin
 libgnomecupsui1.0-1c2a
 gnome-about
 hal-device-manager
 compiz-gnome
 ekiga
 powernowd
 avahi-daemon
 totem-xine
 network-manager-gnome
 nautilus-sendto
 python-gnome2-extras
 gnome-power-manager
 libbonoboui2-0
 python-gnome2
 gnome-terminal
 firestarter
Processing was halted because there were too many errors.
root@ubuntu:/# dpkg -f --configure -a
dpkg: conflicting actions -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@ubuntu:/# dpkg --configure -f
dpkg: conflicting actions -f (--field) and -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@ubuntu:/#

```

---

