---
title: "Problems trying to update system after fresh install"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by LiquidOC on 2007-09-19
When I first logon, my system tells me there are packages that have updates available, so I click on the orange icon where the message originated from, and I get this message:

> Software Index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I ran the sudo command, and it outputs this:

> liquidoc@Office-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 115 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libcairomm-1.0-1 ...
Segmentation fault (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebconfclient0 ...
Segmentation fault (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebian-installer4 ...
Segmentation fault (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdiscover1 ...
Segmentation fault (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libfuse2 ...
Segmentation fault (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libglibmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libntfs9 ...
Segmentation fault (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 139
Removing xfsprogs ...
Segmentation fault (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to run Synaptic package manager, and I get this error:

> 
E: libdiscover1: subprocess post-removal script returned error exit status 139

So I'm at a loss now. I also can't figure out how to disable the onboard sound and get my Soundblaster Audigy to work, and to get all the resolutions supported by my video card (Intel i740 AGP) to show up, but those problems can wait until I can actually update my system. Any help at all is appreciated. Thanks!!!!!!!!

Edit: I fixed my problems with resolutions and my sound by searching these forums, which is just awesome, but I still need this little problem fixed. Thanks!!!!!

---

### Post by alienexplorers on 2007-09-19
What happens if you run:
> sudo apt-get update
and
> sudo apt-get upgrade
then run
> sudo apt-get install -f

---

### Post by LiquidOC on 2007-09-20
OK, Ran the commands.

> liquidoc@Office-desktop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [77.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [13.8kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [35.6kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [4876B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6101B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [1052B]
Fetched 198kB in 1s (123kB/s)                        
Reading package lists... Done


next.....

> liquidoc@Office-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host
  capplets-data dbus dbus-1-utils dnsutils evolution-data-server
  evolution-data-server-common file firefox firefox-gnome-support gimp
  gimp-data gimp-python gnome-app-install gnome-control-center gnome-panel
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables
  language-pack-en language-pack-gnome-en libbind9-0 libcamel1.2-10 libcurl3
  libdbus-1-3 libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libexif12 libfreetype6
  libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libgnome-window-settings1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1
  libkrb53 liblwres9 libmagic1 libmagick9 libmetacity0 libnspr4 libnss3
  libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libslab0
  libsmbclient libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 linux-generic
  linux-restricted-modules-common mesa-utils metacity metacity-common
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-style-human openoffice.org-writer poppler-utils python
  python-apport python-gdbm python-launchpad-bugs python-minimal
  python-problem-report python-uno python2.5 python2.5-minimal rdesktop rsync
  samba-common smbclient tar tcpdump ttf-opensymbol tzdata unattended-upgrades
  update-manager update-manager-core vim-common vim-tiny xscreensaver-data
  xscreensaver-gl
112 upgraded, 0 newly installed, 9 to remove and 3 not upgraded.
9 not fully installed or removed.
Need to get 0B/140MB of archives.
After unpacking 5280kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libcairomm-1.0-1 ...
Segmentation fault (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebconfclient0 ...
Segmentation fault (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebian-installer4 ...
Segmentation fault (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdiscover1 ...
Segmentation fault (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libfuse2 ...
Segmentation fault (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libglibmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libntfs9 ...
Segmentation fault (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 139
Removing xfsprogs ...
Segmentation fault (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)


next.....

> liquidoc@Office-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 115 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libcairomm-1.0-1 ...
Segmentation fault (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebconfclient0 ...
Segmentation fault (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdebian-installer4 ...
Segmentation fault (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libdiscover1 ...
Segmentation fault (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libfuse2 ...
Segmentation fault (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 139
Removing libglibmm-2.4-1c2a ...
Segmentation fault (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 139
Removing libntfs9 ...
Segmentation fault (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 139
Removing xfsprogs ...
Segmentation fault (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)


So I'm still getting the same errors. At least it runs smoother than xp ;)

---

### Post by LiquidOC on 2007-09-20
I tried a few commands that were given to me in a PM, and they didn't work either. Here's what they output:

> liquidoc@Office-desktop:~$ sudo aptitude update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (3B/s)  
Reading package lists... Done


and....

> 
liquidoc@Office-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have unmet dependencies:
  libdiscover1: Depends: discover1-data (>= 1.2004.09.24) but it is not installable


Thanks!!

---

### Post by wpshooter on 2007-09-20
What version of Ubuntu are you running ?  Is it Feisty ?

Have you gone into software sources and made sure the proper sources are marked ?

Then go into Synaptic and try doing a refresh / or reload and then reboot and then try to install the updates after you get back up to the desktop.

---

### Post by LiquidOC on 2007-09-20
I am running 7.04.....whichever that is. How do I go into software sources and check them? I know this all might sound dumb, but I don't know anything really about linux, or ubuntu for that manner. Thanks!!

---

### Post by LiquidOC on 2007-09-27
I also feel it might be important to tell you all that I cannot install anything on my system either, but don't know if that helps you.

Thanks,

LiquidOC

---

### Post by gnudoc on 2007-09-27
could you please do the following in a terminal:

```
cat /etc/apt/sources.list
```

This is the command-line way of checking your sources - the GUI way is System -> Administration -> Software Sources, but the result isn't as easy to paste into a forum :)

Thanks
gnudoc

---

