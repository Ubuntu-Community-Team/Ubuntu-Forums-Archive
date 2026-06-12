---
title: "Cant Upgade To Fiesty !!!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-04-20
Hi there :)

I am trying  to upgrade from 6.10 to Fiesty with upgrade manager. I upgraded the necessary packages for 6.10 before I started the major upgrade to Fiesty...............anyway I had to go to sleep cause it was going to take like two hours only to find out this morning the installation clashed-- this is the error message I keep getting --------Not All Updates Can Be Installed. So I went ahead and tried to upgrade via terminal and I am still getting error messages .......please help. I am including the error message from my  terminal 



sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  human-gtk-theme libvolumeid0 python-apport-utils
The following NEW packages will be installed:
  boo command-not-found command-not-found-data dmsetup espeak-data
  evolution-common feisty-gdm-themes feisty-session-splashes feisty-wallpapers
  gdebi-core genisoimage gnome-cards-data gnome-mount gnome-user-guide gpgv
  gs-esp-x gtkhtml3.14 libavahi-core5 libcaca0 libcamel1.2-10 libcdaudio1
  libclamav2 libcucul0 libdatrie0 libdb4.2 libdirectfb-0.9-25 libdns22
  libedataserver1.2-9 libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3
  libfreebob0 libgail-gnome-module libgdiplus libgnomekbd-common libgnomekbd1
  libgnomekbdui1 libgpod1 libgs-esp8 libgtkhtml3.14-19 libgucharmap6
  libhunspell-1.1-0 libicu36 libipod-cil libipodui-cil libjack0.100.0-0
  libjaxp1.3-java libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnm-glib0
  liboobs-1-3 libopenobex1 libpulse0 libsasl2-2 libslab0 libsoundtouch1c2
  libstlport5.1 libthai-data libthai0 libusplash0 libvolume-id0 libwavpack1
  libwps-0.1-1 libwv-1.2-3 libwxbase2.6-0 libwxgtk2.6-0 libx86-1
  libxcomposite1 libxine1-ffmpeg libxml-twig-perl linux-headers-2.6.20-15
  linux-headers-2.6.20-15-generic linux-image-2.6.20-15-generic
  linux-restricted-modules-2.6.20-15-generic mscompress myspell-en-za
  openoffice.org-filter-mobiledev openoffice.org-hyphenation
  openoffice.org-style-andromeda openoffice.org-style-human python-apport
  python-bittorrent python-launchpad-bugs python-orca-brlapi
  python-software-properties python-wxgtk2.6 python2.5 python2.5-minimal
  software-properties-gtk update-inetd update-manager-core wodim
