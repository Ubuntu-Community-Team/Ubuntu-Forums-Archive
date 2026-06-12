---
title: "problem removing packages_software index broken"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by sunflower on 2007-06-11
Hi!
Need some help.. Am new to all this and I don't know what to do...

So I get an icon on the top right side of the screen saying updates are available, I click on it and get the following message

[COLOR="Red"]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
[/COLOR]

So I use a terminal and get the following

marie@Sunflower:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 46 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? Y
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
marie@Sunflower:~$ 



Then in one post I saw someone suggesting the Add/Remove so I clicked and here's what I got...

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


When I use the Synaptic package manager I get the following

An error occured

The following details are provided:
E: libdiscover1: subprocess post-removal script returned error exit status 139


Don't know what to do.. :cry: help help...:(

---

### Post by mejy on 2007-06-11
What package were you installing/removing when this happened?  Try running 'sudo apt-get update && sudo apt-get upgrade'.

---

### Post by sunflower on 2007-06-11
OK... here's what I get. 
I didn't have any specifinc package in mind I just wanted to update that's it and i got the index broken message and now when I do what you asked me to do I get this... 

marie@Sunflower:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data-commercial apport apport-gtk capplets-data firefox
  firefox-gnome-support gimp gimp-data gimp-python gnome-control-center
  gnome-panel gnome-panel-data hwdb-client-common hwdb-client-gnome
  libfreetype6 libgimp2.0 libgnome-window-settings1 libmetacity0 libnspr4
  libnss3 libpanel-applet2-0 libslab0 libsmbclient linux-generic
  linux-restricted-modules-common metacity metacity-common python
  python-apport python-gdbm python-minimal python-problem-report python2.5
  python2.5-minimal rdesktop samba-common smbclient tzdata unattended-upgrades
  update-manager update-manager-core vim-common vim-tiny
43 upgraded, 0 newly installed, 9 to remove and 3 not upgraded.
9 not fully installed or removed.
Need to get 0B/35.9MB of archives.
After unpacking 9110kB disk space will be freed.
Do you want to continue [Y/n]? Y
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
marie@Sunflower:~$

---

