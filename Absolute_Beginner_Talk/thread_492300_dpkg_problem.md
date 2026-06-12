---
title: "dpkg problem"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by spookyct on 2007-07-04
I just installed kubuntu, and now I am having major problems installing software.  I am getting dpkg errors.  This is what I get with pretty much every package....


```
sujames@james-linux-box:~$ sudo aptitude install imwheel
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
james@james-linux-box:~$
james@james-linux-box:~$ sudo dpkg --configure -a
Setting up kde-icons-mono (3.5.6-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kde-icons-mono (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libgii1-target-x (1.0.1-3) ...
Setting up kdebase-data (3.5.6-0ubuntu20.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdebase-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up avahi-utils (0.6.17-0ubuntu3) ...
Setting up libavcodec0d (0.cvs20060823-3.1ubuntu4) ...

Setting up koffice-data (1.6.2-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing koffice-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-app-install (0.3.31) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 2
Setting up pidgin-data (2.0.2-1~getdeb1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing pidgin-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libsdl-image1.2 (1.2.5-2) ...

Setting up libpostproc0d (0.cvs20060823-3.1ubuntu4) ...

Setting up libsvga1 (1.4.3-24) ...

dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up libwxbase2.6-0 (2.6.3.2.1.5ubuntu6) ...

Setting up smlnj (110.54-0ubuntu1) ...

Setting up libxosd2 (2.2.14-1.3) ...

dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kcontrol depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash:
 ksplash depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 ksplash depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing ksplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash-engine-moodin:
 ksplash-engine-moodin depends on ksplash (>= 4:3.5.5-1); however:
  Package ksplash is not configured yet.
dpkg: error processing ksplash-engine-moodin (--configure):
 dependency problems - leaving unconfigured
Setting up msttcorefonts (1.8ubuntu1) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
/bin/sh: Can't open id
[: 16: 0: unexpected operator

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--15:10:43--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      224.71K/s

15:10:44 (224.29 KB/s) - `./andale32.exe' saved [198384/198384]

--15:10:44--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      224.37K/s

15:10:45 (223.50 KB/s) - `./arialb32.exe' saved [168176/168176]

--15:10:45--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      412.31K/s

15:10:47 (411.57 KB/s) - `./arial32.exe' saved [554208/554208]

--15:10:47--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      274.22K/s

15:10:48 (273.42 KB/s) - `./comic32.exe' saved [246008/246008]

--15:10:48--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      424.01K/s

15:10:50 (422.67 KB/s) - `./courie32.exe' saved [646368/646368]

--15:10:50--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      342.97K/s

15:10:52 (342.28 KB/s) - `./georgi32.exe' saved [392440/392440]

--15:10:52--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      228.85K/s

15:10:53 (228.62 KB/s) - `./impact32.exe' saved [173288/173288]

--15:10:53--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      407.98K/s

15:10:55 (407.03 KB/s) - `./times32.exe' saved [661728/661728]

--15:10:55--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      336.08K/s

15:10:56 (335.27 KB/s) - `./trebuc32.exe' saved [357200/357200]

--15:10:56--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      328.33K/s