The following packages will be upgraded:
  acpi-support acpid adduser alacarte alien alsa-base alsa-utils anacron apmd
  app-install-data app-install-data-commercial apport apport-gtk apt apt-utils
  aptitude aspell-en at at-spi avahi-daemon azureus azureus-gcj banshee
  base-files bash bc beagle bind9-host binutils binutils-static bittorrent
  bittorrent-gui bluez-cups bluez-pin bluez-utils brltty brltty-x11
  bsdmainutils bsdutils bug-buddy busybox-initramfs bzip2 ca-certificates
  capplets-data cdparanoia cdrdao cdrecord clamav-base clamav-freshclam
  cli-common console-setup console-terminus console-tools
  contact-lookup-applet coreutils cpp cpp-4.1 cron cupsys cupsys-bsd
  cupsys-client cupsys-common cupsys-driver-gutenprint dash dbus dbus-1-utils
  dc debhelper debianutils deskbar-applet desktop-file-utils dhcp3-client
  dhcp3-common dictionaries-common diff diveintopython dnsutils doc-base
  dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs
  edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes
  edgy-wallpapers eject ekiga eog esound esound-common ethtool evince
  evolution evolution-data-server evolution-data-server-common
  evolution-exchange evolution-plugins evolution-webcal example-content f-spot
  fastjar fdutils festival ffmpeg file file-roller findutils finger firefox
  firefox-gnome-support flashplugin-nonfree fontconfig fontconfig-config
  foo2zjs foomatic-db foomatic-db-engine foomatic-db-hpijs foomatic-filters
  fortune-mod fortunes-min g++ g++-4.1 gaim gaim-data gamin gcalctool gcc
  gcc-3.3-base gcc-4.1 gcc-4.1-base gcj-4.1-base gconf-editor gconf2
  gconf2-common gdb gdebi gdm gedit gedit-common gettext gettext-base gij
  gij-4.1 gimp gimp-data gimp-print gimp-python gksu gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media
  gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnupg
  gparted grep grub gs-common gs-esp gsfonts gstreamer0.10-alsa
  gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-tools gstreamer0.10-x gstreamer0.8-misc gthumb gtk2-engines
  gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs gxine gzip hal
  hal-device-manager hdparm hicolor-icon-theme hostname hotkey-setup hpijs
  hplip hplip-data human-theme hwdb-client-common hwdb-client-gnome ifupdown
  imagemagick info initramfs-tools initscripts intltool-debian iproute
  iptables iputils-arping iputils-ping iputils-tracepath iso-codes java-common
  java-gcj-compat klibc-utils klogd lame language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common language-support-en laptop-detect
  laptop-mode-tools launchpad-integration less lftp liba52-0.7.4 libacl1
  libapm1 libartsc0 libasound2 libatspi1.0-0 libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavcodec0d libavformat0d libbcprov-java libbcprov-java-gcj libbeagle0
  libbeecrypt6 libbind9-0 libblkid1 libbluetooth2 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl4
  libbz2-1.0 libcairo-java libcairo-java-gcj libcairo-perl libcairo2
  libcairomm-1.0-1 libcdio6 libcdparanoia0 libcomerr2 libconsole libcupsimage2
  libcupsys2 libcurl3 libcurl3-gnutls libdb4.3 libdbus-1-3 libdbus-glib-1-2
  libdc1394-13 libdevmapper1.02 libdjvulibre15 libdmx1 libdrm2 libdv4
  libdvdread3 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserverui1.2-8 libeel2-2 libeel2-data libenchant1c2a libendeavour2-2
  libesd-alsa0 libestools1.2 libexif12 libflac7 libfontconfig1 libfontenc1
  libfribidi0 libfs6 libgadu3 libgail-common libgail18 libgamin0 libgc1c2
  libgcc1 libgcj-bc libgcj-common libgcj7-0 libgcj7-jar libgconf2-4
  libgconf2.0-cil libgcrypt11 libgd2-noxpm libgda2-3 libgda2-common libggi2
  libgii1 libgii1-target-x libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1
  libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglade2.0-cil libglew1
  libglib-java libglib-java-gcj libglib-perl libglib1.2 libglib2.0-cil
  libglibmm-2.4-1c2a libglu1-mesa libgmime-2.0-2 libgmime2.2-cil libgmp3c2
  libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0
  libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2.0-cil
  libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecupsui1.0-1c2a
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java
  libgnutls13 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1
  libgsf-1-114 libgsf-1-common libgstreamer-gconf0.8-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins0.8-0 libgstreamer0.10-0
  libgtk-java libgtk-java-gcj libgtk-jni libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15
  libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtop2-7
  libgtop2-common libguile-ltdl-1 libgutenprint2 libgutenprintui2-1
  libhal-storage1 libhal1 libhsqldb-java libhtml-parser-perl libice6 libidl0
  libidn11 libiec61883-0 libieee1284-3 libipoddevice0 libisc11 libisccc0
  libisccfg1 libiw28 libjline-java libklibc libkpathsea4 libkrb53 liblame0
  liblaunchpad-integration0 libldap2 liblircclient0 liblog4j1.2-java
  liblpint-bonobo0 liblwres9 libmagic1 libmagick9 libmdbtools libmetacity0
  libmikmod2 libmjpegtools0c2a libmms0 libmodplug0c2 libmono-cairo1.0-cil
  libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil
  libmono-security2.0-cil libmono-sharpzip0.6-cil libmono-sharpzip0.84-cil
  libmono-sharpzip2.84-cil libmono-sqlite1.0-cil libmono-sqlite2.0-cil
  libmono-system-data1.0-cil libmono-system-data2.0-cil
  libmono-system-runtime1.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono0 libmono1.0-cil libmono2.0-cil libmpeg2-4 libmusicbrainz4c2a
  libmyspell3c2 libnautilus-burn4 libnautilus-extension1 libncurses5
  libncursesw5 libneon25 libnet-dbus-perl libnewt0.52 libnjb5 libnotify1
  libnspr4 libnss3 libogg0 liboggflac3 liboil0.3 libopal-2.2.0 libopenal0a
  libopencdk8 liborbit2 libpam-modules libpam-runtime libpam0g
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpaper1 libparted1.7-1
  libpcap0.8 libpci2 libpisock9 libpisync0 libpng12-0 libpoppler1
  libpoppler1-glib libpopt0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libqt3-mt libqthreads-12 libquicktime0 libraw1394-8
  libreadline5 librecode0 librpm4 libsasl2 libsasl2-modules libscim8c2a
  libscrollkeeper0 libsdl1.2debian libsdl1.2debian-alsa libsensors3
  libservlet2.3-java libsexy2 libsgutils1 libshout3 libsigc++-2.0-0c2a
  libslang2 libslp1 libsm6 libsmbclient libsmpeg0 libsndfile1 libsnmp-base
  libsnmp9 libsoup2.2-8 libspeex1 libsqlite3-0 libss2 libssl0.9.8
  libstartup-notification0 libstdc++5 libstdc++6 libstdc++6-4.1-dev
  libstlport4.6c2 libswfdec0.3 libswt3.2-gtk-java libswt3.2-gtk-jni libsysfs2
  libtag1c2a libtasn1-3 libtheora0 libtotem-plparser1 libungif4g libuniconf4.2
  libuuid1 libvisual-0.4-0 libvorbis0a libvorbisenc2 libvorbisfile3
  libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwpd8c2a
  libwrap0 libwvstreams4.2-base libwvstreams4.2-extras libwxgtk2.4-1 libx11-6
  libx11-data libxalan2-java libxau6 libxaw7 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxevie1 libxext6 libxfixes3 libxfont1 libxft2 libxi6
  libxine-extracodecs libxine-main1 libxine1 libxkbfile1 libxklavier11
  libxml-parser-perl libxml2 libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxss1 libxt6 libxv1 libxvidcore4 libxxf86dga1
  libxxf86misc1 libxxf86vm1 linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic linux-sound-base login lsb-base lsb-release
  lshw make makedev man-db manpages mcpp mesa-utils metacity metacity-common
  mime-support min12xxw mjpegtools mkisofs module-init-tools mono-common
  mono-gac mono-jit mono-runtime mount mozilla-firefox-locale-en-gb mplayer
  myspell-en-gb myspell-en-us nano nautilus nautilus-cd-burner nautilus-data
  nautilus-sendto ncurses-base ncurses-bin netbase notification-daemon ntpdate
  onboard openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-default
  openoffice.org-style-industrial openoffice.org-thesaurus-en-us
  openoffice.org-writer openssh-client openssl parted passwd pciutils
  pcmciautils pkg-config pnm2ppa po-debconf poppler-utils popularity-contest
  powermanagement-interface powermgmt-base powernowd ppp pppconfig pppoeconf
  procps psmisc python python-apt python-at-spi python-cairo python-central
  python-dbus python-gconf python-gdbm python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas
  python-gobject python-gst0.10 python-gtk2 python-gtkhtml2
  python-launchpad-integration python-libxml2 python-minimal python-numeric
  python-problem-report python-pyorbit python-support python-uno python-vte
  python-wxgtk2.4 python-wxversion python-xdg python-xml python2.4
  python2.4-minimal radeontool rdesktop readahead readline-common
  reiserfsprogs rhythmbox rpm rss-glx rsync samba-common scim
  scim-gtk2-immodule scim-modules-socket screen scrollkeeper serpentine
  sg3-utils shared-mime-info slocate smbclient sound-juicer sox
  ssh-askpass-gnome startup-tasks strace sun-java6-bin sun-java6-fonts
  sun-java6-jre sun-java6-plugin synaptic sysklogd system-services
  system-tools-backends sysv-rc sysvutils tangerine-icon-theme
  tango-icon-theme tango-icon-theme-common tar tasksel tasksel-data tcpd
  tcpdump telnet thunderbird-locale-en-gb tomboy toshset totem-xine tsclient
  ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts ttf-opensymbol ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg
  ubuntu-artwork ubuntu-docs ubuntu-minimal ubuntu-sounds ubuntu-standard ucf
  udev unattended-upgrades unzip update-manager update-notifier upstart
  upstart-compat-sysv upstart-logd usbutils usplash usplash-theme-ubuntu
  util-linux util-linux-locales vbetool vim-common vim-tiny vino vnc-common
  volumeid vorbis-tools w3m wget whiptail whois wireless-tools wpasupplicant
  wvdial x-ttcidfont-conf x11-common xbase-clients xcursor-themes
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xkb-data xkeyboard-config xmms xorg xpmutils xscreensaver-data
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xsltproc xterm xutils
  xutils-dev xvncviewer yelp zenity
