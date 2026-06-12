---
title: "Unable to run apt-get update without crashing"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Reynoldsjf on 2007-12-20
HEre's the deal. I've been using for about a month, did the upgrade to 7.1, then I foo'd the stuff up so I just wiped it clean and started. Now I can't do updates. It says run  sudo apt-get update then it will start and then crash. So I've had it working on this box, so I know that's not it. Def very inexperienced and would appreciate some help. Thank you.
                                                                                             ~Joseph




so this is my output 
Setting up capplets-data (1:2.20.1-0ubuntu1) ...

Setting up cupsys-common (1.3.2-1ubuntu7.1) ...
Setting up libebook1.2-9 (1.12.1-0ubuntu1) ...

Setting up python-gmenu (2.20.1-0ubuntu1) ...

Setting up gnome-menus (2.20.1-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up libpng12-0 (1.2.15~beta5-2ubuntu0.1) ...

Setting up libcupsimage2 (1.3.2-1ubuntu7.1) ...

Setting up libcairo2 (1.4.10-1ubuntu4.4) ...

Setting up compiz-plugins (1:0.6.0+git20071008-0ubuntu1.1) ...
Setting up libpango1.0-0 (1.18.3-0ubuntu1) ...

Setting up libgs8 (8.61.dfsg.1~svn8187-0ubuntu3.2) ...

Setting up ghostscript (8.61.dfsg.1~svn8187-0ubuntu3.2) ...
Updating font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Updating category type1..
Updating category type3..
Updating category gsfontderivative..
Updating category truetype..
Updating category cid..
Updating category cmap..
Updating category psprint..
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.

Setting up libwnck22 (2.20.1-0ubuntu1) ...

Setting up libgnomeui-0 (2.20.1.1-0ubuntu1) ...

Setting up libpanel-applet2-0 (1:2.20.1-0ubuntu1) ...

Setting up libgnome-desktop-2 (1:2.20.1-0ubuntu1) ...

Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up perl (5.8.8-7ubuntu3.1) ...

dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libgnome-window-settings1 (1:2.20.1-0ubuntu1) ...

Setting up gnome-control-center (1:2.20.1-0ubuntu1) ...

Setting up compiz-gnome (1:0.6.0+git20071008-0ubuntu1.1) ...

Setting up compiz (1:0.6.0+git20071008-0ubuntu1.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys



how do I do this?

---

### Post by llamakc on 2007-12-20
Are you saying the machine is crashing, or just the output from `sudo apt-get upgrade`?

If you mean the latter, do this:

```

sudo apt-get update && sudo apt-get upgrade

```

When that is done, do this to be sure:

```

sudo apt-get -f install

```

If the problem occurs when running `sudo apt-get update`, run the `sudo apt-get -f install` command first.

---

### Post by SOULRiDER on 2007-12-20
Try with aptitude
```
sudo aptitude update
sudo aptitude dist-upgrade
```

You may need to do a 
```
sudo dpkg --configure -a
``` first and thenr un those commands. try it out and post results.

---

### Post by Reynoldsjf on 2007-12-21
The computer actually freezes up and my caps lock and scroll lock flash. 

to the first command

 sudo apt-get update && sudo apt-get upgrade
[sudo] password for xavier:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [51.6kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [8655B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [29.4kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [4609B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2903B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]
Fetched 149kB in 1s (108kB/s)   
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

to the second command

 sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 0s (4B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

to the third command

sudo dpkg --configure -a
Setting up ubufox (0.4~beta1-0ubuntu6) ...
Setting up libflac8 (1.1.4-3ubuntu1.1) ...

Setting up libnm-util0 (0.6.5-0ubuntu16.7.10.0) ...

Setting up openssl (0.9.8e-5ubuntu3.1) ...

Setting up sound-juicer (2.20.1-0ubuntu1) ...

Setting up pidgin-data (1:2.2.1-1ubuntu4.1) ...

Setting up linux-restricted-modules-common (2.6.22.4-14.10) ...

Setting up hwdb-client-common (0.6.11.1) ...

Setting up libsmbclient (3.0.26a-1ubuntu2.3) ...

Setting up gtk2-engines (1:2.12.2-0ubuntu1) ...
Setting up linux-headers-2.6.22-14 (2.6.22-14.47) ...
Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10) ...

Setting up samba-common (3.0.26a-1ubuntu2.3) ...

Setting up mono-common (1.2.4-6ubuntu6.1) ...

Setting up smbclient (3.0.26a-1ubuntu2.3) ...
Setting up hwdb-client-gnome (0.6.11.1) ...
Setting up libpcre3 (7.4-0ubuntu0.7.10.1) ...

Setting up gnome-games-data (1:2.20.1-0ubuntu1) ...

Setting up gnome-panel-data (1:2.20.1-0ubuntu1) ...

Setting up network-manager (0.6.5-0ubuntu16.7.10.0) ...
 * Reloading system message bus config...                                [ OK ] 
 * Restarting network connection manager NetworkManager                  [ OK ] 
 * Restarting network events dispatcher NetworkManagerDispatcher         [ OK ] 

Setting up gnome-screensaver (2.20.0-0ubuntu4.2) ...

Setting up gnome-system-tools (2.20.0-0ubuntu2) ...

Setting up libpcrecpp0 (7.4-0ubuntu0.7.10.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up libmono0 (1.2.4-6ubuntu6.1) ...

Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...

Setting up linux-headers-2.6.22-14-generic (2.6.22-14.47) ...

Setting up gnome-system-monitor (2.20.1-0ubuntu1) ...

Setting up mono-jit (1.2.4-6ubuntu6.1) ...

Setting up gnome-panel (1:2.20.1-0ubuntu1) ...

Setting up libpurple0 (1:2.2.1-1ubuntu4.1) ...

Setting up gnome-games (1:2.20.1-0ubuntu1) ...

Setting up pidgin (1:2.2.1-1ubuntu4.1) ...

Setting up libmono-corlib2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-corlib1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up mono-gac (1.2.4-6ubuntu6.1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono

Setting up libmono-cairo1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-system1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up mono-runtime (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org-core (1:2.3.0-1ubuntu5.3) ...
Setting up openoffice.org-draw (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-calc (1:2.3.0-1ubuntu5.3) ...

Setting up python-uno (1:2.3.0-1ubuntu5.3) ...

Setting up libmono-system2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org-style-human (1:2.3.0-1ubuntu5.3) ...
Setting up openoffice.org-impress (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-math (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gtk (1:2.3.0-1ubuntu5.3) ...

Setting up libmono-security2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org-common (1:2.3.0-1ubuntu5.3) ...
Updating OpenOffice.org's dictionary list... done.
No theme index file in '/usr/share/icons/locolor'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up libmono-sharpzip2.84-cil (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org-writer (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gnome (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-java-common (1:2.3.0-1ubuntu5.3) ...

Setting up libmono-data-tds2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org-base (1:2.3.0-1ubuntu5.3) ...

Setting up libmono-system-data2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up openoffice.org (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-evolution (1:2.3.0-1ubuntu5.3) ...

Setting up libmono-system-web2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-sqlite2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono2.0-cil (1.2.4-6ubuntu6.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
xavier@xavier:~$


It seems to have worked, but cups still initiates a crash. Why is that. And what exactly did I do, if you don't mind me just asking. Thank you

~Joseph

---

