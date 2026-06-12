---
title: "HELP! I ran 'deselect' and now apt-get wants to uninstall 500 packages that I use"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by AustinMarton on 2008-03-22
I am running Fiesty. I was trying to install dillo and all the dependancies that went with it. I ran 'dselect' accidentally and now whenever I run synaptic or 'apt-get -f install' to try and fix up the unfilled dependencies errors it comes up with an enormous list of packages ticked for removal, 1.3gb worth. I know I use lots of them on the list. I just say 'no' don't go ahead, but it comes up again every time I want to install something.

How do I cancel??? Is there a way to deselect all the packages marked for removal?!??!

Please help me I am very worried I am going to accidentally uninstall everything.

---

### Post by angryfirelord on 2008-03-22
Post the output of sudo apt-get -f install.

---

### Post by AustinMarton on 2008-03-22
```
root@austin-laptop:/home/austin# apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  beryl-core libpopt-dev libcommons-collections3-java libopenexr2c2a
  enlightenment-data libsm-dev libchewing3-data libartsc0 libxfce4mcs-client3
  libcommons-pool-java libice-dev libmpfr1 libgoffice-0-common
  ndiswrapper-common x11proto-xext-dev libtasn1-3-dev libaudio-dev
  libgconf2-ruby x11proto-kb-dev liblucene-java libgpg-error-dev
  beryl-settings-bindings libatk1-ruby librplay3 libgstreamer-gconf0.8-0 anthy
  libots0 libcommons-el-java libflac++5c2 x11proto-xinerama-dev junit
  libopencdk8-dev x11proto-render-dev libgcrypt11-dev kdelibs-data
  libregexp-java libtagc0 libcommons-modeler-java abiword-common lmms-common
  libxi-dev gftp-text geda-doc libglib2-ruby libaiksaurus-1.2-0c2a
  libxmu-headers libxrender-dev liblualib50 libpostproc0d gftp-common
  mesa-common-dev libservlet2.4-java gnumeric-common libxdmcp-dev python2.4
  libtomcat5.5-java libwavpack1 libdvbpsi4 libpng12-dev libsnack2 xpdf-utils
  libxosd2 libxfce4util4 xtrans-dev ruby1.8 libbcel-java libchewing3
  libltdl3-dev libberylsettings0 libvlc0 x11proto-core-dev libxcursor-dev
  libglibmm-2.4-1c2a librexml-ruby ant libcommons-launcher-java
  libwpd-stream8c2a ruby geda-symbols libcommons-logging-java tcllib libgmp3c2
  libt1-5 libglu1-mesa-dev libgnutls-dev libaiksaurus-1.2-data
  x11proto-randr-dev xfce4-icon-theme libgdome2-0 libwxbase2.6-0 libxt-dev
  libxmu-dev libxext-dev libwxbase2.8-0 libjpeg62-dev tcltls
  libcommons-dbcp-java libmjpegtools0c2a zlib1g-dev x11proto-input-dev
  libungif4-dev libtiff4-dev x11proto-fixes-dev libcommons-collections-java
  libdvdnav4 libxau-dev libcommons-beanutils-java libiso9660-4 libfluidsynth1
  liblzo-dev tcl8.5 python-wxversion libcdaudio1 libtiffxx0c2 libgl1-mesa-dev
  liblcms1-dev libgdome2-cpp-smart0c2a liblo0 libxrandr-dev libxvmc1
  python-cups libexpat1-dev libcommons-digester-java libanthy0
  libgstreamer-plugins0.8-0 rosegarden-data libraptor1 libstroke0
  libmodplug0c2 libpulse0 libx11-dev liblrdf0 libtar liblucene-java-doc
  libxfce4mcs-manager3 beryl-plugins-data liblua50 libruby1.8 libwraster3
  libjsch-java libxfixes-dev python-eyed3 libquicktime0 libmng-dev ladcca2
  libberyldecoration0 ant-optional libxinerama-dev libvcdinfo0 libcupsys2-dev
  libmpcdec3 libmx4j-java libmms0 xpdf-common libsdl-image1.2
  ndiswrapper-utils-1.9
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword abiword-plugins afterstep alacarte amsn apport-gtk at-spi aterm
  automatix2 avant-window-navigator-bzr awn-core-applets-bzr bbkeys beryl
  beryl-manager beryl-plugins beryl-settings bittornado-gui blackbox
  blackbox-themes blender bluefish bluez-cups bluez-pin brltty-x11 bug-buddy
  catfish compiz compiz-gnome compiz-gtk compiz-plugins conky
  contact-lookup-applet cowbell cupsys cupsys-driver-gutenprint deskbar-applet
  desktop-effects eclipse eclipse-jdt eclipse-pde eclipse-platform eclipse-rcp
  eclipse-source ekiga electric emerald emerald-themes enlightenment eog eterm
  evince evolution evolution-exchange evolution-plugins evolution-webcal
  f-spot fbpanel file-roller filelight firefox firefox-gnome-support
  firestarter fluxbox fontconfig foomatic-db-hpijs fvwm gaim gamix gcalctool
  gconf-editor gdebi gdm geda geda-gnetlist geda-gschem gedit genius gftp
  gftp-gtk giblib1 gimp gimp-print gimp-python gksu gnome-about
  gnome-accessibility-themes gnome-alsamixer gnome-app-install gnome-applets
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media
  gnome-menus gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca
  gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-screensaver gnome-session gnome-spell gnome-splashscreen-manager
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gnumeric-gtk gnusound
  gparted gqview gs-common gs-esp gs-esp-x gsfonts-x11
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-x
  gstreamer0.8-lame gstreamer0.8-misc gthumb gtk-recordmydesktop gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  gtk2-engines-xfce gtkhtml3.14 gtweakui gucharmap gxine hal-cups-utils
  hal-device-manager hpijs hplip human-theme hwdb-client-gnome hydrogen idesk
  idjc imagemagick kdelibs4c2a khelpcenter language-selector
  language-support-en lesstif2 libafterimage0 libafterstep1
  libaiksaurusgtk-1.2-0c2a libarts1c2a libast2 libatspi1.0-0 libavahi-qt3-1
  libawn-bzr libbonoboui2-0 libbt libcairo-perl libcairo-ruby libcairo-ruby1.8
  libcairo2 libcairomm-1.0-1 libedataserverui1.2-8 libeel2-2 libemeraldengine0
  libexchange-storage1.2-3 libexo-0.3-0 libfontconfig1 libfontconfig1-dev
  libfreetype6 libfreetype6-dev libgail-common libgail-gnome-module libgail18
  libgconf2.0-cil libgd2-xpm libgdiplus libgdk-pixbuf2-ruby libgdl-1-0
  libgdl-1-common libgeda20 libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1
  libglade2-0 libglade2-ruby libglade2.0-cil libglib2.0-cil libgmime2.2-cil
  libgnome-desktop-2 libgnome-keyring0 libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomecupsui1.0-1c2a libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgoffice-gtk-0-3 libgpod1 libgs-esp8
  libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.14-19
  libgtkmathview0c2a libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtkspell0
  libgucharmap6 libgutenprintui2-1 libimlib2 libimlib2-dev
  liblaunchpad-integration0 liblpint-bonobo0 libmagick9 libmetacity0
  libmono-cairo1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil
  libnautilus-burn4 libnautilus-extension1 libnotify1 libpanel-applet2-0
  libpango1-ruby libpango1.0-0 libpango1.0-common libpoppler1 libpoppler1-glib
  libqt3-mt libqt3-mt-dev librsvg2-2 librsvg2-common libsexy2 libslab0
  libswfdec0.3 libswt3.2-gtk-java libswt3.2-gtk-jni libthunar-vfs-1-2
  libtotem-plparser1 libvte9 libwmf0.2-7 libwnck18 libwxgtk2.6-0 libwxgtk2.8-0
  libxfcegui4-4 libxfont1 libxft-dev libxft2 libxine-extracodecs libxine1
  libxine1-ffmpeg libxklavier11 lmms metacity mjpegtools mousepad
  mozilla-firefox-locale-en-gb mozilla-thunderbird nautilus nautilus-cd-burner
  nautilus-open-terminal nautilus-sendto ndisgtk network-manager-gnome
  notification-daemon ntfs-config openbox openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer orage pcb pcsx-bin
  pnm2ppa python-at-spi python-cairo python-exo python-glade2 python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gtk2
  python-gtkhtml2 python-launchpad-integration python-notify python-uno
  python-vte python-wxgtk2.6 qemu-launcher qsynth qt3-dev-tools qucs
  restricted-manager rhythmbox rosegarden rss-glx scim scim-anthy scim-chewing
  scim-gtk2-immodule scim-hangul scim-modules-table scim-pinyin
  scim-tables-additional screensaver-default-images scrot serpentine simdock
  software-properties-gtk sound-juicer ssh-askpass-gnome synaptic
  system-config-printer tangerine-icon-theme tango-icon-theme-common thunar
  thunar-archive-plugin thunar-media-tags-plugin thunar-volman-plugin
  thunderbird-locale-en-gb tile tk8.5 tomboy totem totem-mozilla totem-xine
  tsclient ttf-arphic-ukai ttf-arphic-uming ttf-thai-tlwg uae ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntustudio-icon-theme ubuntustudio-theme
  update-manager update-notifier usplash-switcher vino vlc vlc-nox wahcade
  waimea wmaker x-ttcidfont-conf xarchiver xbase-clients xclock xfburn
  xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer
  xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin
  xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin
  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfd xfdesktop4 xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfprint4 xfwm4
  xfwm4-themes xlogo xorg xpdf xpdf-reader xsane xscreensaver
  xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xubuntu-desktop
  xutils yelp zenity zeroinstall-injector
0 upgraded, 0 newly installed, 485 to remove and 112 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1396MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by angryfirelord on 2008-03-22
Did you uninstall the ubuntu-desktop meta-package by mistake? If you did, install it, update it, and run the command again.

---

### Post by AustinMarton on 2008-03-22
Thanks for the quick replies. 

```
root@austin-laptop:/home/austin# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libfreetype6: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
                Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5ubuntu1.1) but 2.3.5-1+b1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I am stuck not being able to install packages! I was trying to install a new version of libfreetype6 and some other libraries that I didn't have new enough versions to install dillo.

