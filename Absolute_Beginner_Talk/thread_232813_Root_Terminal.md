---
title: "Root Terminal"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2006-08-09
Root terminal no longer ask me for a password since i updated my reposities to intsall wine which didn't work.

---

### Post by smile-its-smiley on 2006-08-09
Weird, the root terminal now asks for a password but i still cant install wine help please.

---

### Post by smile-its-smiley on 2006-08-09
This is very weird it no longer asks for a password, help whats going on?

---

### Post by philippe_carlo on 2006-08-09
Are you using sudo/gksudo? Sudo remebers the password for the remainder of the sessions, once you have provide it first. What error do you get with wine?

---

### Post by smile-its-smiley on 2006-08-09
root@sam-laptop:/home/sam# sudo aptitude install wine
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for wine
The following packages have been kept back:
app-install-data-commercial avm-fritz-firmware base-files cupsys
cupsys-bsd cupsys-client eog epiphany-browser file-roller gdm gedit
gedit-common gimp-python gnome-about gnome-accessibility-themes
gnome-applets gnome-applets-data gnome-desktop-data gnome-games
gnome-games-data gnome-menus gnome-panel gnome-panel-data
gnome-screensaver gnome-session gnome-themes gnupg gstreamer0.10-alsa
gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines-clearlooks
gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
gtkhtml3.8 kdelibs-bin kdelibs-data kdelibs4c2a kopete krdc krfb
language-pack-en language-pack-en-base language-pack-gnome-en
language-pack-gnome-en-base language-selector language-selector-common
libcupsimage2 libcupsys2 libeel2-2 libeel2-data libfreetype6 libgimp2.0
libgnome-desktop-2 libgnome-menu2 libgnomecups1.0-1 libgnomeui-0
libgnomeui-common libgstreamer-plugins-base0.10-0 libgtk2.0-0
libgtk2.0-bin libgtk2.0-common libgtkhtml3.8-15 libgtksourceview-common
libgtksourceview1.0-0 libnautilus-burn3 libnautilus-extension1
libpanel-applet2-0 libpango1.0-0 libpango1.0-common libruby1.8
libsmbclient libtiff4 libtotem-plparser1 libtunepimp-bin libtunepimp2c2a
libwmf0.2-7 libxine-main1 linux-386 linux-headers-386 linux-image-386
linux-restricted-modules-386 linux-restricted-modules-common
localechooser-data login nautilus nautilus-cd-burner nautilus-data
openoffice.org openoffice.org-base openoffice.org-calc
openoffice.org-common openoffice.org-core openoffice.org-draw
openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
openoffice.org-impress openoffice.org-java-common
openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
passwd pmount ppp python-gmenu python-uno samba-common smbclient totem
totem-gstreamer ttf-opensymbol ubuntu-base ubuntu-minimal ubuntu-standard
xserver-xorg-core xserver-xorg-input-mouse yelp zenity
0 packages upgraded, 0 newly installed, 0 to remove and 127 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
redhat-cluster-suite depends on clvm; however:
Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
system-config-cluster depends on redhat-cluster-suite; however:
Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
clvm
redhat-cluster-suite
system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
redhat-cluster-suite depends on clvm; however:
Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
system-config-cluster depends on redhat-cluster-suite; however:
Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
clvm
redhat-cluster-suite
system-config-cluster
root@sam-laptop:/home/sam#

---

