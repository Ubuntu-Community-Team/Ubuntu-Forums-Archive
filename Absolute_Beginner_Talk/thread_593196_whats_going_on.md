---
title: "whats going on?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-26
OK whats up with this? i was running some updates and something with them failed (im using kubuntu feisty) and then i tried to install compiz fusion from this tutorial: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) but i keep getting errors.... heres what it all looks like

```

carl@Islandmassive:~$ sudo apt-get -y remove compiz-core desktop-effects
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
carl@Islandmassive:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
carl@Islandmassive:~$ sudo dpkg --configure -a
Setting up libpq5 (8.2.5-0ubuntu0.7.04.1) ...

Setting up libdbus-1-3 (1.0.2-1ubuntu4) ...

Setting up libexif12 (0.6.13-5ubuntu0.2) ...

Setting up libcurl3-gnutls (7.15.5-1ubuntu2.1) ...

Setting up kdebase-data (3.5.6-0ubuntu20.7) ...

Setting up hpijs (2.7.2+1.7.3-0ubuntu1.1) ...
Setting up vim-common (7.0-164+1ubuntu7.2) ...

Setting up openssl (0.9.8c-4ubuntu0.2) ...

Setting up koffice-data (1.6.2-0ubuntu1.1) ...

Setting up libmagic1 (4.19-1ubuntu2.1) ...

Setting up ksysguardd (3.5.6-0ubuntu20.7) ...
Setting up libmagick9 (6.2.4.5.dfsg1-0.14ubuntu0.2) ...

Setting up dbus (1.0.2-1ubuntu4) ...
 * Reloading system message bus config...                                [ OK ]

Setting up linux-restricted-modules-common (2.6.20.5-16.29) ...

Setting up file (4.19-1ubuntu2.1) ...
Setting up libisc11 (9.3.4-2ubuntu2.1) ...

Setting up hwdb-client-common (0.6.10.1) ...

Setting up update-manager-core (0.59.25) ...

Setting up app-install-data (0.3.31) ...
Setting up libsmbclient (3.0.24-2ubuntu1.2) ...

Setting up liblwres9 (9.3.4-2ubuntu2.1) ...

Setting up mysql-common (5.0.38-0ubuntu1.1) ...
Setting up rsync (2.6.9-3ubuntu1.1) ...

Setting up hwdb-client-kde (0.6.10.1) ...
Setting up linux-headers-2.6.20-16 (2.6.20-16.32) ...

Setting up tcpdump (3.9.5-2ubuntu1) ...
Setting up libpulse0 (0.9.5-5ubuntu4.1) ...

Setting up samba-common (3.0.24-2ubuntu1.2) ...

Setting up libgl1-mesa-glx (6.5.2-3ubuntu8) ...

Setting up linux-headers-2.6.20-16-generic (2.6.20-16.32) ...
Setting up unattended-upgrades (0.23ubuntu3) ...
Setting up smbclient (3.0.24-2ubuntu1.2) ...
Setting up python-problem-report (0.76.1) ...

Setting up libpoppler1 (0.5.4-0ubuntu8.1) ...

Setting up util-linux-locales (2.12r-17ubuntu2.1) ...

Setting up poppler-utils (0.5.4-0ubuntu8.1) ...
Setting up kdelibs-data (3.5.6-0ubuntu14.1) ...

Setting up linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up python-launchpad-bugs (0.1.13.2) ...

Setting up libvorbis0a (1.1.2.dfsg-1.2ubuntu2) ...

Setting up linux-headers-generic (2.6.20.16.28.1) ...
Setting up iptables (1.3.6.0debian1-5ubuntu2.1) ...

Setting up vim-tiny (7.0-164+1ubuntu7.2) ...

Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libwrap0 (7.6.dbs-11ubuntu0.1) ...

Setting up libisccc0 (9.3.4-2ubuntu2.1) ...

Setting up libgl1-mesa-dri (6.5.2-3ubuntu8) ...
Setting up kdelibs4c2a (3.5.6-0ubuntu14.1) ...

Setting up libvorbisfile3 (1.1.2.dfsg-1.2ubuntu2) ...

Setting up konsole (3.5.6-0ubuntu20.7) ...

Setting up libdns22 (9.3.4-2ubuntu2.1) ...

Setting up mesa-utils (6.5.2-3ubuntu8) ...
Setting up adept-common (2.1.2ubuntu26.1) ...

Setting up kdebase-bin (3.5.6-0ubuntu20.7) ...

Setting up libmysqlclient15off (5.0.38-0ubuntu1.1) ...

Setting up libkonq4 (3.5.6-0ubuntu20.7) ...

Setting up python-apport (0.76.1) ...

Setting up kate (3.5.6-0ubuntu20.7) ...

Setting up adept-updater (2.1.2ubuntu26.1) ...

Setting up libglu1-mesa (6.5.2-3ubuntu8) ...

Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.29) ...

Setting up kmenuedit (3.5.6-0ubuntu20.7) ...

Setting up libvorbisenc2 (1.1.2.dfsg-1.2ubuntu2) ...

Setting up libpoppler1-qt (0.5.4-0ubuntu8.1) ...

dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
Setting up kdeprint (3.5.6-0ubuntu20.7) ...

Setting up libisccfg1 (9.3.4-2ubuntu2.1) ...

Setting up linux-image-generic (2.6.20.16.28.1) ...
Setting up ksplash (3.5.6-0ubuntu20.7) ...

Setting up kfind (3.5.6-0ubuntu20.7) ...

Setting up kdesktop (3.5.6-0ubuntu20.7) ...

Setting up ktorrent (2.1-0ubuntu2.1) ...

Setting up khelpcenter (3.5.6-0ubuntu20.7) ...

Setting up ksysguard (3.5.6-0ubuntu20.7) ...

Setting up linux-restricted-modules-generic (2.6.20.16.28.1) ...
Setting up adept-installer (2.1.2ubuntu26.1) ...

Setting up kwin (3.5.6-0ubuntu20.7) ...

Setting up adept-manager (2.1.2ubuntu26.1) ...

dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
Setting up kdebase-kio-plugins (3.5.6-0ubuntu20.7) ...

Setting up kdm (3.5.6-0ubuntu20.7) ...

Setting up koffice-libs (1.6.2-0ubuntu1.1) ...

Setting up konqueror-nsplugins (3.5.6-0ubuntu20.7) ...

Setting up linux-generic (2.6.20.16.28.1) ...
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
Setting up libjasper-runtime (1.701.0-2ubuntu0.7.04) ...
Setting up kicker (3.5.6-0ubuntu20.7) ...

dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Setting up klipper (3.5.6-0ubuntu20.7) ...

Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ]

Setting up adept-batch (2.1.2ubuntu26.1) ...
Setting up kdepasswd (3.5.6-0ubuntu20.7) ...

Setting up kexi (1.6.2-0ubuntu1.1) ...

Setting up adept-notifier (2.1.2ubuntu26.1) ...
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
Setting up libbind9-0 (9.3.4-2ubuntu2.1) ...

dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
Setting up apport-qt (0.76.1) ...
Setting up adept (2.1.2ubuntu26.1) ...
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Setting up ksmserver (3.5.6-0ubuntu20.7) ...

dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Setting up bind9-host (9.3.4-2ubuntu2.1) ...
Setting up kcontrol (3.5.6-0ubuntu20.7) ...

Setting up konqueror (3.5.6-0ubuntu20.7) ...

Setting up dnsutils (9.3.4-2ubuntu2.1) ...

Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-calc
 openoffice.org-kde
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org-style-human
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-style-crystal
carl@Islandmassive:~$ sudo apt-get -y remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package compiz-core is not installed, so not removed
Package desktop-effects is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 openoffice.org-math
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-human
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

thanx for any help:guitar:

---

### Post by MegaJim on 2007-10-26
what happens if you now run

```
sudo apt-get check
```

---

### Post by kamitsukai on 2007-10-26
```
carl@Islandmassive:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
carl@Islandmassive:~$

```

---

### Post by kerry_s on 2007-10-26
[B]sudo apt-get clean
sudo apt-get -f install[/B]

---

### Post by kamitsukai on 2007-10-26
Kerry_s=

```

carl@Islandmassive:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 openoffice.org-math
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-human
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code (1)
carl@Islandmassive:~$           
```

---

### Post by kamitsukai on 2007-10-26
well lol i dont mean to be rude (as i only just posted this :P) but its 4:30 in the morning in the uk and i could do with some sleep so if you know whats wrong i would be greatful if anyone can help

---

### Post by MegaJim on 2007-10-26
:) you're welcome

work through this

[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)

---

### Post by kerry_s on 2007-10-27
try to get rid of that cache error->
**sudo fc-cache -f -v**

---

### Post by kamitsukai on 2007-10-27
Thanx! ill try both of those and ill post how i get on :P

---

### Post by kamitsukai on 2007-10-27
thnx works like a charm (^0^)

---

