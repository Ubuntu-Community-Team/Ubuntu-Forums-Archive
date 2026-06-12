---
title: "Xubuntu CD"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Fireware on 2007-01-04
Does anyone know somewhere that they ship free Xubuntu CD's? I cannot download it and was wondering if there is any place, safe place, that ships Xubuntu CD's for free? 

Can I install Xubuntu with only 128 MB of RAM?

---

### Post by taurus on 2007-01-04
You can install the server version and then install XFce4 after that!!!

```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by raul_ on 2007-01-04
Maybe with 128MB you should check [Fluxbuntu]("http://fluxbuntu.org/")

---

### Post by jem7v on 2007-01-04
You Could use Xubuntu, but Fluxbuntu (or Xubuntu with the Fluxbox desktop installed) will be quicker than the default XFCE environment that Xubuntu uses.  Xubuntu+Fluxbox runs fine on 400mhz/64MB RAM, but it's pretty slow when it's just running the default XFCE installation.

Taurus's idea is good though. Get a server install and just install the xubuntu-desktop if you want xubuntu without a real xubuntu disk.

---

### Post by maxamillion on 2007-01-04
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

> ShipIt

Unfortunately, unlike the other Ubuntu derivatives, Xubuntu does not yet have free cds available for shipping due to lack of funding.


---

### Post by Fireware on 2007-01-04
What does the Fluxbuntu look like? 

Could I use Ubuntu and do that command apt-get to i stall Xubuntu, cuz I have a Ubuntu CD. If so, whats to commad?

---

### Post by maxamillion on 2007-01-04
[http://fluxbuntu.org/](http://fluxbuntu.org/) <--screenshots are on the homepage

you can install xubuntu from ubuntu with the commands that taurus gave you

---

### Post by Fireware on 2007-01-04
Cool. Thanks.

---

### Post by Pobega on 2007-01-04
> sudo aptitutde install xubuntu-desktop
**or**
> sudo aptitude install xfce4

If that seems to be too slow for you, try

> sudo aptitude install fluxbox fluxconf

That will give you Fluxbox and the Fluxbox configuration utility.

---

### Post by raul_ on 2007-01-04
Remember to remove gnome desktop, othwerwise you'll fill up your hard drive:

```

sudo apt-get remove 
alacarte app-install-data-commercial apport apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cli-common contact-lookup-applet dbus-1-utils deskbar-applet desktop-file-utils edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers ekiga eog esound evince evolution evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gconf-editor gconf2 gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gray-theme gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-gnome industrialtango-theme language-selector legacyhuman-theme libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 libcairo-perl libcamel1.2-8 libcdio6 libcroco3 libdbus-1-cil libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-12 libenchant1c2a libestools1.2 libexchange-storage1.2-2 libgadu3 libgail-common libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap5 libguile-ltdl-1 libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmeanwhile1 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil libmyspell3c2 libnautilus-burn4 libnautilus-extension1 libnet-dbus-perl libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-2 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-grove-perl libxml-parser-perl libxml-perl libxml2-utils libxres1 metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon onboard openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-style-industrial outdoors-theme python-apport-utils python-at-spi python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-numeric python-problem-report python-pyorbit python-virtkey python-vte python-xdg python-xml rdesktop resilience-theme rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info silicon-theme sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity

```

from [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by Fireware on 2007-01-04
> **raul_ said:**
> Remember to remove gnome desktop, othwerwise you'll fill up your hard drive:

```

sudo apt-get remove 
alacarte app-install-data-commercial apport apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cli-common contact-lookup-applet dbus-1-utils deskbar-applet desktop-file-utils edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers ekiga eog esound evince evolution evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gconf-editor gconf2 gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gray-theme gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-gnome industrialtango-theme language-selector legacyhuman-theme libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 libcairo-perl libcamel1.2-8 libcdio6 libcroco3 libdbus-1-cil libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-12 libenchant1c2a libestools1.2 libexchange-storage1.2-2 libgadu3 libgail-common libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap5 libguile-ltdl-1 libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmeanwhile1 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil libmyspell3c2 libnautilus-burn4 libnautilus-extension1 libnet-dbus-perl libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-2 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-grove-perl libxml-parser-perl libxml-perl libxml2-utils libxres1 metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon onboard openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-style-industrial outdoors-theme python-apport-utils python-at-spi python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-numeric python-problem-report python-pyorbit python-virtkey python-vte python-xdg python-xml rdesktop resilience-theme rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info silicon-theme sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity

```

from [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

So I type all of that code and then do the Xubuntu commands?

---

### Post by raul_ on 2007-01-04
no, install xubuntu first

---

### Post by Fireware on 2007-01-04
Oh okay. Thank you.

---

### Post by raul_ on 2007-01-04
Let us know how that worked

---

### Post by Fireware on 2007-01-04
I clicked F6 and typed " sudo aptitude install xubuntu-xfce4 " and it brough me to a blue screen that says Memtest86+ v1.65 at the top left corner with stuff that says Pass (and loading or somehing) and test...

---

### Post by Fireware on 2007-01-04
Okay....I entered the text boot thing by pressing Esc. 

But it says its not it cannot find kernel image sudo ... ?

---

### Post by raul_ on 2007-01-05
U mean u didn't install ubuntu? You just typed "sudo aptitude install xubuntu-xfce4" in the boot options? you need to install ubuntu first...after you have ubuntu installed, then you can install xubuntu and remove gnome

---

### Post by jem7v on 2007-01-05
What we all mean is you need to start with a server installation and THEN install a desktop manager (such as xubuntu-desktop or whatever you want).

Look at this link. It goes over installing a lightweight system, such as you desire!
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Fireware on 2007-01-05
So Ubuntu will install on my desktop (it only has 128 MB of RAM)? 

When I do try something it just stays on the brown screen for a LONG time. Should I let it run like that for a few hours?

---

### Post by jem7v on 2007-01-06
If you only have 128 MB RAM, you probably won't be able to run the LiveCD at all.  You'll have to install from the "Alternate Install" CD (aka the Text Installer) because it doesn't install from a GUI and doesn't need as much RAM to run.

---

