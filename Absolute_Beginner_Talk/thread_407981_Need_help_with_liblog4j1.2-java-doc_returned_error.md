---
title: "Need help with liblog4j1.2-java-doc returned error."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wedshot on 2007-04-12
Hi all,
I'm running Dapper Drake and when I download from synaptic I always get this prompt : liblog4j1.2-java-doc, Subprocess post-installation script returned error exit ststus 2.
I'm having a hard time figuring out what this is for.  Help please.
wedshot

---

### Post by Seisen on 2007-04-13
Try typing this in the command line and see if it works.

```
sudo dpkg --configure -a
sudo aptitude -f install
```

---

### Post by wedshot on 2007-04-15
Seisen:  I ran those commands in the terminal and got the following response:
sudo dpkg --configure -a
sudo aptitude -f install sudo dpkg --configure -a
sudo aptitude -f install wedshot@wedshot-desktop:~$ sudo dpkg --configure -a
Password:
wedshot@wedshot-desktop:~$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  ffmpeg ffmpeg2theora python-wxgtk2.6 totem ubuntu-desktop
The following NEW packages will be installed:
  gnome-desktop-environment gnome-fifth-toe
The following packages will be REMOVED:
  gnome-vlc gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-good-doc gvlc kaffeine kaffeine-xine kfaxview
  kviewshell libarts1-xine libdc1394-13 libdvbpsi4 libggi2 libgii0
  libgii0-target-x libglide2 libgstreamer-plugins-base0.10-dev
  libgstreamer0.10-0-dbg libgstreamer0.10-dev libiso9660-4 libsvga1 libtar
  libvcdinfo0 libvlc0-dev libwxgtk2.6-0 libxosd2 libxv1-dbg libxvmc1-dbg
  mozilla-plugin-vlc qvlc vlc vlc-plugin-alsa vlc-plugin-arts
  vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl
  vlc-plugin-svgalib wxvlc xvfb
0 packages upgraded, 4 newly installed, 40 to remove and 0 not upgraded.
Need to get 23.6kB/51.4kB of archives. After unpacking 61.6MB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: libesd-alsa0 but it is not installable
  ffmpeg2theora: Depends: libdc1394-13 but it is not installable
  ffmpeg: Depends: libdc1394-13 but it is not installable
  python-wxgtk2.6: Depends: libwxgtk2.6-0 (>= 2.6.1.2ubuntu2) but it is not installable
  totem: Depends: totem-gstreamer (>= 1.4.3-0ubuntu1) but it is not installable or
                  totem-xine (>= 1.4.3-0ubuntu1) but 1.4.1-0ubuntu4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
totem [1.4.1-0ubuntu4 (dapper)]

Keep the following packages at their current version:
gnome-desktop-environment [Not Installed]
gnome-fifth-toe [Not Installed]
libdc1394-13 [1.1.0-3 (dapper, now)]
libgstreamer0.10-dev [0.10.6-0ubuntu2 (dapper, now)]
libwxgtk2.6-0 [2.6.1.2ubuntu2 (dapper, now)]
ubuntu-desktop [Not Installed]

Score is -342

Accept this solution? [Y/n/q/?]
wedshot@wedshot-desktop:~$ y
bash: y: command not found
wedshot@wedshot-desktop:~$ Y
bash: Y: command not found

I'm not sure what it's all about but it looks to me like I'm behind 342 to zip

---

### Post by Seisen on 2007-04-15
It's telling you that Ubuntu Desktop isn't installed as well as some other packages, run the aptitude -f install again and when it ask's you "Accept this selection" type in Y and hit Enter. Let me know what happen's after that.

---

### Post by wedshot on 2007-04-17
Here's what I got

wedshot@wedshot-desktop:~$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  ffmpeg ffmpeg2theora python-wxgtk2.6 ubuntu-desktop
The following NEW packages will be installed:
  gnome-desktop-environment gnome-fifth-toe
