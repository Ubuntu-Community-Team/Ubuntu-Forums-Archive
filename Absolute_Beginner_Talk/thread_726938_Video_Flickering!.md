---
title: "Video Flickering!"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-17
Hey guys , anyone fixed video flickering while running compiz(my card is ATI x1400) ?
Seems like some of the screensavers that came with gutsy are now flickering aswell.
I tried the advice of a similar post that recommended edit the xorg.conf file but I nothing displayed for that file , could be cos I used Envy to get my card on the road? Any help , as always , is much appreciated!

---

### Post by Ub1476 on 2008-03-17
The ATI driver is still no good, but improvements are coming every months. Only way to avoid video flickering is to turn off Compiz (this is not Compiz fault, but the ATI drivers which can't handle both). f you are using the latest 8.3 Catalyst/fglrx driver, you can at least play movies in VLC by setting the  output module to X11.

---

### Post by jan quark on 2008-03-17
to edit the xorg.conf file run

```
gksudo gedit  /etc/X11/xorg.conf
```

---

### Post by billgoldberg on 2008-03-17
I don't know if this will work for you ati card but the only ati driver that works well for me is the one in "restricted drivers". If I use envy the fullscreen video lags and flickers.

---

### Post by Helios1276 on 2008-03-17
I use Envy i get compiz and video flickering, I use the Restricted driver I get no compiz and non flickering video. This annoys me lol

---

### Post by Helios1276 on 2008-03-17
ok, going to give VLC a shot, tried this and now im stuck, what next?

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IE
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IE           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IE     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IE       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IE     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Get:2 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release.gpg [189B]              
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Translation-en_IE            
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release                           
Err [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release
  
Get:3 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Translation-en_IE
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Get:5 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release [3469B]
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release     
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy Release                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main Sources            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/restricted Sources      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Packages       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe Sources        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Packages     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/multiverse Sources      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/main Packages   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/main Sources    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Packages     
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Sources
Fetched 3661B in 3s (1216B/s)
Reading package lists... Done
W: GPG error: [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
shane@Acer:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fftw3 libxcb-xv0 mysql-common libmysqlclient15off ruby1.8 libxcb1 python-qt3 ruby libkonq4
  python-sip4 kdebase-bin libxcb-shape0 libtunepimp5 libifp4 libdbus-qt-1-1c2 kdesktop libxvmc1
  libpq5 libpulse0 libruby1.8 libxcb-shm0 libnjb5 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec1d libavformat1d libavutil1d libdc1394-13 libdvbpsi4 libdvdnav4 libebml0 libgsm1
  libiso9660-4 libmatroska0 libpostproc1d libsdl-image1.2 libtar libvcdinfo0 libvlc0
  libwxbase2.6-0 libwxgtk2.6-0 libxosd2 ttf-dejavu ttf-dejavu-extra vlc-nox
Suggested packages:
  xfonts-base-transcoded
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libavcodec1d libavformat1d libavutil1d libdc1394-13 libdvbpsi4 libdvdnav4 libebml0 libgsm1
  libiso9660-4 libmatroska0 libpostproc1d libsdl-image1.2 libtar libvcdinfo0 libvlc0
  libwxbase2.6-0 libwxgtk2.6-0 libxosd2 mozilla-plugin-vlc ttf-dejavu ttf-dejavu-extra vlc
  vlc-nox vlc-plugin-esd
0 upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.9MB/15.6MB of archives.
After unpacking 41.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe libvlc0 0.8.6.release.c-0ubuntu5.1 [873kB]
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main libdc1394-13 1.1.0-3ubuntu3 [34.4kB]
Get:3 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main libavformat1d 3:0.cvs20070307-5ubuntu4 [287kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe vlc-nox 0.8.6.release.c-0ubuntu5.1 [4671kB]
Get:5 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libdvbpsi4 0.1.5-3 [32.2kB]                    
Get:6 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libdvdnav4 0.1.10-0.2 [92.3kB]                 
Get:7 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libebml0 0.7.7-3 [62.5kB]                      
Get:8 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/universe libiso9660-4 0.76-1ubuntu2.7.10.1 [97.0kB]
Get:9 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libmatroska0 0.8.1-1 [190kB]                   
Get:10 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main libpostproc1d 3:0.cvs20070307-5ubuntu4 [71.5kB]   
Get:11 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main libsdl-image1.2 1.2.5-3 [29.4kB]                  
Get:12 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libtar 1.2.11-4 [19.0kB]                      
Get:13 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libvcdinfo0 0.7.23-3 [124kB]                  
Get:14 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libwxbase2.6-0 2.6.3.2.1.5ubuntu12 [570kB]    
Get:15 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libwxgtk2.6-0 2.6.3.2.1.5ubuntu12 [2886kB]    
Get:16 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/universe libxosd2 2.2.14-1.3 [24.5kB]                  
Get:17 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main ttf-dejavu-extra 2.19-1ubuntu3 [2652kB]           
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe vlc 0.8.6.release.c-0ubuntu5.1 [1162kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe mozilla-plugin-vlc 0.8.6.release.c-0ubuntu5.1 [38.0kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe vlc-plugin-esd 0.8.6.release.c-0ubuntu5.1 [4872B]
Get:21 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy/main ttf-dejavu 2.19-1ubuntu3 [22.7kB]                 
Fetched 13.9MB in 1m54s (122kB/s)                                                                
Selecting previously deselected package libavutil1d.
(Reading database ... 104468 files and directories currently installed.)
Unpacking libavutil1d (from .../libavutil1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libgsm1.
Unpacking libgsm1 (from .../libgsm1_1.0.10-13build1_i386.deb) ...
Selecting previously deselected package libavcodec1d.
Unpacking libavcodec1d (from .../libavcodec1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libdc1394-13.
Unpacking libdc1394-13 (from .../libdc1394-13_1.1.0-3ubuntu3_i386.deb) ...
Selecting previously deselected package libavformat1d.
Unpacking libavformat1d (from .../libavformat1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libdvbpsi4.
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-3_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from .../libdvdnav4_0.1.10-0.2_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3_i386.deb) ...
Selecting previously deselected package libiso9660-4.
Unpacking libiso9660-4 (from .../libiso9660-4_0.76-1ubuntu2.7.10.1_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1_i386.deb) ...
Selecting previously deselected package libpostproc1d.
Unpacking libpostproc1d (from .../libpostproc1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.5-3_i386.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-4_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-3_i386.deb) ...
Selecting previously deselected package libvlc0.
Unpacking libvlc0 (from .../libvlc0_0.8.6.release.c-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libwxbase2.6-0.
Unpacking libwxbase2.6-0 (from .../libwxbase2.6-0_2.6.3.2.1.5ubuntu12_i386.deb) ...
Selecting previously deselected package libwxgtk2.6-0.
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.3.2.1.5ubuntu12_i386.deb) ...
Selecting previously deselected package libxosd2.
Unpacking libxosd2 (from .../libxosd2_2.2.14-1.3_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.8.6.release.c-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package ttf-dejavu-extra.
Unpacking ttf-dejavu-extra (from .../ttf-dejavu-extra_2.19-1ubuntu3_all.deb) ...
Selecting previously deselected package ttf-dejavu.
Unpacking ttf-dejavu (from .../ttf-dejavu_2.19-1ubuntu3_all.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.8.6.release.c-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package mozilla-plugin-vlc.
Unpacking mozilla-plugin-vlc (from .../mozilla-plugin-vlc_0.8.6.release.c-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package vlc-plugin-esd.
Unpacking vlc-plugin-esd (from .../vlc-plugin-esd_0.8.6.release.c-0ubuntu5.1_i386.deb) ...
Setting up libavutil1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libgsm1 (1.0.10-13build1) ...

Setting up libavcodec1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libdc1394-13 (1.1.0-3ubuntu3) ...

Setting up libavformat1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libdvbpsi4 (0.1.5-3) ...

Setting up libdvdnav4 (0.1.10-0.2) ...

Setting up libebml0 (0.7.7-3) ...

Setting up libiso9660-4 (0.76-1ubuntu2.7.10.1) ...

Setting up libmatroska0 (0.8.1-1) ...

Setting up libpostproc1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libsdl-image1.2 (1.2.5-3) ...

Setting up libtar (1.2.11-4) ...

Setting up libvcdinfo0 (0.7.23-3) ...

Setting up libvlc0 (0.8.6.release.c-0ubuntu5.1) ...

Setting up libwxbase2.6-0 (2.6.3.2.1.5ubuntu12) ...

Setting up libwxgtk2.6-0 (2.6.3.2.1.5ubuntu12) ...

Setting up libxosd2 (2.2.14-1.3) ...

Setting up vlc-nox (0.8.6.release.c-0ubuntu5.1) ...
Setting up ttf-dejavu-extra (2.19-1ubuntu3) ...
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.

Setting up ttf-dejavu (2.19-1ubuntu3) ...
Setting up vlc (0.8.6.release.c-0ubuntu5.1) ...

Setting up mozilla-plugin-vlc (0.8.6.release.c-0ubuntu5.1) ...
Setting up vlc-plugin-esd (0.8.6.release.c-0ubuntu5.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
shane@Acer:~$

---

### Post by Ub1476 on 2008-03-17
Wow.. I suggest you type this command:

```
sudo apt-get autoremove
```

To set X11 as output module in VLC, go to Settings>Preferences>Video>Output modules>Advanced options>Select X11 in the dropdownmenu in "Output modules".

This doesn't affect the system. It only does so you can watch movies in VLC without turning off Compiz. Screensavers etc, still wont work with Compiz (not without some tweaking as I know as at least..).

---

### Post by Helios1276 on 2008-03-17
wow? lol whats wrong?

---

### Post by Ub1476 on 2008-03-17
All these packages:

```
fftw3 libxcb-xv0 mysql-common libmysqlclient15off ruby1.8 libxcb1 python-qt3 ruby libkonq4
python-sip4 kdebase-bin libxcb-shape0 libtunepimp5 libifp4 libdbus-qt-1-1c2 kdesktop libxvmc1
libpq5 libpulse0 libruby1.8 libxcb-shm0 libnjb5 libofa0 libxine1
```

Are installed but not required anymore.

```
sudo apt-get autoremove
```

To remove them.

---

### Post by forrestcupp on 2008-03-17
If you use vlc for your videos, you can go to Settings->Preferences.  Then click the down arrow next to 'Video' and click on 'Output Options.'  In the lower right corner, check the 'Advanced Options' box, and set the 'Video Output Module' drop down box to 'X11 video output.'  Then save your settings.

That will get rid of the video flickering while Compiz is on.  Unfortunately, there is nothing you can do about opengl screensavers and games.  If you want to play an opengl game, you just have to turn Compiz off.

---

### Post by Helios1276 on 2008-03-17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fftw3 libxcb-xv0 mysql-common libmysqlclient15off ruby1.8 libxcb1 python-qt3
  ruby libkonq4 python-sip4 kdebase-bin libxcb-shape0 libtunepimp5 libifp4
  libdbus-qt-1-1c2 kdesktop libxvmc1 libpq5 libpulse0 libruby1.8 libxcb-shm0
  libnjb5 libofa0 libxine1
The following packages will be REMOVED:
  fftw3 kdebase-bin kdesktop libdbus-qt-1-1c2 libifp4 libkonq4
  libmysqlclient15off libnjb5 libofa0 libpq5 libpulse0 libruby1.8 libtunepimp5
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common
  python-qt3 python-sip4 ruby ruby1.8
0 upgraded, 0 newly installed, 24 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 50.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105155 files and directories currently installed.)
Removing libtunepimp5 ...
Removing libofa0 ...
Removing fftw3 ...
Removing kdesktop ...
Removing kdebase-bin ...
Removing libdbus-qt-1-1c2 ...
Removing libifp4 ...
Removing libkonq4 ...
Removing libmysqlclient15off ...
Removing libnjb5 ...
Removing libpq5 ...
Removing ruby ...
Removing ruby1.8 ...
Removing libruby1.8 ...
Removing mysql-common ...
Removing python-qt3 ...
Removing python-sip4 ...
Removing libxine1 ...
Removing libpulse0 ...
Removing libxcb-shape0 ...
Removing libxcb-shm0 ...
Removing libxcb-xv0 ...
Removing libxcb1 ...
Removing libxvmc1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
shane@Acer:~$ 

Am I good?

---

### Post by Helios1276 on 2008-03-17
ok, im setting up x11 in vlc, gotten to the x11 menu, how do i enable it properly? so far i'm still getting the flickering

---

### Post by forrestcupp on 2008-03-17
You don't need to be in the X11 menu.  You need to highlight the 'Output modules' menu, then click the 'Advanced options' box and set the video output module to X11.  Then save it, close VLC and try it again.

---

