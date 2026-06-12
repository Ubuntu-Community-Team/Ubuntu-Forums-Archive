---
title: "Removing xubuntu / xubuntu-desktop from a KDE/Kubuntu install"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by eyemou on 2007-08-07
Hi,

I looked around on the forums for a bit, and while I found posts about folks wanting to remove xubuntu, I didn't see my specific problem addressed...

Out of curiosity, I decided to play around with xubuntu, so I installed (apt-get install xubuntu-desktop) the desktop on my KDE/Feisty system.

In doing so, 170 packages (~396mb) were installed (I'll post a list at the end of this post).

Anyhow, I really wasn't into xubuntu, so I logged back into KDE and attempted to apt-get remove xubuntu-desktop.

Here's what came back (I opted NOT to go ahead with the uninstall until I learned more):

[I]
The following packages were automatically installed and are no longer required:
  python-gst0.10 python-gnome2 kdegames-card-data libgnomeui-common python-gnome
  gstreamer0.10-gnomevfs gstreamer0.10-gnonlin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 41.0kB disk space will be freed.[/i]

...which is a far cry from the 170 packages / ~395mb. Is there a way to easily (short of manually removing each one -- thankfully I copied/pasted a list!) remove everything that was installed with xubuntu-desktop?

Here's what was installed:
[i]
The following extra packages will be installed:
  abiword abiword-common abiword-plugins anthy app-install-data-commercial
  apport-gtk dbus-1-utils evince-gtk feisty-gdm-themes feisty-session-splashes
  feisty-wallpapers gcalctool-gtk gdebi gdebi-core gdm gimp-print gksu
  gnome-accessibility-themes gnome-app-install gnome-icon-theme gnome-mount
  gnumeric-common gnumeric-gtk gqview gtk2-engines gtk2-engines-pixbuf
  gtk2-engines-ubuntulooks gtk2-engines-xfce hal-cups-utils hplip
  human-cursors-theme human-icon-theme human-theme language-selector
  libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a
  libanthy0 libchewing3 libchewing3-data libenchant1c2a libexo-0.3-0
  libgail-common libgail18 libgdome2-0 libgdome2-cpp-smart0c2a libgksu2-0
  libglib2.0-data libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgoffice-0-common
  libgoffice-gtk-0-3 libgtkhtml2-0 libgtkmathview0c2a libgtop2-7
  libgtop2-common libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libkpathsea4 libnet-dbus-perl libnotify1 liboobs-1-3
  libots0 libpoppler1-glib libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2
  liburi-perl libvte-common libvte9 libwnck-common libwnck18 libwpd-stream8c2a
  libwww-perl libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4
  libxfcegui4-4 libxklavier11 libxml-parser-perl libxml-twig-perl libxres1
  mousepad mozilla-thunderbird notification-daemon onboard orage python-cups
  python-exo python-gdbm python-gtkhtml2 python-launchpad-integration
  python-notify python-virtkey python-vte python-xml restricted-manager scim
  scim-anthy scim-chewing scim-gtk2-immodule scim-hangul scim-modules-socket
  scim-modules-table scim-pinyin scim-tables-additional
  software-properties-gtk synaptic system-config-printer system-tools-backends
  tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin
  thunar-doc thunar-media-tags-plugin thunar-volman-plugin ubuntu-artwork
  update-manager vim-runtime vnc-common xarchiver xfburn xfce4-appfinder
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin
  xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer
  xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin
  xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin
  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes
  xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork-usplash
  xubuntu-default-settings xubuntu-docs xubuntu-system-tools xvncviewer zenity
Suggested packages:
  msttcorefonts gutenprint-doc gutenprint-locales gnome-themes totem
  cryptsetup gnumeric-doc gnumeric-plugins-extra xpaint gtk-engines-pixmap
  kdeprint gtklp xpp hpijs-ppds hplip-doc libio-socket-ssl-perl
  libunicode-map8-perl libunicode-string-perl
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector
  mozilla-thunderbird-enigmail python-exo-dbg python-gnome2-extras-doc
  python-launchpad-integration-dbg python-vte-dbg python-xml-dbg scim-uim
  scim-m17n scim-prime scim-skk scim-canna scim-tables-ja scim-tables-ko
  scim-tables-zh kasumi ttf-unfonts ttf-alee dwww vncserver menu a2ps netpbm
  xfishtank xdaliclock qcam streamer ssh
Recommended packages:
  abiword-help latex-xft-fonts update-notifier ubuntu-sounds python-reportlab
  libmailtools-perl libhtml-format-perl libtie-ixhash-perl libxml-xpath-perl
  im-switch deborphan libgnome2-perl arj rpm p7zip xli xloadimage
The following NEW packages will be installed:
  abiword abiword-common abiword-plugins anthy app-install-data-commercial
  apport-gtk dbus-1-utils evince-gtk feisty-gdm-themes feisty-session-splashes
  feisty-wallpapers gcalctool-gtk gdebi gdebi-core gdm gimp-print gksu
  gnome-accessibility-themes gnome-app-install gnome-icon-theme gnome-mount
  gnumeric-common gnumeric-gtk gqview gtk2-engines gtk2-engines-pixbuf
  gtk2-engines-ubuntulooks gtk2-engines-xfce hal-cups-utils hplip
  human-cursors-theme human-icon-theme human-theme language-selector
  libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a
  libanthy0 libchewing3 libchewing3-data libenchant1c2a libexo-0.3-0
  libgail-common libgail18 libgdome2-0 libgdome2-cpp-smart0c2a libgksu2-0
  libglib2.0-data libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgoffice-0-common
  libgoffice-gtk-0-3 libgtkhtml2-0 libgtkmathview0c2a libgtop2-7
  libgtop2-common libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libkpathsea4 libnet-dbus-perl libnotify1 liboobs-1-3
  libots0 libpoppler1-glib libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2
  liburi-perl libvte-common libvte9 libwnck-common libwnck18 libwpd-stream8c2a
  libwww-perl libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4
  libxfcegui4-4 libxklavier11 libxml-parser-perl libxml-twig-perl libxres1
  mousepad mozilla-thunderbird notification-daemon onboard orage python-cups
  python-exo python-gdbm python-gtkhtml2 python-launchpad-integration
  python-notify python-virtkey python-vte python-xml restricted-manager scim
  scim-anthy scim-chewing scim-gtk2-immodule scim-hangul scim-modules-socket
  scim-modules-table scim-pinyin scim-tables-additional
  software-properties-gtk synaptic system-config-printer system-tools-backends
  tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin
  thunar-doc thunar-media-tags-plugin thunar-volman-plugin ubuntu-artwork
  update-manager vim-runtime vnc-common xarchiver xfburn xfce4-appfinder
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin
  xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer
  xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin
  xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin
  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes
  xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork-usplash
  xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-system-tools
  xvncviewer zenity
0 upgraded, 170 newly installed, 0 to remove and 0 not upgraded.
[/i]
Any insight GREATLY appreciated.

Thanks!!

---

### Post by bodhi.zazen on 2007-08-07
Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
	Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)

	[http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop)

	[http://doc.gwos.org/index.php/Install/remove_%28K%2CX%2CEd%29ubuntu-desktop_packages](http://doc.gwos.org/index.php/Install/remove_%28K%2CX%2CEd%29ubuntu-desktop_packages)

	Pure gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
	Pure KDE: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
	Pure XFCE: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Sorry I did not read your long post ...

---

### Post by overdrank on 2007-08-07
> **bodhi.zazen said:**
> Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
	Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)

	[http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_ubuntu-desktop)

	[http://doc.gwos.org/index.php/Install/remove_%28K%2CX%2CEd%29ubuntu-desktop_packages](http://doc.gwos.org/index.php/Install/remove_%28K%2CX%2CEd%29ubuntu-desktop_packages)

	Pure gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
	Pure KDE: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
	Pure XFCE: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Sorry I did not read your long post ...

Thanks for the links! :popcorn:

---

### Post by eyemou on 2007-08-07
Awesome -- thanks!

---

### Post by bodhi.zazen on 2007-08-07
> **overdrank said:**
> Thanks for the links! :popcorn:

You are most welcome, but we should give thanks to **[color=brown]aysiu[/color]** as well ;)

---

### Post by strabes on 2007-08-11
You really should have use aptitude to install it. That way, when you removed xubuntu-desktop with aptitude it would have removed all of the other packages that came with it.```
sudo aptitude install xubuntu-desktop
sudo aptitude remove xubuntu-desktop
```

---