The following packages will be REMOVED:
  gnome-vlc gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-good-doc gvlc kaffeine kaffeine-xine kfaxview
  kviewshell libarts1-xine libdc1394-13 libdvbpsi4 libggi2 libgii0
  libgii0-target-x libglide2 libgstreamer-plugins-base0.10-dev
  libgstreamer0.10-0-dbg libgstreamer0.10-dev libiso9660-4 libsvga1 libtar
  libvcdinfo0 libvlc0-dev libwxgtk2.6-0 libxosd2 libxv1-dbg libxvmc1-dbg
  mozilla-plugin-vlc qvlc vlc vlc-plugin-alsa vlc-plugin-arts
  vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl
  vlc-plugin-svgalib wxvlc xvfb
0 packages upgraded, 3 newly installed, 40 to remove and 0 not upgraded.
Need to get 37.4kB of archives. After unpacking 61.6MB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: deskbar-applet but it is not installable
                  Depends: libesd-alsa0 but it is not installable
                  Depends: rhythmbox but it is not installable
                  Depends: serpentine but it is not installable
  ffmpeg2theora: Depends: libdc1394-13 but it is not installable
  ffmpeg: Depends: libdc1394-13 but it is not installable
  python-wxgtk2.6: Depends: libwxgtk2.6-0 (>= 2.6.1.2ubuntu2) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-desktop-environment [Not Installed]
gnome-fifth-toe [Not Installed]
libdc1394-13 [1.1.0-3 (dapper, now)]
libgstreamer0.10-dev [0.10.6-0ubuntu2 (dapper, now)]
libwxgtk2.6-0 [2.6.1.2ubuntu2 (dapper, now)]
ubuntu-desktop [Not Installed]

Score is -252

Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  gnome-vlc gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-good-doc gvlc kaffeine kaffeine-xine kfaxview
  kviewshell libarts1-xine libdvbpsi4 libggi2 libgii0 libgii0-target-x
  libglide2 libgstreamer-plugins-base0.10-dev libgstreamer0.10-0-dbg
  libiso9660-4 libsvga1 libtar libvcdinfo0 libvlc0-dev libxosd2 libxv1-dbg
  libxvmc1-dbg mozilla-plugin-vlc qvlc vlc vlc-plugin-alsa vlc-plugin-arts
  vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl
  vlc-plugin-svgalib wxvlc xvfb
0 packages upgraded, 0 newly installed, 37 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 50.6MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 243578 files and directories currently installed.)
Removing gnome-vlc ...
Removing gstreamer0.10-plugins-base-dbg ...
Removing gstreamer0.10-plugins-good-dbg ...
Removing gstreamer0.10-plugins-good-doc ...
Removing gvlc ...
Removing kfaxview ...
Removing kviewshell ...
Removing libarts1-xine ...
Removing qvlc ...
Removing vlc-plugin-svgalib ...
Removing vlc-plugin-sdl ...
Removing vlc-plugin-glide ...
Removing vlc-plugin-ggi ...
Removing vlc-plugin-esd ...
Removing vlc-plugin-arts ...
Removing mozilla-plugin-vlc ...
dpkg - warning: while removing mozilla-plugin-vlc, directory `/usr/lib/mozilla-firefox/components' not empty so not removed.
Removing libvlc0-dev ...
Removing libggi2 ...
Removing libglide2 ...
Removing libgstreamer-plugins-base0.10-dev ...
Removing libgstreamer0.10-0-dbg ...
Removing libsvga1 ...
Removing libxv1-dbg ...
Removing libxvmc1-dbg ...
Removing xvfb ...
Removing libgii0 ...
Removing libgii0-target-x ...
Removing wxvlc ...
Removing vlc ...
Removing libdvbpsi4 ...
Removing libvcdinfo0 ...
Removing libiso9660-4 ...
Removing libtar ...
Removing libxosd2 ...
Removing kaffeine ...
Removing kaffeine-xine ...
Removing vlc-plugin-alsa ...
wedshot@wedshot-desktop:~$

My score is up to -252.  I'm feeling better already

---

### Post by Seisen on 2007-04-17
Now you need to reinstall ubuntu-desktop.

```
sudo aptitude install ubuntu-desktop
```

---

### Post by wedshot on 2007-04-17
Thanks Seisen:  Everything seems to be running much smoother now.
Wedsot
(closed)

---

