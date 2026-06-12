---
title: "remove pmount without dependencies"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-06-16
Is there ANY Possible way to remove "pmount", without actually removing all of the dependencies that tag along with it?

My pmount is messed up, as it won't mount a portable device, and it's quite frustrating, but if I remove pmount from synaptic, it removes a boat load of dependencies, that make my system work!

I don't want to start a fresh, by reinstalling my OS, but want to remove pmount, and then reinstall it.

Any suggestions or ideas how to do this, or how to correct my problem?

Dr Small

---

### Post by Inxsible on 2007-06-22
What happens when you try 

```
sudo apt-get remove pmount
```

---

### Post by RTrev on 2007-06-23
> **Dr Small said:**
> Is there ANY Possible way to remove "pmount", without actually removing all of the dependencies that tag along with it?

My pmount is messed up, as it won't mount a portable device, and it's quite frustrating, but if I remove pmount from synaptic, it removes a boat load of dependencies, that make my system work!

I don't want to start a fresh, by reinstalling my OS, but want to remove pmount, and then reinstall it.

Any suggestions or ideas how to do this, or how to correct my problem?

Dr Small

Can you just mark it for reinstallation in Synaptic?

---

### Post by Dr Small on 2007-06-30
> **Inxsible said:**
> What happens when you try 

```
sudo apt-get remove pmount
```
```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  alacarte automatix2 bug-buddy contact-lookup-applet deskbar-applet ekiga eog
  evince evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal file-roller firestarter gcalctool gconf-editor gdesklets
  gdesklets-data gedit gnome-about gnome-app-install gnome-applets
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
  gnome-media gnome-menus gnome-netstatus-applet gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-utils gnome-volume-manager gnomesword gnopernicus gok
  gstreamer0.10-gnomevfs gstreamer0.8-gnomevfs gthumb gtkhtml3.8 gucharmap
  hal-device-manager hwdb-client inkscape libbonoboui2-0 libebook1.2-5
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6
  libeel2-2 libexchange-storage1.2-1 libgail-gnome-module libgdl-1-0
  libgdl-1-common libgnome-desktop-2 libgnome-menu2 libgnome2-0 libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra
  libgtkhtml3.8-15 libgucharmap4 liblpint-bonobo0 libnautilus-extension1
  libpanel-applet2-0 libtotem-plparser1 nautilus nautilus-cd-burner
  nautilus-sendto openoffice.org-gnome pmount python-gmenu python-gnome2
  python-gnome2-desktop python-gnome2-extras python2.4-gnome2
  python2.4-gnome2-desktop python2.4-gnome2-extras rhythmbox serpentine
  sound-juicer soundconverter totem totem-xine totem-xine-firefox-plugin
  tsclient update-notifier vino yelp
0 upgraded, 0 newly installed, 105 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 276MB disk space will be freed.
Do you want to continue [Y/n]?
```

So that wouldn't work, and reinstalling didn't help from Synaptic....

Dr Small

---

### Post by Dr Small on 2007-06-30
And, and here is the output when I use aptitude:
```
drsmall@drsmall:~$ sudo aptitude remove pmount
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-volume-manager libgnomevfs2-common
The following packages will be REMOVED:
  pmount
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 168kB will be freed.
The following packages have unmet dependencies:
  gnome-volume-manager: Depends: pmount but it is not installable
  libgnomevfs2-common: Depends: pmount (>= 0.9.5-0ubuntu4) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
pmount [0.9.11-1ubuntu1 (dapper-updates, now) -> 0.9.11-1 (dapper)]

Score is -39

Accept this solution? [Y/n/q/?]

```

Any ideas of what I should do?

Dr Small

---

### Post by RTrev on 2007-06-30
Are you certain you even need pmount?  I just looked on my own Ubuntu Feisty 64-bit install, and I don't have it installed at all.  I do have mount, and gnome-mount installed.

Just a thought...

---

### Post by Dr Small on 2007-06-30
After months of having this problem, I have finally traced the source of the problem, and solved it. It was rather simple, and I was stupid not to look there first.

I kept getting a Permission Denied type error, saying I wasn't having permission to mount or unmount the portable/cdrom drive. So, I tried changing permissions on /usr/bin/pmount, but didn't get much there, so I looked aroundin System > Administration > Users and Groups, went to my account (drsmall), went to the "User Privilages" Tab, and checked:
Enable Access to external storage devices automatically.

Of course, since I was messing with the permissions on pmount, i kept still getting the error, so I reinstalled pmount via synaptic and plugged in my usb flash drive and it all worked :)

Thanks for all the help!
Dr Small

---