911 upgraded, 92 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/712MB of archives.
After unpacking 388MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 114200 files and directories currently installed.)
Preparing to replace coreutils 5.96-5ubuntu4 (using .../coreutils_5.97-5.2ubuntu3_i386.deb) ...
Unpacking replacement coreutils ...
dpkg: error processing /var/cache/apt/archives/coreutils_5.97-5.2ubuntu3_i386.deb (--unpack):
 unable to stat `./usr/share/man/man1/md5sum.1.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.97-5.2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rajaiskandarshah on 2007-04-20
if you can get to gnome, then go to system > administration > synaptic package manager, then mark all upgrades, then apply. this will have ubuntu download the missing packages.

i think the error messages are because it could not download those packages (for whatever reason), hence could not install them.

---

### Post by 043087m135 on 2007-07-07
Are you sure you had all the updates installed before trying to upgrade to the next distribution? Note that with xubuntu it will NOT automatically tell you which updates to install, you have to manually hit the "check" button when opening up the update-manager. Install all the updates for 6.1 and then re-try the upgrade to Feisty. Also try to avoid the text-based upgrade. If you do attempt it make sure to do a total backup of all your important files beforehand. It may leave your system totally paralyzed, because apt-get doesn't check dependencies the same way other forms of upgrade to.

Good luck!

---

