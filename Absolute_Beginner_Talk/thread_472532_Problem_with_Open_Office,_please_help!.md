---
title: "Problem with Open Office, please help!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by czhou on 2007-06-13
I just installed Ubuntu 6.10 Edgy, and I've been having problems with Open Office. Whenever I try to open any of the Open Office Applications (Word, Spreadsheet, Database, etc), it loads up a little and then just disappears (nothing opens).

I tried to reinstall the applications under Synaptic Package Manager, but that didn't do anything. 

I tried to remove Open Office Suite completely, but it said that such an action would also remove Ubuntu Desktop System (which I don't think I would want to do). Is there a way to fix this, without reinstalling the entire system?

Thanks in advance.

---

### Post by hyper_ch on 2007-06-13
Well, you could try this.

(1) Open a terminal
(2) Run this command:

```

sudo aptitude update && sudo aptitude install openoffice.org openoffice.org-gtk

```

Please post the output here :)

---

### Post by scribles on 2007-06-13
ubuntu-desktop is just a virtual package (it tells the install to install other packages) so uninstalling it won't hurt anything.

Before you go uninstalling anything try running Open Office from the command line. Open a terminal and type 'oowriter'. You should see some error messages that might point you in the right direction.

---

### Post by czhou on 2007-06-13
[SIZE="6"]Thanks guys. Here's the update output:[/SIZE]

zhou@zhou-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_AU
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_AU
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_AU                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_AU           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_AU             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/multiverse Translation-en_AU
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Packages                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/multiverse Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Sources           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Sources     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Sources       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/multiverse Sources     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Sources   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/multiverse Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Fetched 3B in 22s (0B/s) 
Reading package lists... Done

zhou@zhou-desktop:~$ sudo aptitude install openoffice.org openoffice.org-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus 
  dbus-1-utils dnsutils ekiga evince evolution evolution-data-server 
  evolution-data-server-common evolution-plugins file firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-applets 
  gnome-applets-data gnome-control-center gnome-games gnome-games-data 
  gnome-netstatus-applet gnome-panel gnome-panel-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libaudio2 
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libbind9-0 libc6 libc6-i686 libcamel1.2-8 libcurl3 
  libdbus-1-3 libdns21 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8 
  libegroupwise1.2-12 libexchange-storage1.2-2 libexif12 libfreetype6 
  libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common 
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmagic1 libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnautilus-extension1 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 
  libpoppler1-glib libsmbclient libsoup2.2-8 libtotem-plparser1 
  libvolumeid0 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-data poppler-utils popularity-contest rdesktop samba-common 
  screen slocate smbclient synaptic system-tools-backends tar tcpdump totem 
  totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs udev 
  update-manager update-notifier vim-common vim-tiny vino volumeid w3m 
  x11-common xbase-clients xorg xscreensaver-data xscreensaver-gl 
  xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-video-all xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 153 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
[SIZE="6"]
and here's the error message after running writer from command line:[/SIZE]

zhou@zhou-desktop:~$ oowriter

** (process:7999): WARNING **: Unknown error forking main binary / abnormal early exit ...


I also searched on other forums, and from the chinese forum, it seems that open office clashes with the scim input method. One solution was to delete the last 2 lines from * /etc/gtk-2.0/gtk.immodules*:

"/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so"
"scim" "SCIM Input Method" "scim" "/usr/share/locale" ""

I tried that, and open office worked, but scim input method stopped working in open office....

Should I uninstall open office and reinstall, hoping the clash would somehow vanish, or should I get rid of scim input method and find another input method?

Thanks for your help!

---

### Post by scribles on 2007-06-13
I don't know anything about scim so I can't help you with that, but I would make sure everything is up to date first. Run the Update Manager or from the command line ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by czhou on 2007-06-13
Thanks scribles, I've updated everything.

I found the solution to the problem in the Chinese forum. It is a clash between open office and the scim input method. The solution was to use scim-bridge.

sudo apt-get install scim-qtimm scim-bridge scim-bridge-agent scim-bridge-client-gtk scim-bridge-client-qt

(scim-bridge-agent scim-bridge-client-gtk scim-bridge-client-qt might not work, but that didn't matter)

sudo im-switch -s scim
sudo gedit /etc/X11/xinit/xinput.d/scim

change **GTK_IM_MODULE=scim** to **GTK_IM_MODULE="scim-bridge"**

---

