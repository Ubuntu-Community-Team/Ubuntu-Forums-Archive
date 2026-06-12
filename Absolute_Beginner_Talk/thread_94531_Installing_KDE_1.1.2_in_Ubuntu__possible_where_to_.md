---
title: "Installing KDE 1.1.2 in Ubuntu ? possible? where to find installation files ?"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-24
it's for my old pc ...

---

### Post by suRoot on 2005-11-24
The oldest release in the KDE "Attic" is 2.2.2:

[ftp://ftp.kde.org/pub/kde/Attic]("ftp://ftp.kde.org/pub/kde/Attic")

---

### Post by patrick295767 on 2005-11-24
Thank you very very very much !!!!!!!!
U are my only hope for my old pc 
  
I tried allllllllll the net to find kde installtion files 1.2 and 1.1.2 
but nothing !!
  
I hope 2.2 Kde attix will be working ... I am gonna download that 
  
---
Also, I have my cd's of corel linux at home. Would you think that I can get the required files of KDE 1.1.2 from the cd, then use them for installing 
the KDE 1.1.2 on my old pc, (with UBUNTU installed as server on it )
I guess I could do it no ? 
(alien -i  and dpkg -i       will be my allies)
  
--
I wish we could make it for these old pc's !!
  
Greeeeetz 
Pat'

---

### Post by Brunellus on 2005-11-24
if you're trying to make an old computer work, I suggest using XFCE (for computers with less that 256 MB RAM) or fluxbox (for computers with less than 128 MB RAM).

---

### Post by patrick295767 on 2005-11-24
I was with fvwm ...
as u certainly read in my other post, my damn old corel linux was faster than fvwm even ... 
 
I'll try xfce again, and wish it will work with oldest KDE versions !
I really liked like COREL LINUX KDE 1.1.2., much user friendly than fvwm for me ... 
 
 Thank you for your information, 
  
------------
Let's make re-live the KDE 1.1.2 or 2. sthg in Ubuntu !

---

### Post by patrick295767 on 2005-11-24
Btw, do you think I can get back my old cd of corellinux to use the KDE 1.1.2 files to install them in Ubuntu ?

---

### Post by patrick295767 on 2005-11-24
I have found the KDE 1.1.2 at this webpage:
[http://www.dia.uniroma3.it/db/roadRunner/rpmfind/bydistribution/samples/Distribution04.html](http://www.dia.uniroma3.it/db/roadRunner/rpmfind/bydistribution/samples/Distribution04.html)

I dont really know how I will install that on UBUNTU Server install ...

---

### Post by suRoot on 2005-11-24
I'm not trying to run you away from Ubuntu, but you may want to look at using Xandros which is the new name for Corel Linux.  I'm not that familiar with it, but a quick google leads me to believe that it contain the file manager that you want.  You can find it here:  [http://neo.caslab.queensu.ca/~bhall/ISO/xandros-301-ocd-installation.iso]("http://neo.caslab.queensu.ca/~bhall/ISO/xandros-301-ocd-installation.iso")

Aside from that, you may try finding ISOs of Corel somewhere, surely they're on an FTP archive somewhere.  I think what you're trying to do here with Breezy may not be a good idea.  You may well get that old version of KDE working, but I can almost assure you you're going to run in to a lot of other problems running the newer apps we're using today.  In the end, I think you'll find it was more trouble than it was worth.

---

### Post by Mr. Swiveller on 2005-11-24
Hi there Patrick,

It appears that the packages which you're planning to install are RPMs. These were made for Redhat-derived platforms (such as Redhat, Mandriva, and Fedora). 

Since Ubuntu is based on Debian Linux, you require either DEB packages, or the appropriate sourcecode, which you'd then have to compile yourself.

Note, though, that it is best to have DEB packages which were made for your specific flavour of Linux (e.g., Ubuntu Breezy), since these are most likely to be compatible with your setup. 

Cheers,

Swiveller

---

### Post by patrick295767 on 2005-11-24
[QUOTE=suRoot]I'm not trying to run you away from Ubuntu, but you may want to look at using Xandros which is the new name for Corel Linux.  I'm not that familiar with it, but a quick google leads me to believe that it contain the file manager that you want.  You can find it here:  [http://neo.caslab.queensu.ca/~bhall/ISO/xandros-301-ocd-installation.iso]("http://neo.caslab.queensu.ca/~bhall/ISO/xandros-301-ocd-installation.iso")

Aside from that, you may try finding ISOs of Corel somewhere, surely they're on an FTP archive somewhere.  I think what you're trying to do here with Breezy may not be a good idea.  You may well get that old version of KDE working, but I can almost assure you you're going to run in to a lot of other problems running the newer apps we're using today.  In the end, I think you'll find it was more trouble than it was worth.[/QUOTE]
  
I have plenty cd's of old linux at home 'cos I tried all distro at least once ... 
My conclusions were always this one: I LOVE UBUNTU !
  
I go home and figure out during way what to do ... I let you informed of my progression !
  
Thank you very much !!  Nice that there is experienced people like you to discuss with !
 
Greetz ' 
  
Pat'

---

### Post by patrick295767 on 2005-11-24
[QUOTE=patrick295767]I have plenty cd's of old linux at home 'cos I tried all distro at least once ... 
My conclusions were always this one: I LOVE UBUNTU !
  
I go home and figure out during way what to do ... I let you informed of my progression !
  
Thank you very much !!  Nice that there is experienced people like you to discuss with !
 
Greetz ' 
  
Pat'[/QUOTE]
(I will have a look in my corellinux cd, I have somewhere at home, what's the content in files ...)

---

### Post by ace2005 on 2005-11-24
[QUOTE=Brunellus]if you're trying to make an old computer work, I suggest using XFCE (for computers with less that 256 MB RAM) or fluxbox (for computers with less than 128 MB RAM).[/QUOTE]

Well i ran KDE on a system with 256 MB of ram for 6 months or so and it ran fine.

You never said what the specs of this PC you are going to put KDE 1.1.2

---

### Post by patrick295767 on 2005-11-24
256Mb ... , I wish I had ...
I have 64 MB with AMD proc.
  
--- Additional info now:
-----------------------------
I just burnt now the cd of CorelLinux and surprise !!!
It's a DEB type ! 
Plenty of deb files !
    
I tried tthe dpkg -i kde-corel_1.1-1254.deb --force
  (25MB file)
   
this results of course in a broken pipe ...
   
I made a list of the packages present on the cd ... 
```
Package: autofs
Version: 3.1.3-2
Section: utils
Priority: extra
Architecture: i386
Depends: libc6
Installed-Size: 117
Maintainer: Justin Maurer <justin@debian.org>
Description: A kernel-based automounter for Linux.
 The kernel automounter implements an almost complete SunOS style
 automounter under Linux. The automounter is supported by Linux kernels
 2.0.31 and higher or the 2.1.X series. Automounter support must
 be activated while compiling the kernel.
Filename: dists/corellinux-1.0/corel/binary-i386/autofs_3.1.3-2_i386.deb
Size: 41780
MD5sum: 52433ab73d97cbe70a17c9d9e777bec8

Package: gpm
Version: 1.14-3
Architecture: i386
Depends: libc6 (>= 2.0.7u), libncurses4, debianutils (>= 1.7)
Installed-Size: 211
Maintainer: James Troup <james@nocrew.org>
Description: General Purpose Mouse Interface
 This package provides a daemon that listens to the mouse when the
 console is displayed, and delivers them to applications.
 .
 The default when no application is running is to emulate
 "selection", i.e. allow cut-and-paste with the mouse on the
 console the same way as under X.
Filename: dists/corellinux-1.0/corel/binary-i386/gpm_1.14-3.deb
Size: 115438
MD5sum: 0f13e643799d6eaeaeaadae52569d6d1

Package: kde-corel-admin
Version: 1.1-1254
Architecture: i386
Depends: kde-corel 
Conflicts: kde
Section: Corel Desktop
Installed-Size: 163
Maintainer: Robert Schwartz <roberts@corel.com>
Description: Corel's KDE Desktop
 Corel's K Desktop Environment server administration tools.
Filename: dists/corellinux-1.0/corel/binary-i386/kde-corel-admin_1.1-1254.deb
Size: 54492
MD5sum: c0946e556b5cb610334681bbf03fa96e

Package: kde-corel
Version: 1.1-1254
Architecture: i386
Depends: qt-corel, smbfs, libpam0g, libapt-pkg2.5 
Suggests: samba
Conflicts: kde
Section: Corel Desktop
Installed-Size: 86242
Filename: dists/corellinux-1.0/corel/binary-i386/kde-corel_1.1-1254.deb
Maintainer: Robert Schwartz <roberts@corel.com>
Description: Corel's KDE Desktop
 Corel's K Desktop Environment.
Size: 25871488
MD5sum: a52c0a29e109e7f789229b08df856c03

Package: kernel-headers-2.2.12
Version: corel.1.0
Architecture: i386
Provides: kernel-headers
Installed-Size: 8199
Maintainer: Roberts Schwartz <roberts@corel.com>
Source: kernel-source-2.2.12
Description: Header files related to a specific Linux kernel.
 This package provides kernel header files, for sites that want the latest
 kernel headers. Please read /usr/doc/kernel-headers-2.2.12/debian.README.gz
 for details
Filename: dists/corellinux-1.0/corel/binary-i386/kernel-headers-2.2.12_corel.1.0_i386.deb
Size: 1666056
MD5sum: fe3d758354782b55f06f702f805edabf

Package: kernel-source-2.2.12
Version: corel.1.0
Architecture: all
Depends: binutils | gas
Recommends: libc-dev, gcc, make
Suggests: ncurses-dev, tk-dev, kernel-package, bin86
Provides: kernel-source
Installed-Size: 14706
Maintainer: Roberts Schwartz <roberts@corel.com>
Description: Linux kernel source.
 This package provides the source code for the Linux kernel, as well
 as the scripts that maintain the symbolic link /usr/src/linux).
 .
 You may configure the kernel to your setup by typing "make config"
 and following instructions, but you could get ncursesX.X-dev and
 tk4X-dev and try "make menuconfig" for a jazzier, and easier to use
 interface. Also, on intel platforms, you MUST get bin86 if
 you wish to compile the kernel sources. Ignore the suggestion to get bin86
 for non intel architectures. Also, please read the detailed documentation
 /usr/doc/kernel-source-2.2.12/README.headers.gz.
 .
 If you wish to use this package to create a custom Linux kernel, then
 it is suggested that you investigate the package kernel-package,
 which has been designed to ease the task of creating kernel image
 packages.
Filename: dists/corellinux-1.0/corel/binary-i386/kernel-source-2.2.12_corel.1.0_all.deb
Size: 14973296
MD5sum: be397484725cacf8d4442ac3af807eb8


Package: login
Version: 980403-0.3.2
Section: base
Priority: required
Architecture: i386
Essential: yes
Pre-Depends: libc6
Conflicts: shadow-login
Replaces: shadow-login, shadow-passwd
Installed-Size: 153
Maintainer: Guy Maor <maor@debian.org>
Source: shadow
Description: Sign on to the system.
 login and newgrp change the user and group.
Filename: dists/corellinux-1.0/corel/binary-i386/login_980403-0.3.2_i386.deb
Size: 78810
MD5sum: 5fb7f37a3489382ca0b2d76aee867b2c

Package: lpr
Version: 1:0.46-1-0slink1
Section: net
Priority: standard
Architecture: i386
Depends: libc6, netbase
Suggests: magicfilter | apsfilter, gs
Installed-Size: 197
Maintainer: Adam Klein <aklein@debian.org>
Description: BSD lpr/lpd line printer spooling system
 This is the BSD printer spooler and associated utilities.
 You can use this for local and remote printers.
 .
 If you install magicfilter or apsfilter (along with gs),
 lpr will be able to automatically handle special file types
 (such as Postscript and PDF files).
Filename: dists/corellinux-1.0/corel/binary-i386/lpr_0.46-1-0slink1_i386.deb
Size: 82698
MD5sum: 694600a076aee86b99780c5e915fb901

Package: motifnls
Version: 2.1-5
Architecture: all
Installed-Size: 78
Maintainer: Nadya Fenton <nadyaf@corel.com> 
Description: Files needed to run some Motif applications.
 This package provides the XFree-2.1 configuration files
 needed to allow Motif applications compiled under XFree-2.1
 to run under XFree-3.1.
 .
 Without these files, some Motif applications compiled on
 other machines (such as Netscape) may crash when attempting
 to copy or paste from or to a text field, and may also
 exhibit other problems.
Filename: dists/corellinux-1.0/corel/binary-i386/motifnls_2.1-5.deb
Size: 11976
MD5sum: b75dc309a69c6b49de5320c31d59cb35

Package: navigator4
Version: 4.7-4
Section: web
Priority: optional
Architecture: i386
Depends: motifnls, libc6 (>= 2.0.7u), libg++272 (>= 2.7.2.8), xlib6g (>= 3.3-5), xpm4g (>= 3.4j-0)
Recommends: mime-support
Suggests: imagemagick
Conflicts: netscape, netscape-beta
Replaces: netscape, netscape3, netscape-beta
Provides: netscape, www-browser, news-reader, mail-reader
Installed-Size: 11714
Maintainer: Nadya Fenton <nadyaf@corel.com> 
Description: Popular World-Wide-Web browser software (installer)
 Netscape (pronounced "Mozilla") is a graphical World-Wide-Web browser
 with many features.  It supports advanced features of HTML and new
 technologies such as "Java" from Sun Microsystems.
 .
 You will need the "ImageMagick" package installed if you wish to
 get inline support of image types not directly supported by netscape.
 .
 Netscape Communications Corporation does not allow redistribution of
 their software.  Therefore, this package requires the user to fetch
 the netscape archive separately and place it in the directory pointed
 to by the TMPDIR environment variable (or /tmp if TMPDIR not defined)
 before attempting to install this package.  You can get the linux
 package via anonymous ftp from "ftp.netscape.com" under the
 directory "/pub/communicator".  The archive must be readable and
 owned by root before it can be installed.
 .
 Note: You'll need a "glibc2" version of the archive for this
 installer.
Filename: dists/corellinux-1.0/corel/binary-i386/navigator4_4.7-4_i386.deb
Size: 11888508
MD5sum: 8703f59721fa600aafc7bd1eeb646000

Package: passwd
Version: 980403-0.3.2
Section: base
Priority: required
Architecture: i386
Depends: libc6, login (>= 970502-1)
Conflicts: shadow-passwd
Replaces: manpages (<=1.15-2)
Installed-Size: 609
Maintainer: Guy Maor <maor@debian.org>
Source: shadow
Description: Change and administer password and group data.
 This package includes passwd, chsh, chfn, and many other programs to
 maintain password and group data.
 .
 Shadow passwords are supported.  See /usr/doc/passwd/README.Debian
Filename: dists/corellinux-1.0/corel/binary-i386/passwd_980403-0.3.2_i386.deb
Size: 215116
MD5sum: 2811a7f7de94e94fd1deb1d218ba14d4

Package: printfilters 
Version: 1.2 
Section: misc 
Priority: optional
Architecture: i386
Installed-Size: 127
Maintainer: Doreen <doreenw@corel.ca>
Description: Print filters for automated printing  
 Print filters that help to automate the output for various
 printers. 
Filename: dists/corellinux-1.0/corel/binary-i386/printfilter_1.2.deb
Size: 23564
MD5sum: 116b9abcc115407012e81b2f8e48cb63

Package: proftpd
Version: 1.2.0pre9-4
Section: net
Priority: extra
Architecture: i386
Depends: netbase (>= 2.0), libc6, perl | perl5
Conflicts: wu-ftpd, wu-ftpd-academ, ftp-server
Provides: ftp-server
Installed-Size: 614
Maintainer: Johnie Ingram <johnie@debian.org>
Description: Versatile, virtual-hosting FTP daemon
 A powerful replacement for wu-ftpd, this File Transfer Protocol
 daemon supports hidden directories, virtual hosts, and per-directory
 ".ftpaccess" files.  It uses a single main configuration file, with a
 syntax similar to Apache.
 .
 Because of the advanced design, anonymous-FTP directories can have
 an arbitrary internal structure (bin, lib, etc, and special files are
 not needed).  Advanced features like multiple password files and
 upload/download ratios are also supported.
 .
 More information can be found at http://www.proftpd.org/.
Filename: dists/corellinux-1.0/corel/binary-i386/proftpd_1.2.0pre9-4_i386.deb
Size: 305224
MD5sum: 26482b8817defe8eef78ff0b3f892a1d

Package: qmail-corel
Version: 1.03-1254
Architecture: i386
Depends: kde-corel 
Conflicts: kde
Conflicts: sendmail, mail-transport-agent
Provides: mail-transport-agent
Section: Corel Desktop
Installed-Size: 4092
Maintainer: Robert Schwartz <roberts@corel.com>
Description: Corel's qmail server
 Corel's Qmail server deb.
Filename: dists/corellinux-1.0/corel/binary-i386/qmail-corel_1.03-1254.deb
Size: 1435656
MD5sum: 09692c129473c72e3e76855ffcdac108

Package: qt-corel
Version: 1.44O-6
Architecture: i386
Conflicts: qt1, qt
Section: Corel Desktop
Installed-Size: 2408
Maintainer: Robert Schwartz <roberts@corel.com>
Description: qt libraries with Corel bug fixes
 QT is a library and framework for GUI development.  If you have
 applications linked against the shared library *libqt* you'll need
 to install this package.  For own development using QT you should
 install the qt-dev and probably the qt-doc package.
Filename: dists/corellinux-1.0/corel/binary-i386/qt-corel_1.44O-6_slink.deb
Size: 923660
MD5sum: c6385ef6f803c64bf288bc74a9462cc3

Package: samba-doc
Version: 2.0.5a-1
Section: net
Priority: optional
Architecture: all
Installed-Size: 971
Maintainer: Eloy A. Paris <peloy@debian.org>
Source: samba
Description: Samba documentation.
 The Samba software suite is a collection of programs that
 implements the SMB protocol for unix systems, allowing you to serve
 files and printers to Windows, NT, OS/2 and DOS clients. This protocol
 is sometimes also referred to as the LanManager or Netbios protocol.
 .
 This package contains all the documentation that comes in the original
 tarball.
Filename: dists/corellinux-1.0/corel/binary-i386/samba-doc_2.0.5a-1_all.deb
Size: 423650
MD5sum: a9c1addcff72605f66a2334eef5e25ef

Package: secure-su
Version: 980403-0.3.2
Section: admin
Priority: optional
Architecture: i386
Depends: libc6, login (>= 970502-1)
Conflicts: shadow-su
Replaces: shadow-su
Installed-Size: 51
Maintainer: Guy Maor <maor@debian.org>
Source: shadow
Description: su with more security options
 secure-su offers more security options than the normal su, such as a
 wheel group, and from-user and to-user specific restrictions.
Filename: dists/corellinux-1.0/corel/binary-i386/secure-su_980403-0.3.2_i386.deb
Size: 22376
MD5sum: 867117abdd02aedccfac02eaec6b26ed

Package: twm
Version: 3.3.5-1.0.1
Architecture: i386
Depends: libc6, xlib6g (>= 3.3.5-1)
Recommends: xterm
Replaces: xbase (<< 3.3.2.3a-2)
Provides: x-window-manager
Installed-Size: 221
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: Tab window manager
 twm is a window manager for the X Window System.  It provides title bars,
 shaped windows, several forms of icon management, user-defined macro
 functions, click-to-type and pointer-driven keyboard focus, and user-specified
 key and pointer button bindings.
Filename: dists/corellinux-1.0/corel/binary-i386/twm_3.3.5-1.0.1_i386.deb
Size: 119524
MD5sum: 53a2879226d103c3053ba71c14613529

Package: xbase-clients
Version: 3.3.5-1.0.1
Architecture: i386
Depends: cpp, libc6, libncurses4, xlib6g (>= 3.3.5-1), zlib1g (>= 1:1.1.3)
Conflicts: xbase (<< 3.3.2.3a-2), xserver-common (<< 3.3.2.3a-9), xmodmap,
 xaw-wrappers (<< 0.90), xfonts-100dpi (<< 3.3.3.1-3),
 xfonts-75dpi (<< 3.3.3.1-3), xfonts-base (<< 3.3.3.1-3),
 xfonts-cyrillic (<< 3.3.3.1-3), xfonts-scalable (<< 3.3.3.1-3),
 xfnt100 (<= 3.3.2.3a-1), xfnt75 (<= 3.3.2.3a-1), xfntbase (<= 3.3.2.3a-1),
 xfntcyr (<= 3.3.2.3a-1), xfntscl (<= 3.3.2.3a-1)
Replaces: xbase (<< 3.3.2.3a-2), xserver-common (<< 3.3.2.3a-9),
 xf86setup (<< 3.3.2.3a-9), xmodmap
Provides: xmodmap
Installed-Size: 2066
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: miscellaneous X clients
 An X client is a program that uses the X libraries to interface with an X
 server, and thus with some input and output hardware like a graphics card,
 monitor, keyboard, and pointer device (such as a mouse).  This package
 provides a miscellaneous assortment of X clients that ship with the X Window
 System, including xinit and startx, the programs that start an X session on
 demand from the command line; a bitmap editor and conversion utilities;
 utilities for font display and format conversion; a rudimentary screensaver,
 beforelight; X resource display and editing utilities; X server testing and
 performance evaluation programs; graphical clocks (xclock and oclock); X
 session access control programs; tools for use with the XKEYBOARD (XKB)
 extension; xmodmap, a tool for remapping keys and pointer buttons; a video
 mode tuner for XFree86 X servers; a screen/window capture program (and viewer
 for the captures); and several other programs of general utility in the X
 Window System.
Filename: dists/corellinux-1.0/corel/binary-i386/xbase-clients_3.3.5-1.0.1_i386.deb
Size: 930462
MD5sum: 6cbe476319c971a61582864f41afbe51

Package: xdm
Version: 3.3.5-1.0.1
Architecture: i386
Depends: cpp, libc6, xlib6g (>= 3.3.5-1)
Replaces: xbase (<< 3.3.2.3a-2)
Installed-Size: 215
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X display manager
 xdm manages a collection of X servers, which may be on the local host or
 remote machines.  It provides services similar to those provided by init,
 getty, and login on character-based terminals; prompting for login name and
 password, authenticating the user, and running a session.  xdm supports XDMCP
 (X Display Manager Control Protocol) and can also be used to run a chooser
 process which presents the user with a menu of possible hosts that offer XDMCP
 display management.
Filename: dists/corellinux-1.0/corel/binary-i386/xdm_3.3.5-1.0.1_i386.deb
Size: 111218
MD5sum: 5dc0ce0db05592de8fd4d48098b9054d

Package: xf86setup
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xbase-clients, xfonts-100dpi | xfonts-75dpi, xfonts-base,
 xserver-common, xserver-vga16 | xserver, libc6, tcl8.0 (>=8.0.4), tk8.0 (>=8.0.4), xlib6g (>= 3.3.5-1)
Replaces: xserver-vga16 (<< 3.3.2.3a-2), xbase (<< 3.3.2.3a-2)
Installed-Size: 719
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server configuration tools
 xf86setup contains two X clients used to configure XFree86 X servers.
 .
 XF86Setup itself is used to either perform the initial setup of the servers
 or to make adjustments to the existing configuration; when invoked from the
 console to initially configure the XFree86 servers, it will start the VGA16
 server and then allow configuration settings to be entered.  When run from
 within an already running server environment (e.g. from an xterm window),
 XF86Setup can be used to make adjustments to the current server
 configuration.
 .
 xf86setup also contains a graphical mouse configuration utility, xmseconfig.
 .
 Note to Alpha users: The XF86Setup program has no awareness of TGA
 hardware and cannot be used to configure the TGA server.
Filename: dists/corellinux-1.0/corel/binary-i386/xf86setup_3.3.5-1.0.1_i386.deb
Size: 223112
MD5sum: 55d2499f46e30f3a48bbfb5bf81ec585

Package: xfonts-100dpi
Version: 3.3.5-2
Section: x11
Priority: optional
Architecture: all
Depends: xbase-clients (>= 3.3.3.1-5)
Suggests: xfs | xserver
Conflicts: xfnt100
Replaces: xfnt100
Provides: xfnt100
Installed-Size: 1334
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-2
Description: 100 dpi fonts for X
 xfonts-100dpi provides a set of bitmapped fonts at 100 dots per inch.  In
 most cases it is desirable to have the X font server (xfs) and/or an X server
 installed to make the fonts available to X clients.
 .
 This package and xfonts-75dpi provide the same set of fonts, rendered at
 different resolutions; only one or the other is necessary, but both may be
 installed.  xfonts-100dpi may be more suitable for large monitors and/or
 large screen resolutions (over 1024x768).
Filename: dists/corellinux-1.0/corel/binary-i386/xfonts-100dpi_3.3.5-2_all.deb
Size: 1244752
MD5sum: 34efce9a1a5a561413c748f91c3eb96f

Package: xfonts-75dpi
Version: 3.3.5-2
Section: x11
Priority: optional
Architecture: all
Depends: xbase-clients (>= 3.3.3.1-5)
Suggests: xfs | xserver
Conflicts: xfnt75
Replaces: xfnt75
Provides: xfnt75
Installed-Size: 1178
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-2
Description: 75 dpi fonts for X
 xfonts-75dpi provides a set of bitmapped fonts at 75 dots per inch.  In most
 cases it is desirable to have the X font server (xfs) and/or an X server
 installed to make the fonts available to X clients.
 .
 This package and xfonts-100dpi provide the same set of fonts, rendered at
 different resolutions; only one or the other is necessary, but both may be
 installed.  xfonts-75dpi may be more suitable for small monitors and/or small
 screen resolutions (under 1024x768).
Filename: dists/corellinux-1.0/corel/binary-i386/xfonts-75dpi_3.3.5-2_all.deb
Size: 1072044
MD5sum: 7518f9524ff9ec0fe6b16bef5e493965

Package: xfonts-base
Version: 3.3.5-2
Section: x11
Priority: optional
Architecture: all
Depends: xbase-clients (>= 3.3.3.1-5)
Suggests: xfs | xserver
Conflicts: xfntbase
Replaces: xfntbase
Provides: xfntbase
Installed-Size: 282
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-2
Description: standard fonts for X
 xfonts-base provides a standard set of low-resolution bitmapped fonts.  In
 most cases it is desirable to have the X font server (xfs) and/or an X server
 installed to make the fonts available to X clients.
 .
 If you are not using a remote font server, you must install this package if
 you are installing an X server.  It contains fonts without which X servers
 will not work.
Filename: dists/corellinux-1.0/corel/binary-i386/xfonts-base_3.3.5-2_all.deb
Size: 216412
MD5sum: bdbf9d74ab0185042c537431227540c9

Package: xfree86-common
Version: 3.3.5-1.0.1
Architecture: all
Suggests: twm | x-window-manager, xbase-clients, xdm, xf86setup,
 xfonts-100dpi | xfonts-75dpi, xfonts-base, xfonts-scalable, xlib6g,
 xlib6g-dev, xserver-common, xserver-vga16 | xserver,
 xterm | x-terminal-emulator
Replaces: xbase (<< 3.3.2.3a-9), xlib6g-dev (<< 3.3.2.3a-2),
 xmanpages (<< 3.3.4), xstd
Installed-Size: 399
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X Window System (XFree86) infrastructure
 xfree86-common contains the filesystem infrastructure required for further
 installation of the X Window System in any configuration.
 .
 Those wishing an X server only (with remote font services and clients) will
 also require the xserver-common package and an X server package.
 .
 The counterpart to the above configuration is a machine with the X libraries
 (the xlib6g package), xbase-clients, a window manager, some X font packages,
 and likely many more client packages.
 .
 Those who desire a standalone X workstation (and/or are fuzzy on the concepts
 of X servers and X clients) will require both of the above sets of packages.
 A recommended minimal list of packages for such a configuration is:
 xbase-clients, xf86setup, xfonts-100dpi or xfonts-75dpi, xfonts-base,
 xfonts-scalable, xlib6g, xserver-common, an xserver (several are available,
 and which you use is largely dependent on your graphics hardware), a window
 manager (several are available, and which you use is largely a matter of
 preference), and a terminal emulator X client package (again, several are
 available and which you use is your decision).
 .
 A number of terms are used to refer to the X Window System, including "X", "X
 Version 11", "X11", "X11R6", and "X11R6.3".  The version of X used in Debian
 is derived from the version released by the XFree86 Project, Inc., and is
 thus often also referred to as "XFree86".  All of the preceding quoted terms
 are functionally interchangeable in a Debian system.
 .
 Still confused?  Install this package and then read the files in
 /usr/doc/xfree86-common/ for assistance.
Filename: dists/corellinux-1.0/corel/binary-i386/xfree86-common_3.3.5-1.0.1_all.deb
Size: 269610
MD5sum: 8dcffcc45c2a4537a116181a895daa1a

Package: xfs
Version: 3.3.5-1.0.1
Architecture: i386
Depends: libc6, zlib1g (>= 1:1.1.3)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-base, xfonts-scalable
Replaces: xbase (<< 3.3.2.3a-2)
Installed-Size: 378
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X font server
 xfs is a daemon that listens on a network port and serves X fonts to X
 servers (and thus to X clients).  All X servers have the ability to serve
 locally installed fonts for themselves, but xfs makes it possible to offload
 that job from the X server, and/or have a central repository of fonts on a
 networked machine running xfs so that all the machines running X servers on a
 network do not require their own set of fonts.  xfs may also be invoked by
 users to, for instance, make available X fonts in user accounts that are not
 available to the X server or to an already running system xfs.
Filename: dists/corellinux-1.0/corel/binary-i386/xfs_3.3.5-1.0.1_i386.deb
Size: 192166
MD5sum: bee64ab21fcc4aecb43bc18562357838




```

---

### Post by patrick295767 on 2005-11-24
```
Package: xlib6
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xlib6g (>= 3.3.2.3a-8), libc5 (>= 5.4.0-0)
Conflicts: elf-x11r6lib, xlib
Replaces: xbase (<< 3.3.2.3a-2), elf-x11r6lib, xlib
Installed-Size: 1797
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: shared libraries required by libc5 X clients
 The X libraries are the interface between X client programs and the
 hardware-oriented X servers, and consist of routines to read input from the
 keyboard and pointer, draw on the screen, etc., in an abstract manner that is
 independent of the particular characteristics of the hardware.  The X
 libraries communicate with X servers by means of the X protocol.  Xlib itself
 provides the low-level functionality; Xt, the X Toolkit Instrinsics, is often
 used as a foundation for widget libraries such as Lesstif or Athena.  Xaw,
 the Athena widget set, provides a rudimentary set of graphical user-interface
 elements (buttons, scrollbars, text boxes, etc.).  Several more libraries are
 provided to implement the functions of various X extensions.
 .
 X clients compiled against libc5 require that the X libraries be compiled
 against libc5 as well.  xlib6 provides such backward compatibility.
Filename: dists/corellinux-1.0/corel/binary-i386/xlib6_3.3.5-1.0.1_i386.deb
Size: 773534
MD5sum: 4c51762b2e725db2d073981a13ee5b7e

Package: xlib6g-dev
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xlib6g (>= 3.3.2.3a-8), libc6-dev, cpp
Recommends: xmanpages
Conflicts: xdevel
Replaces: xbase (<< 3.3.2.3a-2), xdevel
Installed-Size: 6156
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: include files and libraries for X client development
 xlib6g-dev provides the standard set of include files for X, and some
 non-shared libraries (with debugging symbols) required for X client
 development.  You only need to install it if you intend to compile X clients
 yourself.
 .
 This package only provides statically linked libraries if there is no
 dynamically linked version available.  For statically linked versions of the
 libraries in the xlib6g package, see the xlib6g-static package.
Filename: dists/corellinux-1.0/corel/binary-i386/xlib6g-dev_3.3.5-1.0.1_i386.deb
Size: 1319306
MD5sum: be1caebda31a2daf54b1f53ad7aa4d36

Package: xlib6g
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xfree86-common, libc6
Conflicts: xlib, xlib6 (<< 3.3.2.3a-8), xlib6g-dev (<< 3.3.2.3a-2)
Replaces: xlib, xbase (<< 3.3.2.3a-2), xlib6 (<< 3.3.2.3a-8),
 xlib6g-dev (<< 3.3.2.3a-2)
Installed-Size: 3128
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: shared libraries required by X clients
 The X libraries are the interface between X client programs and the
 hardware-oriented X servers, and consist of routines to read input from the
 keyboard and pointer, draw on the screen, etc., in an abstract manner that is
 independent of the particular characteristics of the hardware.  The X
 libraries communicate with X servers by means of the X protocol.  Xlib itself
 provides the low-level functionality; Xt, the X Toolkit Intrinsics, is often
 used as a foundation for widget libraries such as Lesstif or Athena.  Xaw,
 the Athena widget set, provides a rudimentary set of graphical user-interface
 elements (buttons, scrollbars, text boxes, etc.).  Several more libraries are
 provided to implement the functions of various X extensions.
 .
 xlib6g also contains the XKB specification files, locale data, and the bitmap
 image files that ship with X11R6.3.
Filename: dists/corellinux-1.0/corel/binary-i386/xlib6g_3.3.5-1.0.1_i386.deb
Size: 978316
MD5sum: 290b9b3f8846d07908580113b3a85567

Package: xmms 
Version: 0.9.5.1-1 
Section: sound 
Priority: extra
Architecture: i386
Installed-Size: 19255 
Maintainer: Dave Neil <davidne@corel.com>
Description: An X11 audio player 
 An X11 audio player that has a gtk user interface.
Filename: dists/corellinux-1.0/corel/binary-i386/xmms_0.9.5.1-1.deb
Size: 6397438
MD5sum: fe99aef1c6a08d17c29a6947e63fc773

Package: xscreensaver
Version: 2.34-1
Architecture: i386
Depends: lesstifg (>= 1:0.85.2), libc6 (>= 2.0.7u), xlib6g (>= 3.3-5), xpm4g (>= 3.4j-0)
Suggests: xdaliclock, xv, xscreensaver-gl, fortune
Installed-Size: 2655
Maintainer: Larry Daffner <vizzie@airmail.net>
Description: Automatic screensaver for X
 The purpose of xscreensaver is to display pretty pictures on your screen
 when it is not in use, in keeping with the philosophy that unattended
 monitors should always be doing something interesting, just like they do
 in the movies.
 .
 The benefit that this program has over the combination of the xlock and
 xautolock programs is the ease with which new graphics hacks can be
 installed: you don't need to recompile this program to add a new display
 mode, you just change some resource settings.  Any program which can be
 invoked in such a way that it draws on the root window of the screen can
 now be used as a screensaver without modification.  The programs that
 are being run as screensavers don't need to have any special knowledge
 about what it means to be a screensaver.
Filename: dists/corellinux-1.0/corel/binary-i386/xscreensaver_2.34-1c.deb
Size: 965534
MD5sum: 04c81176c48c392824f19768dd450e46

Package: xserver-3dlabs
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Provides: xserver
Installed-Size: 2129
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for 3DLabs GLINT and Permedia-based graphics cards
 xserver-3dlabs is an 8-bit PseudoColor, 16-bit TrueColor, 24-bit
 TrueColor, and 32-bit TrueColor X server suitable for use with some 3DLabs
 GLINT 500TX, GLINT MX, Permedia, and Permedia 2 graphic accelerator
 boards.  24-bit operation is supported only on the Permedia 2.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-3dlabs_3.3.5-1.0.1_i386.deb
Size: 905824
MD5sum: 0c8f4e2cfecefa6104526da653a5b9f5

Package: xserver-agx
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1843
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for IBM XGA and IIT AGX-based graphics cards
 xserver-agx is an 8-bit PseudoColor and 16-bit TrueColor X server suitable for
 use with IIT AGX or IBM XGA graphic accelerator boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-agx_3.3.5-1.0.1_i386.deb
Size: 800864
MD5sum: 84229a16bfe75707474696d19479a8ce

Package: xserver-common
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xfree86-common, libc6
Suggests: xfonts-base, xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xbase (<< 3.3.2.3a-2), xsun-utils
Replaces: xbase (<< 3.3.2.3a-2), xserver-vga16 (<< 3.3.2.3a-2),
 xserver-agx (<< 3.3.2.3a-9), xserver-mach32 (<< 3.3.2.3a-9),
 xserver-mach64 (<< 3.3.2.3a-9), xserver-p9000 (<< 3.3.2.3a-9),
 xserver-s3 (<< 3.3.2.3a-9), xserver-s3v (<< 3.3.2.3a-9),
 xserver-tga (<< 3.3.2.3a-9), xserver-w32 (<< 3.3.2.3a-9), xsun-utils
Installed-Size: 780
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: files and utilities common to all X servers
 The X server is the hardware interface of the X Window System.  Its job is to
 communicate with video display and input devices, and present them in a
 standardized, abstract fashion via the X protocol to X clients (X-based
 programs).  The X server largely relieves programs of having to know or care
 about the details of the hardware with which they are interacting (such
 things as 32-bit versus 8-bit color, the layout of the keyboard, how many
 buttons the mouse has, etc.).  The catch is that the X server must itself
 know the technical specifications of the graphics hardware and monitor, the
 keyboard layout, the protocol used by the mouse, and so forth.
 .
 The X servers in Debian are authored by the XFree86 Project, Inc., which also
 distributes the rest of the X Window System source code for convenience.
 XFree86's X servers attempt where possible to take advantage of acceleration
 features present within the video hardware.
 .
 xserver-common contains files required by all XFree86 X servers, and includes
 a text-based program (xf86config) that configures the /etc/X11/XF86Config
 file, whose primary purpose is to describe the computer's video and input
 hardware to the X server.
 .
 All X servers either need fonts installed on the local host, or need to know
 of a remote host that provides font services (with xfs, for instance).  The
 former means that font packages are mandatory.  The latter means that font
 packages may be gratuitous.  To err on the side of caution, install at least
 the xfonts-base, xfonts-100dpi or xfonts-75dpi, and xfonts-scalable packages.
 .
 For a more sophisticated (and graphical) X server configuration tool, see
 the xf86setup package (currently for the i386 architecture only).
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-common_3.3.5-1.0.1_i386.deb
Size: 423482
MD5sum: 8f0585f92d4024be9c347843fff1f6f5

Package: xserver-i128
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 2100
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for Number Nine Imagine 128 graphics cards
 xserver-i128 is an X server suitable for use with Number Nine Imagine 128,
 Ticket 2 Ride, Revolution 3D, and Revolution IV graphics cards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-i128_3.3.5-1.0.1_i386.deb
Size: 896324
MD5sum: 8d6e3e333bd35def971f552ae9bbd351

Package: xserver-mach32
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1803
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for ATI Mach32-based graphics cards
 xserver-mach32 is an 8-bit PseudoColor and 16-bit TrueColor X server suitable
 for use with ATI Mach32 graphic accelerator boards.  16-bit operation is not
 supported on all accelerator boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-mach32_3.3.5-1.0.1_i386.deb
Size: 787356
MD5sum: 1da4ebd4173215282a3681178ffa6961

Package: xserver-mach64
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1931
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for ATI Mach64-based graphics cards
 xserver-mach64 is an 8-bit PseudoColor, 16-bit TrueColor, and 32-bit TrueColor
 X server suitable for use with ATI Mach64, 3D Rage, 3D Rage II, and 3D Rage
 Pro accelerator boards.  16-bit and 32-bit operation is not supported on all
 accelerator boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-mach64_3.3.5-1.0.1_i386.deb
Size: 834606
MD5sum: 090b612ce9537184b5e01639ced3616a

Package: xserver-mach8
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1672
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for ATI Mach8-based graphics cards
 xserver-mach8 is an 8-bit PseudoColor X server suitable for use with ATI Mach8
 graphic accelerator boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-mach8_3.3.5-1.0.1_i386.deb
Size: 730140
MD5sum: c44a148ddbeae18f0586cbcd68705cd2

Package: xserver-p9000
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1865
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for Weitek P9000-based graphics cards
 xserver-p9000 is an 8-bit PseudoColor, 16-bit TrueColor, and 32-bit TrueColor
 X server suitable for use with Weitek Power 9000 (P9000) graphic accelerator
 boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-p9000_3.3.5-1.0.1_i386.deb
Size: 809816
MD5sum: becdbc25d4593595d583ffc63ca47cb6

Package: xserver-s3
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 2346
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for S3 chipset-based graphics cards
 xserver-s3 is an 8-bit PseudoColor, 16-bit TrueColor, and 32-bit TrueColor
 X server suitable for use with S3 graphic accelerator boards (with some
 exceptions, like the ViRGE and ViRGE/VX series).  16-bit and 32-bit operation
 is not supported on all accelerator boards.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-s3_3.3.5-1.0.1_i386.deb
Size: 989032
MD5sum: 6eaff2e46c2da919e6d71904ab8860c9

Package: xserver-s3v
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 2078
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for S3 ViRGE and ViRGE/VX-based graphics cards
 xserver-s3v is an 8-bit PseudoColor and 16-bit TrueColor X server suitable for
 use with S3 ViRGE and ViRGE/VX graphic accelerator boards. In most cases use
 of this X server is deprecated in favor of the SVGA X server.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-s3v_3.3.5-1.0.1_i386.deb
Size: 889626
MD5sum: 070bb52920c5f333d9ed5d77abae86c6

Package: xserver-svga
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 3128
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for SVGA graphics cards
 xserver-svga is an 8-bit PseudoColor, 16-bit TrueColor, and 24-bit TrueColor
 X server suitable for use with many Super VGA video cards; video chipsets
 supported include models from Ark Logic, Alliance, ATI, Avance Logic, Chips
 & Technologies, Cirrus Logic, Compaq, Cyrix, Epson, Genoa, Matrox, MX, NCR,
 NVidia(/SGS Thomson), NeoMagic, Oak, RealTek, Rendition, S3, SiS, Tseng,
 Video7(/Headland Technologies), and Western Digital(/Paradise).  16-bit and
 24-bit TrueColor are currently only supported for some chipsets.
 .
 Note to Alpha users: Only the Matrox, NVidia, S3 Virge, and Trident drivers
 are provided for this architecture.  This server also does not support TGA
 hardware.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-svga_3.3.5-1.0.1_i386.deb
Size: 1306250
MD5sum: 9599b012f51189ef1a18d693c9de318f

Package: xserver-vga16
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1893
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for VGA graphics cards
 xserver-vga16 is a 16-color X server suitable for use with most VGA-compatible
 cards.  It also includes support for the non-VGA monochrome cards supported
 by the xserver-mono package.  For most people this X server is only useful to
 kick-start the XF86Setup program (in the xf86setup package).
 .
 Note to Alpha users: This server does not support TGA hardware.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-vga16_3.3.5-1.0.1_i386.deb
Size: 801136
MD5sum: 62ee793c0bd718a0acf6ed3c5949451d

Package: xserver-w32
Version: 3.3.5-1.0.1
Architecture: i386
Depends: xserver-common (>= 3.3.5), makedev (>= 1.6-8), libc6, zlib1g (>= 1:1.1.3)
Replaces: xbase (<< 3.3.2.1-1)
Provides: xserver
Installed-Size: 1716
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X server for Tseng ET4000/W32 and ET6000-based graphics cards
 xserver-w32 is an 8-bit PseudoColor X server suitable for use with Tseng
 ET4000/W32, ET4000/W32i, ET4000/W32p, and ET6000 graphics accelerator boards.
 For 16, 24 and 32 bit per pixel support on the ET6000, try the xserver-svga
 package.
Filename: dists/corellinux-1.0/corel/binary-i386/xserver-w32_3.3.5-1.0.1_i386.deb
Size: 742348
MD5sum: 50ad34daaa0f61bebb6bbc52b9bf5e6c

Package: xterm
Version: 3.3.5-1.0.1
Architecture: i386
Depends: ncurses-base, libc6, libncurses4, xlib6g (>= 3.3.5-1)
Conflicts: xbase (<< 3.3.2.3a-2)
Replaces: xbase (<< 3.3.2.3a-2)
Provides: x-terminal-emulator
Installed-Size: 566
Maintainer: Branden Robinson <branden@debian.org>
Source: xfree86-1
Description: X terminal emulator
 xterm is a terminal emulator for the X Window System.  It provides DEC VT102
 and Tektronix 4014 compatible terminals for programs that cannot use the
 window system directly.  This version implements ISO/ANSI colors and most of
 the control sequences used by DEC VT220 terminals.
Filename: dists/corellinux-1.0/corel/binary-i386/xterm_3.3.5-1.0.1_i386.deb
Size: 309368
MD5sum: be7d0b8f1aa97052ad147a69a0fa26e4
```

---

### Post by patrick295767 on 2005-11-24
The old guy is a : 
   
COMPAQ 1685 
K6-2 380 MHz - RAM 64 Mo - DD 4.3 Go - 
old ati church stuff as video
  
with even plenty bad clusters at the end of the harddisk ...
   
 It looks an old guy, isnt it ? :-)  :-)

Greetz', 
  
Pat'

---

### Post by aysiu on 2005-11-24
Damn Small Linux

---

### Post by patrick295767 on 2005-11-24
[QUOTE=aysiu]Damn Small Linux[/QUOTE]
  
I tried on it damn small linux, that's true it was going pretty well 
but the fluxbox was rather too muchfor the RAM of the pc
  
then, I got the idea of reducing the colors from 24b to 16bits :
that gave a good improvemnet but ... still a bit slow
  
To have like a normal fast pc while NET surfing and so on , was possible with 8 colors ... 
  
I think I am gonna make and try all possibilities at the end  :-)  
till the day it'll go to the dustbin ... :-)  :-) :D

---

### Post by patrick295767 on 2005-11-24
I like Ubuntu 'cos for drivers for my pcmcia, drinou, as pitux are SLACKWARE based 
and the slackware doesnt accept my exotic pcmcia card ... I experienced that Ubuntu masters so much drivers !! That's really impressive !

---

### Post by peanut butter on 2005-11-24
i'm not very expierenced here but woulden't icewm work?
you could also try other smalllinux distros like puppy.

---

### Post by aysiu on 2005-11-24
[QUOTE=patrick295767]I tried on it damn small linux, that's true it was going pretty well 
but the fluxbox was rather too muchfor the RAM of the pc[/QUOTE] According to Damn Small Linux's website it "Run[s] light enough to power a 486DX with 16MB of Ram."

---

### Post by patrick295767 on 2005-11-24
[QUOTE=aysiu]According to Damn Small Linux's website it "Run[s] light enough to power a 486DX with 16MB of Ram."[/QUOTE]
  
I am agree it's pretty fast ...  I have now temptation to re-try again ... 
  
But normally in Ubuntu, it should be possible to make a fast pc as the linux-damn small linux?

---

### Post by chroniker on 2005-11-24
Kbuntu default install is KDE, tho I don't know what version.

---

### Post by aysiu on 2005-11-24
[QUOTE=patrick295767]I am agree it's pretty fast ...  I have now temptation to re-try again ... 
  
But normally in Ubuntu, it should be possible to make a fast pc as the linux-damn small linux?[/QUOTE] This may help you:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by patrick295767 on 2005-11-24
[QUOTE=chroniker]Kbuntu default install is KDE, tho I don't know what version.[/QUOTE]
  
It will install the KDE version 3 sthg... 
(mandrake 6.1 for instance, at that time, was running a KDE 2.x (if I recall well))
the mandrake 7.1, had a KDE 2.x sure.

I still fighting with my broken packages of my KDE 1.1.2... 
I dont up to now really know how to make it ... 
  I have some headers ... 
I dont really manage now ... :-(

---

### Post by patrick295767 on 2005-11-24
I installed corellinux core, with a kde 1.1.2. The Ubuntu, installed as server, using fvwm, is in another partition. 
Ok, let's make the experiment : 
will UBUNTU+FVWM+Mozilla-Firefox  be faster or identical to the KDE 1.1.2 ??
  
I am rather curious !!

greetz'' 

 Pat'

---

### Post by patrick295767 on 2005-11-24
Result of the inverstigation:
-----------------------------------
  
CorelLINUX is damn fast !!!
the kde is a : version 1.1.2
corellinux : uname -a =>   2.2.12
 
debian base 
  
No doubts it's faster !
I dont know, that certainly the RAM the prob ... 
but the shit the usb ... no usb in corellinux 
  
I'll now install ubuntu !
to make the test

---

### Post by patrick295767 on 2005-11-24
We dont know why but this corellinux is faster than ubuntu+fvwm+mozilla-firefox
maybe mozilla ... the prob
  
and netscape should be used as in corellinux ...

---

### Post by patrick295767 on 2005-11-24
no way ...
I dont know how to install kde 1.1.2 from the deb ... 
it gives broken pipe...

---