15:10:57 (327.54 KB/s) - `./verdan32.exe' saved [351992/351992]

--15:10:57--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      247.91K/s

15:10:58 (247.35 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.

Setting up libdc1394-13 (1.1.0-3ubuntu2) ...

Setting up kdelibs-data (3.5.6-0ubuntu14) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdelibs-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdm:
 kdm depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kdm depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kdm (--configure):
 dependency problems - leaving unconfigured
Setting up libtar (1.2.11-4) ...

Setting up libdvdnav4 (0.1.10-0.1) ...

dpkg: dependency problems prevent configuration of koffice-libs:
 koffice-libs depends on koffice-data (>> 1:1.6.2); however:
  Package koffice-data is not configured yet.
 koffice-libs depends on koffice-data (<< 1:1.6.3); however:
  Package koffice-data is not configured yet.
dpkg: error processing koffice-libs (--configure):
 dependency problems - leaving unconfigured
Setting up libglide2 (2002.04.10-14) ...

dpkg: dependency problems prevent configuration of kicker:
 kicker depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kicker depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
Setting up libiso9660-4 (0.76-1ubuntu2) ...

Setting up libdvbpsi4 (0.1.5-2) ...

Setting up libgii1 (1.0.1-3) ...

dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on kcontrol (= 4:3.5.6-0ubuntu20.1); however:
  Package kcontrol is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ]
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs-data (>= 4:3.1.4-2); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Setting up libggi2 (2.2.1-5ubuntu1) ...

dpkg: dependency problems prevent configuration of kexi:
 kexi depends on koffice-libs (>= 1:1.6.2); however:
  Package koffice-libs is not configured yet.
 kexi depends on koffice-libs (<< 1:1.6.3); however:
  Package koffice-libs is not configured yet.
dpkg: error processing kexi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-default-settings:
 kubuntu-default-settings depends on kdm; however:
  Package kdm is not configured yet.
 kubuntu-default-settings depends on ksplash-engine-moodin; however:
  Package ksplash-engine-moodin is not configured yet.
dpkg: error processing kubuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.6); however:
  Package kdelibs-data is not configured yet.
 kdelibs4c2a depends on kdelibs-data (<< 4:3.5.7); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kontact:
 kontact depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kontact (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b2:
 libk3b2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libk3b2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krdc:
 krdc depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing krdc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of keep:
 keep depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing keep (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdemultimedia-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmime2:
 libkmime2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkmime2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-common:
 adept-common depends on konsole (>= 3.5.0); however:
  Package konsole is not configured yet.
dpkg: error processing adept-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knotes:
 knotes depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knotes (--configure):
 dependency problems - leaving unconfigured
Setting up libwxgtk2.6-0 (2.6.3.2.1.5ubuntu6) ...

dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkexiv2-0:
 libkexiv2-0 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkexiv2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-kfile-plugins:
 kdenetwork-kfile-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdenetwork-kfile-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-systemsettings:
 kde-systemsettings depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kde-systemsettings depends on kcontrol; however:
  Package kcontrol is not configured yet.
dpkg: error processing kde-systemsettings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmailcvt:
 kmailcvt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmailcvt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knetworkconf:
 knetworkconf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knetworkconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kppp:
 kppp depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpdf:
 kpdf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpdf (--configure):
 dependency problems - leaving unconfigured
Setting up libvlc0 (0.8.6.release-0ubuntu4) ...

dpkg: dependency problems prevent configuration of libktnef1:
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libktnef1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kio-apt:
 kio-apt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kio-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpf:
 kpf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde3:
 python-kde3 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 python-kde3 depends on konsole; however:
  Package konsole is not configured yet.
dpkg: error processing python-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq4:
 libkonq4 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkonq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdnssd:
 kdnssd depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdnssd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-qt:
 apport-qt depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-updater:
 adept-updater depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-updater depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-updater (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcron:
 kcron depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kcron (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 kde-icons-mono
 kdebase-data
 capplets-data
 koffice-data
 gnome-app-install
 pidgin-data
 gnome-control-center
 kcontrol
 ksplash
 ksplash-engine-moodin
 kdelibs-data
 gnome-panel-data
 kdm
 koffice-libs
 kicker
 konqueror
 apport
 k3b
 kexi
 kubuntu-default-settings
 kdelibs4c2a
 kontact
 konsole
 libk3b2
 krdc
 keep
 kdemultimedia-kio-plugins
 libkmime2
 adept-common
 knotes
 apport-gtk
 libkexiv2-0
 kdenetwork-kfile-plugins
 kdebase-bin
 kde-systemsettings
 kmailcvt
 knetworkconf
 kppp
 kpdf
 libktnef1
 kio-apt
 kpf
 gnome-panel
 python-kde3
 libkonq4
 kdnssd
 apport-qt
 kaffeine
 kate
 adept-updater
 kcron
Processing was halted because there were too many errors.

```


Is there an easy fix for this?  I really don't want to format/re-install ubuntu again.

---

### Post by supersonicdarky on 2007-07-04
if you look closely you'll see
> E: dpkg was interrupted, you must manually run '**dpkg --configure -a**' to correct the problem.

---

### Post by bigken on 2007-07-04
sudo dpkg --configure -a

---

### Post by spookyct on 2007-07-04
I did run that.  The output begins on line 13

---

### Post by spookyct on 2007-07-04
This may be a bit more clear.

