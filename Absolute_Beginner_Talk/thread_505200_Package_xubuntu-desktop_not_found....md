---
title: "Package xubuntu-desktop not found..."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-20
sources.list is shown here:

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted
universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted
universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse



Also, I only just copy-pasted these in and did sudo apt-get update (I'm using Knoppix 3.8 trying to install xubuntu-desktop). Should I do sudo apt-get dist-upgrade as well? Everytime I do, it never installs something or other and the gui disappears,so I'm rather scared to try it.

---

### Post by Outrunner on 2007-07-20
Knoppix doesn't have an 'xubuntu-desktop' metapackage, it's something specific to Ubuntu. Try searching for 'xfce' and see what you can find
```

aptitude search xfce
```

---

### Post by ARandomKid on 2007-07-20
aptitude search wasn't found, so I did apt-cache search xfce. Got this:

> alltray - Dock any program into the system tray
desktop-profiles - framework for setting up desktop profiles
gmessage - an xmessage clone based on GTK+
kdocker - minimize all applications to system tray
netgo - network configuration tool for Kde
python-xfce - Python bindings for Xfce
xfce4 - meta-package for xfce4 dependencies
xfce4-artwork - additional artwork for the Xfce4 Desktop Environment
xfce4-cpu-freq-plugin - display the CPU informations in the Xfce panel
xfce4-cpufreq-plugin - cpufreq information plugin for the Xfce4 panel
xfce4-datetime-plugin - date and time plugin for the Xfce4 panel
xfce4-dev-tools - Xfce4 development tools
xfce4-diskperf-plugin - disk performance display plugin for the Xfce4 panel
xfce4-genmon-plugin - Generic Monitor for the Xfce4 panel
xfce4-goodies - enhancements for the Xfce4 Desktop Environment
xfce4-messenger-plugin - Dbus messages plugin for xfce4-panel
xfce4-minicmd-plugin - Mini-command line plugin for the Xfce4 panel
xfce4-mpc-plugin - Xfce panel plugin which serves as client for MPD music player
xfce4-radio-plugin - v4l radio control plugin for the Xfce4 panel
xfce4-sensors-plugin - hardware sensors plugin for the Xfce4 panel
xfce4-wavelan-plugin - wavelan status plugin for the Xfce4 panel
xfce4-xfapplet-plugin - Gnome applets plugin for Xfce panel
xfce4-xmms-plugin - xmms plugin for the Xfce panel
xfmedia - Xfce media player
xfmedia-dev - The Xfmedia development files
xfce4-theme-brushedchrome - BrushedChrome theme for Xfwm4 and Gtk+ 2.0
istanbul - Desktop session recorder producing Ogg Theora video
mail-notification - mail notification in system tray
mail-notification-evolution - evolution support for mail notification


---