---

### Post by moore.bryan on 2008-03-22
it sounds like there's a mismatch of releases; do your sources.list entries match the release you're using?

---

### Post by AustinMarton on 2008-03-23
I am running Fiesty. I just replaced my sources file with the following which I found from a link on the forums. It appears to all be good, but still produces the same output as above. Would a mismatch in sources really matter? I just want to cancel all the packages that have been selected for removal!

/etc/apt/sources.lst
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free 
```

---

### Post by zvacet on 2008-03-23
I have to say it is very strange that you have Feisty sourcce list and you are asked for Gutsy packages.Try to refresh your source list

```
sudo apt-get update && sudo apt-get upgrade
```

If you don´t want to lose your packages just install them again and apt-get will never ask you to remove again.So,

```
sudo apt-get install** packages**
```

** packages=list of packages which are supose to be removed**

---

### Post by AustinMarton on 2008-03-23
Hi zvacet, thanks for your input. I'm thinking it wants the Gutsy packages because when I tried to install dillo it asked for them and thats where my initial troubles started?

I've tried to refresh my sources as you said and it seemed to happily update but still said
```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libfreetype6: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed
                Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is installed
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5ubuntu1.1) but 2.3.5-1+b1 is installed
E: Unmet dependencies. Try using -f.

```
when I tried to upgrade.

I then tried installing the giant list of packages it wanted to remove. It said "* is already the newest version." for all of them and then complained some more about unmet dependencies.

This is horrible! Is there somewhere in Automatix or Synaptic that can show me what packages are lined up to be added/removed and I could untick all the ones its trying to remove? Maybe?

---

### Post by angry_johnnie on 2008-03-23
So, what happens if you run this?


```
sudo apt-get install --reinstall <giant list of packages>
```


But make sure libfreetype6 and libfreetype6-dev are not included in the giant list :-), as they have unmet dependencies.

---

### Post by mc4man on 2008-03-23
If your able to do a search in synaptic then search for libfreetype6 and try to force the version back to2.2.1-5ubuntu1.1

---

### Post by AustinMarton on 2008-03-23
In reply to angry_johnnie:
Okay now I got almost the same thing except this time for some packages it also said```
emerald is already the newest version.
emerald set to manual installed.