```
james@james-linux-box:~$ sudo dpkg --configure -a
Password:
Setting up kde-icons-mono (3.5.6-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kde-icons-mono (--configure):
 subprocess post-installation script returned error exit status 2
Setting up kdebase-data (3.5.6-0ubuntu20.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdebase-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up koffice-data (1.6.2-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing koffice-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-app-install (0.3.31) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 2
Setting up pidgin-data (2.0.2-1~getdeb1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing pidgin-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up vlc-plugin-glide (0.8.6.release-0ubuntu4) ...
Setting up vlc-plugin-sdl (0.8.6.release-0ubuntu4) ...
Setting up vlc-plugin-alsa (0.8.6.release-0ubuntu4) ...
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up emacs21 (21.4a+1-2ubuntu1) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done

dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kcontrol depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash:
 ksplash depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 ksplash depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing ksplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash-engine-moodin:
 ksplash-engine-moodin depends on ksplash (>= 4:3.5.5-1); however:
  Package ksplash is not configured yet.
dpkg: error processing ksplash-engine-moodin (--configure):
 dependency problems - leaving unconfigured
Setting up kdelibs-data (3.5.6-0ubuntu14) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdelibs-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdm:
 kdm depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kdm depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of koffice-libs:
 koffice-libs depends on koffice-data (>> 1:1.6.2); however:
  Package koffice-data is not configured yet.
 koffice-libs depends on koffice-data (<< 1:1.6.3); however:
  Package koffice-data is not configured yet.
dpkg: error processing koffice-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kicker:
 kicker depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kicker depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on kcontrol (= 4:3.5.6-0ubuntu20.1); however:
  Package kcontrol is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ]
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs-data (>= 4:3.1.4-2); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kexi:
 kexi depends on koffice-libs (>= 1:1.6.2); however:
  Package koffice-libs is not configured yet.
 kexi depends on koffice-libs (<< 1:1.6.3); however:
  Package koffice-libs is not configured yet.
dpkg: error processing kexi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-default-settings:
 kubuntu-default-settings depends on kdm; however:
  Package kdm is not configured yet.
 kubuntu-default-settings depends on ksplash-engine-moodin; however:
  Package ksplash-engine-moodin is not configured yet.
dpkg: error processing kubuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.6); however:
  Package kdelibs-data is not configured yet.
 kdelibs4c2a depends on kdelibs-data (<< 4:3.5.7); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kontact:
 kontact depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kontact (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b2:
 libk3b2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libk3b2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krdc:
 krdc depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing krdc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of keep:
 keep depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing keep (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdemultimedia-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmime2:
 libkmime2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkmime2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-common:
 adept-common depends on konsole (>= 3.5.0); however:
  Package konsole is not configured yet.
dpkg: error processing adept-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knotes:
 knotes depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knotes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkexiv2-0:
 libkexiv2-0 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkexiv2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-kfile-plugins:
 kdenetwork-kfile-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdenetwork-kfile-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-systemsettings:
 kde-systemsettings depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kde-systemsettings depends on kcontrol; however:
  Package kcontrol is not configured yet.
dpkg: error processing kde-systemsettings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmailcvt:
 kmailcvt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmailcvt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knetworkconf:
 knetworkconf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knetworkconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kppp:
 kppp depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpdf:
 kpdf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktnef1:
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libktnef1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kio-apt:
 kio-apt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kio-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpf:
 kpf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde3:
 python-kde3 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 python-kde3 depends on konsole; however:
  Package konsole is not configured yet.
dpkg: error processing python-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq4:
 libkonq4 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkonq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdnssd:
 kdnssd depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdnssd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-qt:
 apport-qt depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-updater:
 adept-updater depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-updater depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-updater (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcron:
 kcron depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kcron (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 kde-icons-mono
 kdebase-data
 capplets-data
 koffice-data
 gnome-app-install
 pidgin-data
 gnome-control-center
 kcontrol
 ksplash
 ksplash-engine-moodin
 kdelibs-data
 gnome-panel-data
 kdm
 koffice-libs
 kicker
 konqueror
 apport
 k3b
 kexi
 kubuntu-default-settings
 kdelibs4c2a
 kontact
 konsole
 libk3b2
 krdc
 keep
 kdemultimedia-kio-plugins
 libkmime2
 adept-common
 knotes
 apport-gtk
 libkexiv2-0
 kdenetwork-kfile-plugins
 kdebase-bin
 kde-systemsettings
 kmailcvt
 knetworkconf
 kppp
 kpdf
 libktnef1
 kio-apt
 kpf
 gnome-panel
 python-kde3
 libkonq4
 kdnssd
 apport-qt
 kaffeine
 kate
 adept-updater
 kcron
Processing was halted because there were too many errors.
james@james-linux-box:~$       
```

