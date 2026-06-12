---
title: "XFCE on ubuntu 7.10???"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by grrrlshapedthing on 2008-01-21
SO I have Ubuntu 7.10 with a LAMP localhost set up, and have been using this for a bit now and don't really want to do a reinstall, and like how i have everything set up... but i would just like to have xfce instead of gnome without switching to xbuntu is that possible? I'm not really in love with and gnome specific apps so i don't mind having to change some of the apps....

Thanks in advance for any help

---

### Post by mali2297 on 2008-01-21
Yes, of course. Either install the meta package **xubuntu-desktop** or **xfce4**. (The latter is smaller.)

If you want to get rid of gnome in the process, I think this will do it:
```

sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop

```

---

### Post by grrrlshapedthing on 2008-01-21
> **mali2297 said:**
> Yes, of course. Either install the meta package **xubuntu-desktop** or **xfce4**. (The latter is smaller.)

If you want to get rid of gnome in the process, I think this will do it:
```

sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop

```

will this delete any of the settings I currently have like in thunderbird? or firefox?  thanks again

---

### Post by mali2297 on 2008-01-21
> **grrrlshapedthing said:**
> will this delete any of the settings I currently have like in thunderbird? or firefox?  thanks again

No, your personal settings (bookmarks etc) are stored in a hidden directory .mozilla in your home folder. Even if firefox would be removed by the package manager, these settings are kept.

---