```
However when I run ```
apt-get -f install
``` I get the exact same message.

In reply to mc4man:
In Synaptic under 'Broken dependencies' I have 'libfreetype6' version '2.3.5-1+bl' and 'libfreetype6-dev' version '2.2.1-5ubuntu1.1'
The options I have for them are "Mark for Reinstallation", "Mark for Removal" and "Mark for Complete Removal"
Whichever one of these options I choose it comes up with> Mark additional required changes? 
The chosen action also affects other packages. The following changes are required in order to proceed.
**To be removed**
<giant list of packages>
To be installed
gs-gpl
To be upgraded
gimp-data
hpijs
I click cancel out of fear...

---

### Post by mc4man on 2008-03-23
Sorry Austin it was late and i pasted in wrong version> It's been a long time since I had broken dep situation so I forget if synaptic will allow this. (in your current situation). See if you can search to ibfreetype6  and if so highlight it and under packages tab look for force version. If so there may be option to choose version 2.2.1-5ubuntu1.1

---

### Post by moore.bryan on 2008-03-23
one possible solution it to upgrade to gutsy...

---

### Post by AustinMarton on 2008-03-24
mc4man! Thank you, I forced the version back to 2.2.1-5ubuntu1.1 and all the nasty messages have disappeared!! Everything appears to be back to normal and running fine.

I haven't had any big troubles with Fiesty yet (well this is the first freak out), but is there an advantage to upgrading to a newer version? I was trying to follow the if it ain't broke don't fix it moto, but I guess that isn't as fun as if it ain't broke take it apart!

---

### Post by akiratheoni on 2008-03-24
> **AustinMarton said:**
> mc4man! Thank you, I forced the version back to 2.2.1-5ubuntu1.1 and all the nasty messages have disappeared!! Everything appears to be back to normal and running fine.

I haven't had any big troubles with Fiesty yet (well this is the first freak out), but is there an advantage to upgrading to a newer version? I was trying to follow the if it ain't broke don't fix it moto, but I guess that isn't as fun as if it ain't broke take it apart!

Well, newer releases tend to have better hardware support and easier-to-use tools. I found Gutsy a lot easier to detect my monitor resolution however Feisty was still really good for me. Your choice to upgrade or not. Hardy is coming out next month, though, so you might want to hold off on the upgrade and just install Hardy instead of Gutsy.

---

### Post by mc4man on 2008-03-24
@ austin good to hear - couldn't believe I made that mistake. As far as upgrading I like gutsy and hardy better - though if you have a laptop you should first try the live cd . One problem with the cd is you can't test (afaik) how restricted drivers are going to work so a little searching/reading is worth the effort. Desktops generally work one way or the other.

---