---

### Post by bigken on 2007-07-04
I would try rebooting the pc and select safe mode or what ever its called then run the command also try running sudo apt-get update and sudo apt-get upgrade 
after the sudo dpkg --configure -a 

good luck

---

### Post by diatribe on 2007-07-04
try apt-get -f install, it might help also

---

### Post by spookyct on 2007-07-04
Did not work.  I am still getting the same errors.

I tried both suggestions

---

### Post by overdrank on 2007-07-04
> **spookyct said:**
> Did not work.  I am still getting the same errors.

I tried both suggestions

Hi have you tried to go to synaptic manager and fix broken packages? You may have to search for your broken packages under filters. Hope this helps good luck!

---

### Post by spookyct on 2007-07-04
This isn't working...

I am going to try to re-install some packages

---

### Post by bigken on 2007-07-04
after you fixed the packages did you run  sudo dpkg --configure -a ?

---

### Post by spookyct on 2007-07-04
yes, still no change.  I have not re-installed all of them.  that would take years.  It takes about 5 minutes to produce that error, and that error comes up on every install.

---

### Post by spookyct on 2007-07-07
I am still having this problem!  Any new solutions?

---

### Post by abn91c on 2007-07-07
> **diatribe said:**
> try apt-get -f install, it might help also

it's actually sudo apt-get install -f

---

