---
title: "Restoring Original Video Settings!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-04
Hello!

I installed Ubuntu a few days ago and I was trying to set up my ATI Radeon 200M video card and also trying to install beryl.
I think I made a mess on the way.  Installed mesa drivers and other drivers and edited my xorg,conf file.

Is there a way to restore everything to the original state? Both the xorg.conf file and remove all the video drivers and re-installed them?

Thanks

---

### Post by taurus on 2007-06-04
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by matteospqr on 2007-06-04
Thanks! I did that and I assume it created a new xorg,conf file? What about the drivers part?  Should I remove them some how? Or should I try and download them again from the ATI website?

---

### Post by matteospqr on 2007-06-04
I also tried to type: glxinfo | grep vendor and I get

matteo@matteo:~$ glxinfo | grep vendor
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)


what does the "missing on display" part mean? I also dont know how to get rid of the Mesa part!

HELP!! I am a newby and very confused! :)

---

### Post by taurus on 2007-06-04
How did you install that mesa driver?  If you installed it with synaptic, then remove it from synaptic.  And if you install it with apt-get/aptitude, then remove it with

```
sudo apt-get remove program_name
-or-
sudo aptitude remove program_name
```
And if you installed it with dpkg, then try

```
sudo dpkg -r program_name
```

---

### Post by matteospqr on 2007-06-04
I installed those Masa drivers while I was trying to install beryl.  I did:


sudo apt-get remove xorg-driver-fglrx; 

sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

---

### Post by matteospqr on 2007-06-04
The problem I encounter when I try and removed them with apt-get is that it wants to also get rid of a bunch of other stuff like xorg and desktop linux...more than 300mb of stuff.  I am afraid X wont even start anymore if I delete the masa.

Clueless...

---

### Post by matteospqr on 2007-06-04
This is what I get when I try and remove masa:


matteo@matteo:~$ sudo apt-get remove libgl1-mesa-glx libgl1-mesa-dri
Password:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kalzium-data libavahi-qt3-1 libarts1c2a libwxbase2.6-0 libgtkmm-2.4-1c2a
  libtdb1 liblualib50 libqt4-core kdeedu-data python2.4 libglibmm-2.4-1c2a
  libxosd2 libcairomm-1.0-1 libsdl-image1.2 mplayer-skins libgmp3c2
  libopenexr2c2a libmikmod2 python-sip4 tuxkart-data kstars-data debtags
  libdbus-qt-1-1c2 python2.4-minimal ksysguardd libxvmc1 libflac++5c2
  libavahi-compat-libdnssd1 libpulse0 libtar kdelibs-data indi liblua50
  python-wxversion
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater alacarte amule artsbuilder automatix2 bittornado-gui compiz
  compiz-core compiz-gnome compiz-gtk compiz-plugins deskbar-applet
  desktop-effects f-spot freeglut3 gdebi gdm gksu gnome-app-install
  gnome-applets gnome-control-center gnome-netstatus-applet gnome-panel
  gnome-screensaver gnome-session gnome-terminal gparted gstreamer0.10-gl
  hal-device-manager hwdb-client-gnome k3b kalzium katomic kcalc kdebase-bin
  kdelibs4c2a kmid kmix konsole krec kscd ksirtet ksnapshot kstars ksysguard
  kverbos language-selector-qt libgksu1.2-1 libgksu2-0 libgksuui1.0-1
  libgl1-mesa-dri libgl1-mesa-glx libglew1 libglu1-mesa libglut3 libgnomekbd1
  libgnomekbdui1 libgtkglext1 libk3b2 libk3b2-mp3 libkcddb1 libkdeedu3
  libkdegames1 libqt4-gui libwxgtk2.6-0 libwxgtk2.8-0 libxine1
  libxine1-console libxine1-ffmpeg libxine1-gnome libxine1-kde
  libxine1-plugins libxklavier11 mesa-utils mozilla-mplayer mplayer
  mplayer-fonts nautilus nautilus-cd-burner noatun plib1.8.4c2
  python-gnome2-extras python-opengl python-qt4 python-wxgtk2.6 rss-glx
  serpentine software-properties-gtk totem totem-xine tuxkart ubuntu-desktop
  update-manager update-notifier vlc wxvlc xbase-clients xdriinfo xmms xorg
  xorg-driver-fglrx xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i810 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 147 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 401MB disk space will be freed.
Do you want to continue [Y/n]? 


As you can see it wants to remove way too many things...I am afraid I am deleting things the system needs....

---

