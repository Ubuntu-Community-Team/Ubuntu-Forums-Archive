---
title: "Skype install problem"
date: 2012-10-16
forum: Any Other OS
---

### Post by vorphs on 2012-10-16
Hello guys,


Just installed Linux Mint 2h ago so im a complete noob :)

I cannot install Skype from the Software Manager so I tried to install it from the Terminal. I  got a few errors, got past them searching on goole, but for this one it seems that i need to post specific info to get help, so here's what i get:

"sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 385 not upgraded.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:amd64
Setting up libssl0.9.8:i386 (0.9.8o-7ubuntu3.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl0.9.8:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.1-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-pc (1.99-21ubuntu3.4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:i386:
 ia32-libs-multiarch:i386 depends on libssl0.9.8; however:
  Package libssl0.9.8:i386 is not configured yet.
dpkg: error processing ia32-libs-multiarch:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not installed.
  Package ia32-libs-multiarch:i386 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.6.3-2ubuntu2.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.6.3-2ubuntu2.3); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.3-2ubuntu2.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of skype:
 skype depends on ia32-libs; however:
  Package ia32-libs is not configured yet.
 skype depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
  Package ia32-libs which provides ia32-libs-gtk is not configured yet.
dpkg: error processing skype (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl0.9.8:i386
 man-db
 grub-pc
 ia32-libs-multiarch:i386
 ia32-libs
 samba-common
 samba
 smbclient
 skype
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Any help would be much appreciated!

---

### Post by cybrsaylr on 2012-10-16
Installing Skype can be buggy.
I had the best luck going to the Skype website and downloading and installing it from there.

---

### Post by vorphs on 2012-10-16
Yeah, that's how I started...got 2-3 errors, worked around them, but now stuck on this one :)

---

### Post by vorphs on 2012-10-17
Nobody? :(

---

### Post by Perfect Storm on 2012-10-17
Moved to Other OS/Distro Talk.

---