### Post by spookyct on 2007-07-08
```
james@james-linux-box:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
142 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gnome-applets-data (2.18.0-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up update-manager-core (0.59.23) ...

Setting up kdelibs-data (3.5.6-0ubuntu14) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdelibs-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.6); however:
  Package kdelibs-data is not configured yet.
 kdelibs4c2a depends on kdelibs-data (<< 4:3.5.7); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-common:
 adept-common depends on konsole (>= 3.5.0); however:
  Package konsole is not configured yet.
dpkg: error processing adept-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-manager:
 adept-manager depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-manager depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-installer:
 adept-installer depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-installer depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-updater:
 adept-updater depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-updater depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-updater (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-notifier:
 adept-notifier depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-notifier depends on adept-updater; however:
  Package adept-updater is not configured yet.
dpkg: error processing adept-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-batch:
 adept-batch depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-batch depends on adept-manager; however:
  Package adept-manager is not configured yet.
dpkg: error processing adept-batch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept:
 adept depends on adept-manager; however:
  Package adept-manager is not configured yet.
 adept depends on adept-installer; however:
  Package adept-installer is not configured yet.
 adept depends on adept-updater; however:
  Package adept-updater is not configured yet.
 adept depends on adept-notifier; however:
  Package adept-notifier is not configured yet.
 adept depends on adept-batch; however:
  Package adept-batch is not configured yet.
dpkg: error processing adept (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktnef1:
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libktnef1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim1a:
 libkdepim1a depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkdepim1a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcal2b:
 libkcal2b depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 libkcal2b depends on libkdepim1a (>= 4:3.5.3); however:
  Package libkdepim1a is not configured yet.
 libkcal2b depends on libktnef1 (>= 4:3.5.3); however:
  Package libktnef1 is not configured yet.
dpkg: error processing libkcal2b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of akregator:
 akregator depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 akregator depends on libkdepim1a (>= 4:3.5.3); however:
  Package libkdepim1a is not configured yet.
dpkg: error processing akregator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq4:
 libkonq4 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkonq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdesktop:
 kdesktop depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kdesktop depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
 kdesktop depends on kdebase-bin (= 4:3.5.6-0ubuntu20.1); however:
  Package kdebase-bin is not configured yet.
dpkg: error processing kdesktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-kio-plugins:
 kdebase-kio-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kdebase-kio-plugins depends on kdesktop; however:
  Package kdesktop is not configured yet.
dpkg: error processing kdebase-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on kdebase-kio-plugins; however:
  Package kdebase-kio-plugins is not configured yet.
 amarok depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok-xine:
 amarok-xine depends on amarok (= 2:1.4.5-0ubuntu7); however:
  Package amarok is not configured yet.
 amarok-xine depends on amarok; however:
  Package amarok is not configured yet.
 amarok-xine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing amarok-xine (--configure):
 dependency problems - leaving unconfigured
Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ]
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-qt:
 apport-qt depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ark:
 ark depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing ark (--configure):
 dependency problems - leaving unconfigured
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libkexiv2-0:
 libkexiv2-0 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkexiv2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkipi0:
 libkipi0 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkipi0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of digikam:
 digikam depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 digikam depends on libkexiv2-0; however:
  Package libkexiv2-0 is not configured yet.
 digikam depends on libkipi0; however:
  Package libkipi0 is not configured yet.
 digikam depends on kdebase-kio-plugins; however:
  Package kdebase-kio-plugins is not configured yet.
dpkg: error processing digikam (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-app-install (0.3.31) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gwenview:
 gwenview depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 gwenview depends on libkipi0; however:
  Package libkipi0 is not configured yet.
dpkg: error processing gwenview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b2:
 libk3b2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libk3b2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 k3b depends on libk3b2 (>= 1.0); however:
  Package libk3b2 is not configured yet.
 k3b depends on kdelibs-data (>= 4:3.1.4-2); however:
  Package kdelibs-data is not configured yet.
 k3b depends on kdebase-bin; however:
  Package kdebase-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkleopatra1:
 libkleopatra1 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkleopatra1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaddressbook:
 kaddressbook depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kaddressbook depends on libkcal2b (>= 4:3.5.3); however:
  Package libkcal2b is not configured yet.
 kaddressbook depends on libkdepim1a (>= 4:3.5.3); however:
  Package libkdepim1a is not configured yet.
 kaddressbook depends on libkleopatra1 (>= 4:3.5.3); however:
  Package libkleopatra1 is not configured yet.
 kaddressbook depends on libktnef1 (>= 4:3.5.3); however:
  Package libktnef1 is not configured yet.
dpkg: error processing kaddressbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-xine:
 kaffeine-xine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kaffeine-xine depends on kaffeine; however:
  Package kaffeine is not configured yet.
dpkg: error processing kaffeine-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kamera:
 kamera depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kamera (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of karm:
 karm depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 karm depends on libkcal2b (>= 4:3.5.3); however:
  Package libkcal2b is not configured yet.
 karm depends on libkdepim1a (>= 4:3.5.3); however:
  Package libkdepim1a is not configured yet.
 karm depends on libktnef1 (>= 4:3.5.3); however:
  Package libktnef1 is not configured yet.
dpkg: error processing karm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of katapult:
 katapult depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing katapult (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kbstate:
 kbstate depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kbstate (--configure):
 dependency problems - leaving unconfigured
Setting up kdebase-data (3.5.6-0ubuntu20.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdebase-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kicker:
 kicker depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kicker depends on libkonq4 (>= 4:3.5.5-1); however:
  Package libkonq4 is not configured yet.
 kicker depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kicker depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kcontrol depends on kicker (>= 4:3.5.5-1); however:
  Package kicker is not configured yet.
 kcontrol depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kcontrol depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcron:
 kcron depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kcron (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde3:
 python-kde3 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 python-kde3 depends on konsole; however:
  Package konsole is not configured yet.
dpkg: error processing python-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-guidance:
 kde-guidance depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kde-guidance depends on python-kde3; however:
  Package python-kde3 is not configured yet.
dpkg: error processing kde-guidance (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 gnome-applets-data
 kdelibs-data
 kdelibs4c2a
 konsole
 adept-common
 adept-manager
 adept-installer
 adept-updater
 adept-notifier
 adept-batch
 adept
 libktnef1
 libkdepim1a
 libkcal2b
 akregator
 libkonq4
 kdebase-bin
 kdesktop
 kdebase-kio-plugins
 amarok
 amarok-xine
 apport
 apport-gtk
 apport-qt
 ark
 capplets-data
 libkexiv2-0
 libkipi0
 digikam
 gnome-app-install
 gnome-control-center
 gnome-panel-data
 gnome-panel
 gwenview
 libk3b2
 k3b
 libkleopatra1
 kaddressbook
 kaffeine
 kaffeine-xine
 kamera
 karm
 katapult
 kate
 kbstate
 kdebase-data
 kicker
 kcontrol
 kcron
 python-kde3
 kde-guidance
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@james-linux-box:~$    
```

---

### Post by overdrank on 2007-07-08
Hi a similar thread was started today maybe it will help
[http://ubuntuforums.org/showthread.php?t=496003](http://ubuntuforums.org/showthread.php?t=496003)

---

