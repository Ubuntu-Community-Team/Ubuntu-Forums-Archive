---
title: "[SOLVED] Edubuntu 6.06 LTS Beta is born !"
date: 2006-04-21
forum: Announcements &amp; News
---

### Post by Oliver Grawert on 2006-04-21
== Edubuntu 6.06 LTS Beta Released ==

The Edubuntu team is happy to announce the release of Edubuntu 6.06 LTS
Beta.
Aside from the usual install CDs for all architectures, this release
includes the Edubuntu live CD that comes with a new live installer to
install the Edubuntu Workstation flavour directly to the disk.
  
Edubuntu is a classroom distribution, shipping with a selection of
educational applications and built around LTSP the linux terminal server
project. Edubuntu aims for an as easy-as-possible installation of an
LTSP setup, but also comes with a workstation flavour for home usage.
The Edubuntu 6.06 LTS (long term support) release comes with 3 Year
support on the desktop and 5 year support on the server.

== Downloading Edubuntu 6.06 LTS Beta ==

To download Edubuntu 6.06 LTS Beta, use one of the following URLs,
please use bittorrent if possible:

 * United States: [http://us.releases.ubuntu.com/edubuntu/6.06/](http://us.releases.ubuntu.com/edubuntu/6.06/)
 * Europe: [http://se.releases.ubuntu.com/edubuntu/6.06/](http://se.releases.ubuntu.com/edubuntu/6.06/)
 * United Kingdom: [http://releases.ubuntu.com/edubuntu/6.06/](http://releases.ubuntu.com/edubuntu/6.06/)
 * Rest of the World: [http://releases.ubuntu.com/edubuntu/6.06/](http://releases.ubuntu.com/edubuntu/6.06/)

The final release of Edubuntu 6.06 LTS Beta will be released on June
1st, at which time you will be able to order pressed install CDs free of
charge.

== Whats New ? ==

 * Edubuntu ships three themes by default in its -artwork package now, 
   with a simple dpkg-reconfigure edubuntu-artwork you are able to 
   select the systemwide default look. The choices are Junior (6-10 age 
   group), Senior (10-16 age group) *default* and Plain (less graphic 
   rich).
 * Themed graphical login manager for the LTSP clients.
 * Support for multiple architectures for the LTSP clients (It is now 
   possible to build the client chroot on AMD64 systems for i386 
   clients by running sudo ltsp-build-client --arch i386 post install). 
 * The first Edubuntu live CD is now available (it contains all of the 
   Edubuntu workstation install and is available for all 3 supported 
   architectures). 
 * Support for the PowerPC architecture was added 
 * LTSP now finally supports the X_COLOR_DEPTH variable to force the 
   usage of 16Bit on the clients through lts.conf. 
 * By default we now install only the linux-image package in the client
   chroot, the excessive memory usage of the restricted modules package 
   is gone 
 * A special netboot mode was introduced to initramfs so only network
   device drivers are loaded, this reduces the size to two thirds of a 
   normal initramfs and speeds up the bootprocess 
 * LTSP now understands the X_MOUSE_DEVICE and X_MOUSE_PROTOCOL 
   in lts.conf options and adds support for various serial devices 
   including touchscreens and serial tablets. 
 * 3 button emulation of 2 button mice is now supported as well. 
 * The bootprocess has seen a lot of speed improvements 
 * Startup links in rcS.d and rc2.d are now started based on whitelists 
   (RC2_WHITELIST RCS_WHITELIST), only the bare minimum of processes is 
   started on the thin clients 
 * this results in a shorter boottime. 
 * Usplash was included and enabled by default on thin clients - Many 
   patches were merged from the debian team to make the packages work 
   on debian as well. 
 * There is optional Sound support on the thin clients now. 
 * The ltsp-build-client script now has options to manually enable 
   extra and security mirrors during chroot creation. 
 * The default mirror of ltsp-build-client points to 
   archive.ubuntu.com  now. 

== Feedback and Helping ==

If you want to help us developing, documenting and improving edubuntu,
have a look at:

 * [https://wiki.edubuntu.org/EdubuntuCommunity](https://wiki.edubuntu.org/EdubuntuCommunity)

== More Information from online ressources ==

For more information see the edubuntu website, wiki and mailing list:

 * [https://www.edubuntu.org](https://www.edubuntu.org)

 * [https://wiki.edubuntu.org](https://wiki.edubuntu.org)

 * [https://lists.ubuntu.com/mailman/listinfo/edubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/edubuntu-devel)


-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

iD8DBQBESPu0SsOT+6LQaTYRAs20AJ9RRSx+Ronul3aJK+NjiaRrKaPePgCdHmK+
ddGBWVclVFpnldSEm7SqyfE=
=m4Wx
-----END PGP SIGNATURE-----

---

