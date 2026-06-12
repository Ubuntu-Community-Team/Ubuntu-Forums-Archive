---
title: "Switch from Ubuntu to Xubuntu? [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by dzqm on 2007-04-26
Fiesty is killing my system and not letting me uninstall Evolution (WebCal), BitTorrent, etc., and many other things that I have no use for. Apparently, all of these depend on "Ubuntu-Desktop" which Synaptic advises users not to uninstall for proper functioning of the system.
My poor system (an eMachines desktop with 1.3GHz processor and 128MB RAM) is trying to cope with this bloat as I try to find a solution.
Therefore, my question is this: is there anyway to replace the GNOME/KDE environments with the Xubuntu system? Thanx in advance.

---

### Post by lamalex on 2007-04-27
apt-get install xubuntu-desktop

you can uninstall ubuntu-desktop and not break anything. It will just effect dist-upgrades. There are tons of posts about this. So go ahead and uninstall that stuff. You should be ok.

---

### Post by TheMono on 2007-04-27
First, do 

sudo apt-get install xubuntu-desktop

then, do 

sudo apt-get remove alacarte aspell binfmt-support bittorrent bluez-cups bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dcraw deskbar-applet desktop-effects dhcdbd diveintopython ekiga eog esound espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gedit gedit-common gij gij-4.1 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-keyring-manager gnome-media gnome-media-common gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager hwdb-client-common hwdb-client-gnome libaudio2 libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcucul0 libcurl3 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj7-0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomevfs2-bin libgnomevfs2-extra libgphoto2-2 libgphoto2-port0 libgpod1 libgstreamer-plugins-base0.10-0 libgtk2-perl libgtk2.0-cil libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgucharmap6 libguile-ltdl-1 libhsqldb-java libicu36 libidn11 libiec61883-0 libieee1284-3 libjaxp1.3-java libjline-java liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmusicbrainz4c2a libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon25 libnl1-pre6 libnm-util0 liboil0.3 libopal-2.2.0 libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraw1394-8 libsane libservlet2.3-java libshout3 libslab0 libsndfile1 libsoup2.2-8 libstlport5.1 libtotem-plparser1 libungif4g libvisual-0.4-0 libvorbisenc2 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager network-manager-gnome openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-desktop python-gnome2-extras python-gst0.10 python-libxml2 python-uno rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer totem-mozilla tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds update-notifier usplash-theme-ubuntu vino whois xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop


Done. (credit to aysiu of [www.psychocats.net](www.psychocats.net) for the code)

---

### Post by dzqm on 2007-04-27
Wow! Didn't expect a reply this soon.
Thanks guys.
Gonna give this a shot and will let you know how it goes.

---

### Post by dzqm on 2007-04-27
Worked perfectly. And the computer now works like a charm!! Thanks again, both of you.

---

