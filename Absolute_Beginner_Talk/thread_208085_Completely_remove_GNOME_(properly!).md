---
title: "Completely remove GNOME (properly!)"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-07-03
Hi,

I want to completely remove GNOME and any GNOME-based apps from my installation.

I do not want to remove my installations of apache/mysql and the like.

I am not comfortable enough with aptitude to do this through it, so I would prefer a simple apt-get remove command (or multiple) that allows me to see which packages will be removed.

Thanks

---

### Post by uzi09 on 2006-07-03
[http://psychocats.net/ubuntu/purekde.php](http://psychocats.net/ubuntu/purekde.php)

---

### Post by user1397 on 2006-07-03
[quote=Kurt`]Hi,

I want to completely remove GNOME and any GNOME-based apps from my installation.

I do not want to remove my installations of apache/mysql and the like.

I am not comfortable enough with aptitude to do this through it, so I would prefer a simple apt-get remove command (or multiple) that allows me to see which packages will be removed.

Thanks[/quote]what do you want instead?  pure kde or pure xfce?

---

### Post by Kurt` on 2006-07-03
[QUOTE=erik1397]what do you want instead?  pure kde or pure xfce?[/QUOTE]
I don't want *anything* on there. :)

Machine is changing roles to a server temporarily. I originally had GNOME on there just to benchmark performance, then I got carried away and installed and configured tons of stuff, and would prefer not to have to wipe the system.

---

### Post by uzi09 on 2006-07-03
just basically follow the same guide i provided, but don't install KDE when you get to it.

---

### Post by user1397 on 2006-07-03
[quote=Kurt`]I don't want *anything* on there. :)

Machine is changing roles to a server temporarily. I originally had GNOME on there just to benchmark performance, then I got carried away and installed and configured tons of stuff, and would prefer not to have to wipe the system.[/quote]to remove gnome: ```
sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
```

---

### Post by uzi09 on 2006-07-03
you should really use aptitude instead of apt-get there erik
here's why....
[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

btw, i thought i saw you provide this same link to someone else too, maybe you forgot :S

---

### Post by Kurt` on 2006-07-03
[QUOTE=uzi09]you should really use aptitude instead of apt-get there erik
here's why....
[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

btw, i thought i saw you provide this same link to someone else too, maybe you forgot :S[/QUOTE]
Interesting, thanks for the link! :)

---

### Post by aysiu on 2006-07-03
Warning: this may, in fact, remove Apache/MySQL, which you said you did **not** want removed.

*aptitude*, like *apt-get* will warn you about what packages are to be removed, but I have seen at least two posts indicating that my "pure KDE" and "pure Gnome" tutorials remove Apache/MySQL/PHP.

What do you want to have left over--just KDE? Just XFCE? Just a server?

---

### Post by user1397 on 2006-07-03
[quote=uzi09]you should really use aptitude instead of apt-get there erik
here's why....
[http://psychocats.net/ubuntu/aptitude.php]("http://psychocats.net/ubuntu/aptitude.php")

btw, i thought i saw you provide this same link to someone else too, maybe you forgot :S[/quote]but you see, he did not install gnome with aptitude (AFAIK), so therefore uninstalling it with aptitude wouldn't work.

---

