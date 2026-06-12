---
title: "HELP! Upgrade stacked pc and now wont boot."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-20
i was updating from 6.10 to 7.04 and it stacked (stalled) during stopping bluetooth devices.now i can't boot any kernals (6.0.6/6.10) in normal mode or recovery... i'm typing this on the live cd.how do i fix and restore my 6.10 and redo the upgrade without formatting and loosing all my data?
is there any way around this.please help!

EDIT: just remembered it says |Waiting for root filesystem" and goes no further

---

### Post by keef247 on 2007-04-20
tried using a live cd and had these errors:
```
  librdf0 librecode0 libruby1.8 libscim8c2a libsmjs1 libstlport4.6c2
  libtext-glob-perl libuniconf4.2 libwmf0.2-7 libwvstreams4.2-base
  libwvstreams4.2-extras libxine-extracodecs libxine-main1 libxml-libxml-perl
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
392 upgraded, 46 newly installed, 1 to remove and 0 not upgraded.
348 not fully installed or removed.
Need to get 77.2kB/318MB of archives.
After unpacking 250MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com feisty/universe libopenalpp-cvs1 20060714-3build2 [61.8kB]
Get:2 http://archive.ubuntu.com feisty/universe libopenthreads4 1.2.0-2build1 [15.4kB]
Fetched 77.2kB in 0s (83.0kB/s)
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
Preparing to replace libopenal0a 1:0.0.8-1ubuntu1 (using .../libopenal0a_1%3a0.0.8-3_i386.deb) ...
Unpacking replacement libopenal0a ...
Preparing to replace libopenalpp-cvs1 20060714-3build1 (using .../libopenalpp-cvs1_20060714-3build2_i386.deb) ...
Unpacking replacement libopenalpp-cvs1 ...
Errors were encountered while processing:
 /var/cache/apt/archives/bluez-utils_3.9-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

