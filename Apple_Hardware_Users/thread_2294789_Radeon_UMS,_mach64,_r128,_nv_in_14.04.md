---
title: "Radeon UMS, mach64, r128, nv in 14.04"
date: 2015-09-13
forum: Apple Hardware Users
---

### Post by rsavage on 2015-09-13
Debs with a README.txt

[http://1drv.ms/1QxzKWI](http://1drv.ms/1QxzKWI)

---

### Post by rsavage on 2015-09-13
To put some flesh on things before this thread fills up with waffle and nonsense......

The libgl1-mesa-dri_7.11.2-0blossom1_powerpc.deb package contains legacy mesa DRI1 drivers for radeon and r128 cards, non gallium versions of r200, r300 and r600.  It does NOT contain any nouveau drivers.  This package gives you 3D acceleration.

The xserver-xorg-core_1.11.4-1blossom1_powerpc.deb package is essentially the same as that used in 12.04, with a few patches removed and added to make it compile and work.  It gives XAA and EXA acceleration.

The xserver-xorg-video-ati_6.14.6-0blossom2_powerpc.deb and xserver-xorg-video-radeon_6.14.6-0blossom2_powerpc.deb packages are built from the latest ums branch.

The xserver-xorg-video-mach64_6.9.5-1_powerpc.deb and xserver-xorg-video-r128_6.10.0-1~blossom1_powerpc.deb are built from the latest git snapshots.

The xserver-xorg-video-nv_2.1.17-3ubuntu7_powerpc.deb is the version from natty, which still used to work in precise when re-compiled.  Hopefully it still does now, but due to newer cairo it maybe not as fast as before?

I have not provided a nouveau package, but you maybe able to just install the 12.04 version which you can find on launchpad.

---

### Post by rsavage on 2015-09-14
Nobody?

More debs for you.....

Patched webkit [http://1drv.ms/1O8KyMK](http://1drv.ms/1O8KyMK)

Compiz 0.8.6 [http://1drv.ms/1J5KbKZ](http://1drv.ms/1J5KbKZ) can be used as a drop in replacement for kwin or Marco (if you installed UM before the ISO was removed).

Patched r300 mesa debs [http://1drv.ms/1J5K1mN](http://1drv.ms/1J5K1mN) if you want to use KMS.

---

### Post by abtabt on 2015-09-14
hi rsavage

i am intrested but have no account 

do i need windows for download ???

---

### Post by rsavage on 2015-09-14
No you don't need an account, but onedrive doesn't like the PowerPC version of firefox.  A simple way to fool it is to go to about:config, right click, create a new string called  'general.useragent.override', leave the value blank, reload the page and you should be in.

---

### Post by abtabt on 2015-09-15
rsavage
 its working thanks

---

### Post by abtabt on 2015-09-15
rsavage

i download
Patched webkit

i did
sudo dpkg -i *.deb
and get some error 
Fel uppstod vid hantering:
 gir1.2-webkit-1.0
 libwebkit2gtk-3.0-25:powerpc
 gir1.2-webkit2-3.0
tba@tba-desktop:~/Hämtningar/webkit$ 

then i change to dev folder and 
run 
sudo dpkg -i *.deb

and get some errors 

is this the right way to do or need  i a lesson in patching ??

now i can use Quppzilla and mindori so the patch work, maby somthing else get broken 

but its great i can use mindori 

have nice day

---

### Post by rsavage on 2015-09-15
No it won't fix quipzilla, since that uses qtwebkit.  I did patch that too, but it just crashed when you entered text.  Not very useful.  You can get a working quipzilla if you compile the very latest version of quipzilla since that builds on a different version of qtwebkit that is already patched.

You shouldn't need to install the dev packages.

---

### Post by rsavage on 2015-09-15
Latest midori [http://1drv.ms/1Lfp3Id](http://1drv.ms/1Lfp3Id)

---

### Post by rican-linux on 2015-09-15
@rsavage

Thanks for supplying these.

---

### Post by Saml01 on 2015-09-19
Is downgrading to an earlier xorg that supports NV better than running noveau with the MSI interrupts disabled?

I didnt know what midori was until this thread. It didnt work until after I installed the patched webkit. Works now. Cool.

---

### Post by rsavage on 2015-09-19
Probably not.  I think it might be slower in 14.04, and I possibly missed off a patch in the xserver-xorg package so you might get rendering errors with nv.  Dunno really, I don't have a nvidia card.

EDIT: patch already there [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1010794](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1010794)

---

### Post by rsavage on 2015-09-21
There's a newer version of Midori now which I missed.  I can share that if people want it, but I've been experimenting with building it with webkit2.  For those that don't know, webkit1 isn't really getting security updates anymore and everything is going to have to switch to webkit2.  The next release of Midori will probably be webkit2 only.

The problem is, webkit2 seems to be severely broken on powerpc.  Has anybody got it working in any version of *buntu/debian/etc?  Epiphany-browser uses webkit2, and that's the best thing to try.  This forum works on it, but BBC news and YouTube just show a mess - a bizarre page of Chinese characters, a blank page, or just a mess of graphics corruption.  Thoughts?

---

### Post by xeno74 on 2015-09-21
> **rsavage said:**
> There's a newer version of Midori now which I missed.  I can share that if people want it, but I've been experimenting with building it with webkit2.  For those that don't know, webkit1 isn't really getting security updates anymore and everything is going to have to switch to webkit2.  The next release of Midori will probably be webkit2 only.

The problem is, webkit2 seems to be severely broken on powerpc.  Has anybody got it working in any version of *buntu/debian/etc?  Epiphany-browser uses webkit2, and that's the best thing to try.  This forum works on it, but BBC news and YouTube just show a mess - a bizarre page of Chinese characters, a blank page, or just a mess of graphics corruption.  Thoughts?

I tried it out in May:

[[IMG]https://lh3.googleusercontent.com/-NhQ0TxnZzkY/VRP5KFhlykI/AAAAAAAAAfo/XjjBPuyWW08/w426-h320/ubuntu_MATE_15.04_PowerPC_kernel_4.0-rc5_Epiphany_WebKit_browser.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/4jfek7B58XA")

---

### Post by rsavage on 2015-09-21
Yeah, but did it work on all sites e.g. YouTube?

---

### Post by rsavage on 2015-09-21
Midori (webkit1 and webkit2 versions) [http://1drv.ms/1iJmsLK](http://1drv.ms/1iJmsLK)

Smplayer [http://1drv.ms/1LIO9ek](http://1drv.ms/1LIO9ek)

---

### Post by lauri-ojansivu on 2015-09-22
Hi,
I tried upgrading 12.04 to 14.04 on my PowerBook G4, and using your NVidia driver packages, but I didn't get it working. Do you have changes to sources somewhere like GitHub?

I did not take backups before upgrading, so I needed to figure out how to get 12.04 working again with nv driver.

First I downloaded Ubuntu PowerPC alternative install, installed in text mode, setup static IP because my DHCP didn't work. I did setup partitions as they were from previous install, dual boot with Mac OS X.

Then I started in boot menu l = linux, and then "Linux single nomodeset" to get to console.

I installed all updates.

To get ssh access for doing copy-paste commands easier, I did install ssh and start it (it's not started automatically on single user mode):

```

sudo apt-get install ssh
sudo service ssh start

```

Compile instructions for nv module are here:
[http://ubuntuforums.org/showthread.php?t=2203756&p=12922410#post12922410](http://ubuntuforums.org/showthread.php?t=2203756&p=12922410#post12922410)

I think source is originally from here:
[http://cgit.freedesktop.org/xorg/driver/xf86-video-nv/](http://cgit.freedesktop.org/xorg/driver/xf86-video-nv/)

Anyway, I have previously downloaded source files as working backup here, with compiled deb package:
[https://sites.google.com/site/lauriojansivu/nv.zip](https://sites.google.com/site/lauriojansivu/nv.zip)

And here is just the compiled deb package, that works as of today:
[https://sites.google.com/site/lauriojansivu/xserver-xorg-video-nv_2.1.20-3_powerpc.deb](https://sites.google.com/site/lauriojansivu/xserver-xorg-video-nv_2.1.20-3_powerpc.deb)

After installing deb package, add xorg settings to /etc/X11/xorg.conf, I got this info from here:
[http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

```
sudo nano /etc/X11/xorg.conf
```

There add this text:

```
[COLOR=#000000]Section "Device"[/COLOR]
[COLOR=#000000]Identifier "Configured Video Device"[/COLOR]
[COLOR=#000000]Driver "nv"[/COLOR]
[COLOR=#000000]EndSection[/COLOR]

[COLOR=#000000]Section "Monitor"[/COLOR]
[COLOR=#000000]Identifier "Configured Monitor"[/COLOR]
[COLOR=#000000]EndSection[/COLOR]

[COLOR=#000000]Section "Screen"[/COLOR]
[COLOR=#000000]Identifier "Screen0"[/COLOR]
[COLOR=#000000]Device "nVidia"[/COLOR]
[COLOR=#000000]Monitor "Monitor"[/COLOR]
[COLOR=#000000]DefaultDepth 16[/COLOR]
[COLOR=#000000]SubSection "Display"[/COLOR]
[COLOR=#000000]Viewport 0 0[/COLOR]
[COLOR=#000000]Depth 16[/COLOR]
[COLOR=#000000]Modes "1024x768"[/COLOR]
[COLOR=#000000]EndSubSection[/COLOR]
[COLOR=#000000]EndSection[/COLOR]

```

Then blacklist nouveau driver:

```
sudo nano /etc/modprobe.d/blacklist-framebuffer.conf
```

And add there at beginning of list add:

```
blacklist nouveau
```

And save.
To install WLAN drivers:

```
sudo apt-get install firmware-b43legacy-installer
```

Then reboot:

```
sudo reboot
```

And boot with l = Linux, and Enter (no boot options)

BTW, if you get black screen when booting in graphical mode, it means that login screen may be visible, so just write your: username TAB password ENTER  to continue booting. But anyway, this is not necessary when NV driver is installed correctly.

Next time I will backup before trying newer Ubuntu version. :D

---

### Post by rsavage on 2015-09-22
That's a shame.  Thanks for trying.

Did you get any logs off the failed 14.04 install?

If you want to give it another go without reinstalling everything (and you have the hard drive space), then use the wubi instructions [https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F](https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F)

---

### Post by rsavage on 2015-09-22
I should add about the wubi instructions, you could skip the creating of the root and swap disks.  You could test it all from just the installation ISO.  Boot into text mode/single user with nomodeset, 

cd /isodevice/home/insert-your-username/Downloads/etc

install the debs etc and start lightdm

I'm sure upgrading from 12.04 to 14.04 could of caused you problems, particularly if you are using Ubuntu and not lubuntu.  The upgrade paths have not been tested well.

---

### Post by lauri-ojansivu on 2015-09-22
Hi,
yes I'm very interested in trying again. It was originally Lubuntu 12.04 install where I installed Ubuntu desktop, and tried graphical upgrade. After upgrade screen flashed, it could not startx properly after 14.04 text. I did not save any logs. Ubuntu 12.04 only has Firefox 39, and I'd like to compile software that requires libs from 14.04. I will try again later this week, or weekend. What logs would be most useful? Do I need to install all packages, or only xorg core, nv, webkit etc?

---

### Post by rsavage on 2015-09-25
Install all the packages in the first post (but not the ones in the extras directory).  Remove the packages as suggested in the README.

If it doesn't work, then xorg.0.log please.

---

### Post by lauri-ojansivu on 2015-09-26
Hi,
I think previously I installed too many packages (extra etc) so it did not work then.

Now I did backup, start from Lubuntu 14.04 live DVD, and installed packages etc as was in README. After starting LightDM colors seem to be correct, so now I'll start installing to harddisk.

---

### Post by lauri-ojansivu on 2015-09-26
After install, I did need to install those driver packages again.
To get Lubuntu booting to desktop, I did change at /etc/yaboot.conf text "single nomodeset" to "nomodeset" and then run "sudo ybin".
I added Finnish keyboard from Lubuntu settings menu.
Now I'm installing updates etc testing it.

Thanks :)

---

### Post by lauri-ojansivu on 2015-09-26
Hi,
I'm compiling [http://www.secretchronicles.de](http://www.secretchronicles.de) game that is at [https://github.com/Secretchronicles/TSC](https://github.com/Secretchronicles/TSC) , and when I'm installing dependencies for building, it says:

These packages have unmet dependencies:
 libxfixes3 : Breaks: xserver-xorg-core (< 2:1.14)
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
koti@PowerBookG4:~$ dpkg -l | grep xserver-xorg-core
hi  xserver-xorg-core                             2:1.11.4-1blossom1                   powerpc      Xorg X server - core server

Could you provide newer package, and build instructions from source?

---

### Post by rsavage on 2015-09-26
I'm glad it is now working for you now.  Could you tell me if you needed an xorg.conf?  I think it should work without one as long as you are using nomodeset.  I may at some point create an ISO with these packages and that would be useful info.

> **lauri-ojansivu said:**
> 
Could you provide newer package, and build instructions from source?

In a word - no.

It is probably not necessary.  All you have to do is install the dev package from the extras directory e.g. sudo dpkg -i libfixes-devblahblah.deb

If you want to build the packages I've made from source then you'll have to read the changelog for the package and hunt down the commits.  I probably should have given the xserver-xorg package a falsely high version number to avoid some of these problems with package dependencies.

That game seems to use OpenGL, so you might be struggling with nv.  The software rasteriser in the mesa dri package I've given is slow.  If I remember correctly the default mesa dri package in 14.04 uses llvm pipe which is a bit quicker but still slow.  You'll have dependency problems with that though so a bit of manual tinkering will be necessary.

---

### Post by lauri-ojansivu on 2015-09-26
Hi,
I installed dev package with:
sudo dpkg -i --ignore-depends=x11proto-fixes-dev libxfixes-dev_5.0.1-1ubuntu1.1~blossom1_powerpc.deb

Then when I try to install build dependencies:
sudo apt-get install ruby-full rake gperf pkg-config bison libglew-dev   freeglut3-dev gettext libpng12-dev libsdl-ttf2.0-dev   libsdl-mixer1.2-dev libsdl-image1.2-dev libpcre3-dev libxml++2.6-dev   libfreetype6-dev libdevil-dev libboost1.55-all-dev cmake

It then still complains about missing x11proto-fixes-dev package. Do you have that package?
I'll think how else I could get past this error.

---

### Post by lauri-ojansivu on 2015-09-26
Nevermind, I needed to install "sudo apt-get install x11proto-fixes-dev x11proto-xext-dev" first. Continuing setup....

---

### Post by lauri-ojansivu on 2015-09-26
Hi,
I did not need any xorg.conf , only nomodeset option at yaboot.

---

### Post by lauri-ojansivu on 2015-09-26
On this PowerBook G4:

To get sound working, I used [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) page generic fix deb package at:
[http://ubuntuforums.org/showthread.php?t=2209340&page=10&p=13328573#post13328573](http://ubuntuforums.org/showthread.php?t=2209340&page=10&p=13328573#post13328573)

To get wlan working, I did install:
sudo apt-get install firmware-b43legacy-installer

---

### Post by lauri-ojansivu on 2015-09-26
I wanted to install "sudo apt-get install libsdl2-dev libsdl2-image-dev"

And it complained about breaking "xserver-xorg-core (< 2:1.14)"

So according to webpage [http://manpages.ubuntu.com/manpages/maverick/man1/deb-reversion.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/deb-reversion.1.html)
I install devscripts to change package version:
sudo apt-get install devscripts

Then I did:
sudo deb-reversion -v 2:1.14blossom1 xserver-xorg-core_1.11.4-1blossom1_powerpc.deb
sudo apt-mark unhold xserver-xorg-core
sudo dpkg -i xserver-xorg-core_1.14blossom1_powerpc.deb
sudo apt-mark hold xserver-xorg-core

And then I could continue installing libsdl2 :) I also reinstalled libxi6 back to your package, because it got updated to ubuntu version during other updates.

---

### Post by lauri-ojansivu on 2015-09-27
I installed TSC, and it says:
Warning: Video Bpp is not supported but 16 is
Error: Screen mode creation failed
Reason: Couldn't find matching GLX visual

I also installed SuperTux.
It fails on GLX, but swithes itself to use SDL backend instead, and starts the game, although it works very slowly.
And sound is distorted, so I needed to mute it.

With Firefox on Youtube video and sound does work on HTML5 video.

After I installed your mesa-debs, and tried to do "apt-get dist-upgrade", it tries to "fix" broken debs by removing too many packages (I translated messages to English) :

$ sudo apt-get dist-upgrade
[sudo] password for koti: 
Reading package lists... Ready
Creating dependencies tree
Reading status info... Valmis        
You may want to do "apt-get -f install" to fix these.
These packages have unmet dependencies:
 libegl1-mesa-dev : Dependencies: libegl1-mesa (= 10.1.3-0ubuntu0.4) or
                                  libegl1-mesa-lts-utopic but is not installed or
                                  libegl1-mesa-lts-vivid but is not installed
                    Dependencies: libegl1-mesa-drivers (= 10.1.3-0ubuntu0.4) or
                                  libegl1-mesa-drivers-lts-utopic but is not installed or
                                  libwayland-egl1-mesa-lts-vivid but is not installed
 libgl1-mesa-dev : Dependencies: libgl1-mesa-glx (= 10.1.3-0ubuntu0.4) or
                                 libgl1-mesa-glx-lts-utopic but is not installed or
                                 libgl1-mesa-glx-lts-vivid but is not installed
 libgles2-mesa : Dependencies: libglapi-mesa (= 10.1.3-0ubuntu0.4)
E: Unmet dependencies. Try to use  -f.
$ sudo apt-get -f install
Reading package lists... Ready
Creating dependencies tree
Reading status info... Ready
Fixing dependencies... Ready
Following packages are originally installed automatically, and are not needed anymore:
  fonts-sil-gentium fonts-sil-gentium-basic gir1.2-gtk-2.0 ipxe-qemu libaio1
  liballegro4.4 liballegro4.4-plugin-alsa libasound2-dev libavahi-client-dev
  libavahi-common-dev libbrlapi0.6 libcaca-dev libcdr-0.0-0 libdbus-1-dev
  libdrm-dev libegl1-mesa-dev libfdt1 libflac-dev libfs6 libgl1-mesa-dev
  libgles2-mesa-dev libice-dev libjbig-dev libjpeg-dev libjpeg-turbo8-dev
  libjpeg8-dev liblcms1 liblcms1-dev liblzma-dev libmad0-dev libmikmod2
  libmikmod2-dev libmng2 libmspub-0.0-0 liborcus-0.6-0 libpulse-dev librados2
  librbd1 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libslang2-dev
  libsm-dev libtiff5-dev libtiffxx5 libts-dev libudev-dev libusbredirparser1
  libvisio-0.0-0 libwayland-dev libwebp-dev libwebpdemux1 libwebpmux1
  libx11-xcb-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev
  libxcb-present-dev libxcb-randr0 libxcb-randr0-dev libxcb-render0-dev
  libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcursor-dev
  libxdamage-dev libxext-dev libxi-dev libxinerama-dev libxkbcommon-dev
  libxrandr-dev libxrender-dev libxshmfence-dev libxss-dev libxt-dev libxv-dev
  libxxf86vm-dev mesa-common-dev qemu-keymaps qemu-system-arm
  qemu-system-common qemu-system-mips qemu-system-ppc qemu-system-sparc
  qemu-system-x86 qemu-utils seabios x11-apps x11-session-utils x11-xfs-utils
  x11proto-damage-dev x11proto-dri2-dev x11proto-gl-dev x11proto-randr-dev
  x11proto-render-dev x11proto-scrnsaver-dev x11proto-video-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev xinit xinput
Use 'apt-get autoremove' to remove them.
Following extra packages are marked to install:
  docbook-xml docbook-xsl esound-common gstreamer0.10-pulseaudio icoutils
  kate-data katepart kde-baseapps-bin kde-baseapps-data kde-runtime
  kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libasound2-plugins libattica0.4 libaudio2
  libaudiofile1 libbaloocore4 libbaloofiles4 libbalooxapian4 libcanberra-pulse
  libdbusmenu-qt2 libdlrestrictions1 libegl1-mesa-drivers-lts-utopic
  libegl1-mesa-lts-utopic libepub0 libesd0 libexiv2-12 libfftw3-single3
  libgbm1-lts-utopic libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles2-mesa-lts-utopic libkactivities-bin
  libkactivities-models1 libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libkubuntu0 libkxmlrpcclient4 libmysqlclient18 libnepomuk4
  libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4
  libntrack-qt4-1 libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1
  libpoppler-qt4-4 libpulsedsp libqapt2 libqapt2-runtime libqca2 libqjson0
  libqmobipocket1 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtdbus4 libqtgui4 libqtwebkit4 libsolid4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0
  libwayland-egl1-mesa-lts-utopic libxml2-utils libxvmc1 libzip2 mplayer
  mysql-common nepomuk-core-data nepomuk-core-runtime ntrack-module-libnl-0
  odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common phonon-backend-gstreamer1.0
  plasma-scriptengine-javascript pulseaudio pulseaudio-module-x11
  pulseaudio-utils qapt-batch qdbus qtchooser qtcore4-l10n rtkit sgml-data
  shared-desktop-ontologies soprano-daemon ttf-dejavu-core virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  docbook docbook-dsssl docbook-defguide dbtoepub docbook-xsl-doc-html
  docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc docbook-xsl-saxon
  fop libsaxon-java libxalan2-java libxslthl-java xalan
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin finger
  nas pulseaudio-esound-compat exiv2 libfftw3-bin libfftw3-dev hspell
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev libicu48 qt4-qtconfig media-player-info mplayer-doc netselect
  fping phonon-backend-vlc phonon4qt5-backend-gstreamer pavumeter paman
  pavucontrol paprefs pulseaudio-module-raop avahi-daemon qt4-default
  qt5-default perlsgml w3-recs opensp
Following packages WILL BE REMOVED:
  abiword apturl audacious audacious-plugins freeglut3 freeglut3-dev
  gecko-mediaplayer gir1.2-webkit-1.0 gir1.2-webkit2-3.0 gnome-mplayer
  gstreamer1.0-plugins-bad libabiword-3.0 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libclutter-1.0-0 libclutter-gtk-1.0-0
  libcogl-pango15 libcogl15 libdevil-dev libdevil1c2 libegl1-mesa
  libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-glx libglamor0
  libglapi-mesa libgles2-mesa libglew-dev libglew1.10 libglu1-mesa
  libglu1-mesa-dev libgtkglext1 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libreoffice
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core
  libreoffice-base-drivers libreoffice-calc libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-help-fi libreoffice-impress
  libreoffice-math libreoffice-pdfimport libreoffice-report-builder-bin
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-voikko
  libreoffice-writer libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
  libsdl1.2-dev libsdl2-dev libsdl2-image-dev libwayland-egl1-mesa
  libwebkit2gtk-3.0-25 libwebkitgtk-1.0-0 lubuntu-core lubuntu-desktop midori
  mplayer2 python3-uno qemu qemu-system qemu-system-misc xorg xserver-xorg
  zenity
Following NEW packages will be installed:
  docbook-xml docbook-xsl esound-common gstreamer0.10-pulseaudio icoutils
  kate-data katepart kde-baseapps-bin kde-baseapps-data kde-runtime
  kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libasound2-plugins libattica0.4 libaudio2
  libaudiofile1 libbaloocore4 libbaloofiles4 libbalooxapian4 libcanberra-pulse
  libdbusmenu-qt2 libdlrestrictions1 libegl1-mesa-drivers-lts-utopic
  libegl1-mesa-lts-utopic libepub0 libesd0 libexiv2-12 libfftw3-single3
  libgbm1-lts-utopic libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles2-mesa-lts-utopic libkactivities-bin
  libkactivities-models1 libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libkubuntu0 libkxmlrpcclient4 libmysqlclient18 libnepomuk4
  libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4
  libntrack-qt4-1 libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1
  libpoppler-qt4-4 libpulsedsp libqapt2 libqapt2-runtime libqca2 libqjson0
  libqmobipocket1 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtdbus4 libqtgui4 libqtwebkit4 libsolid4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0
  libwayland-egl1-mesa-lts-utopic libxml2-utils libxvmc1 libzip2 mplayer
  mysql-common nepomuk-core-data nepomuk-core-runtime ntrack-module-libnl-0
  odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common phonon-backend-gstreamer1.0
  plasma-scriptengine-javascript pulseaudio pulseaudio-module-x11
  pulseaudio-utils qapt-batch qdbus qtchooser qtcore4-l10n rtkit sgml-data
  shared-desktop-ontologies soprano-daemon ttf-dejavu-core virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 updated, 139 new installs, 82 to remove and 9 not updated.
To be downloaded archives 95,1 Mb.
After this 146 Mb space fill be freed.
Do you want to continue? [Y/n] ?

So I'm not sure how to fix that, so it would not remove so many packages.

---

### Post by rsavage on 2015-09-28
Thanks for the feedback.  This is a quick answer....

> **lauri-ojansivu said:**
> I installed TSC, and it says:
Warning: Video Bpp is not supported but 16 is
Error: Screen mode creation failed
Reason: Couldn't find matching GLX visual

Until I patch things, please install the mesa dri package from precise (12.04), this should hopefully give you a working software rasteriser. If you want glx you would be better off trying to get some version of nouveau working.

> 
With Firefox on Youtube video and sound does work on HTML5 video.

Out of curiosity, does it play smoothly, and what is your processor speed?

> 
After I installed your mesa-debs, and tried to do "apt-get dist-upgrade", it tries to "fix" broken debs by removing too many packages (I translated messages to English) :


I don't understand what you've installed.

---

### Post by rsavage on 2015-09-28
> **lauri-ojansivu said:**
> I installed TSC, and it says:
Warning: Video Bpp is not supported but 16 is
Error: Screen mode creation failed
Reason: Couldn't find matching GLX visual


I force installed the trusty version of mesa dri and the software rasteriser works for me with glxgears/aiglx. 

I've no idea what tsc is, but have you tried a 16 bit colour depth like it says?

---

### Post by lauri-ojansivu on 2015-09-29
Hi,
I did some dist-upgrades and updates, and now:

- I did get TSC game running in window, it works slowly, but sound is at normal speed playing ogg file music and effects. You can see screenshots of game at [http://www.secretchronicles.de](http://www.secretchronicles.de)

- currently supertux game complains about missing libSDL2-2.0.0.so , I have installed that but it still complains. SuperTux game screenshots are at [https://supertux.github.io/](https://supertux.github.io/)

- glxgears works, and here's also other hardware and software info:
```
$ glxgears
209 frames in 5.0 seconds = 41.747 FPS
208 frames frames in 5.0 seconds = 41.540 FPS

$ cat /proc/cpuinfo
processor    : 0
cpu        : 7455, altivec supported
clock        : 867.000000MHz
revision    : 3.3 (pvr 8001 0303)
bogomips    : 66.56
total bogomips    : 66.56
timebase    : 33280357
platform    : PowerMac
model        : PowerBook6,1
machine        : PowerBook6,1
motherboard    : PowerBook6,1 MacRISC3 Power Macintosh
detected as    : 287 (PowerBook G4 12")
pmac flags    : 0000001a
L2 cache    : 256K unified
pmac-generation    : NewWorld
Memory        : 640 MB 

$ lspci
0000:00:0b.0 Host bridge: Apple Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: NVIDIA Corporation NV17M [GeForce4 440 Go 64M] (rev a3)
0001:10:0b.0 Host bridge: Apple Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0002:20:0b.0 Host bridge: Apple Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Unassigned class [ff00]: Apple Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

$ dpkg -l | grep blossom
ii  gir1.2-javascriptcoregtk-1.0             2.4.8-1ubuntu2~blossom14.04.3              powerpc      JavaScript engine library from WebKitGTK+ - GObject introspection data
ii  gir1.2-javascriptcoregtk-3.0             2.4.8-1ubuntu2~blossom14.04.3              powerpc      JavaScript engine library from WebKitGTK+ - GObject introspection data
ii  gir1.2-webkit-1.0                        2.4.8-1ubuntu2~blossom14.04.3              powerpc      Web content engine library for GTK+ - GObject introspection data
ii  gir1.2-webkit-3.0                        2.4.8-1ubuntu2~blossom14.04.3              powerpc      Web content engine library for GTK+ - GObject introspection data
ii  gir1.2-webkit2-3.0                       2.4.8-1ubuntu2~blossom14.04.3              powerpc      WebKit2 API layer for WebKitGTK+ - GObject introspection data
ii  libjavascriptcoregtk-1.0-0:powerpc       2.4.8-1ubuntu2~blossom14.04.3              powerpc      JavaScript engine library from WebKitGTK+
ii  libjavascriptcoregtk-3.0-0:powerpc       2.4.8-1ubuntu2~blossom14.04.3              powerpc      JavaScript engine library from WebKitGTK+
ii  libjavascriptcoregtk-3.0-bin             2.4.8-1ubuntu2~blossom14.04.3              powerpc      JavaScript engine library from WebKitGTK+ - command-line interpreter
ii  libwebkit2gtk-3.0-25:powerpc             2.4.8-1ubuntu2~blossom14.04.3              powerpc      WebKit2 API layer for WebKitGTK+
ii  libwebkitgtk-1.0-0:powerpc               2.4.8-1ubuntu2~blossom14.04.3              powerpc      Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                  2.4.8-1ubuntu2~blossom14.04.3              all          Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0:powerpc               2.4.8-1ubuntu2~blossom14.04.3              powerpc      Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                  2.4.8-1ubuntu2~blossom14.04.3              all          Web content engine library for GTK+ - data files
ii  libxfixes3:powerpc                       1:5.0.1-1ubuntu1.1~blossom1                powerpc      X11 miscellaneous 'fixes' extension library
hU  xserver-xorg-core                        2:1.11.4-1blossom1                         powerpc      Xorg X server - core server
iU  xserver-xorg-input-evdev                 1:2.8.2-1ubuntu2~blossom1                  powerpc      X.Org X server -- evdev input driver

$ dpkg -l | grep video-nv
hU  xserver-xorg-video-nv                    1:2.1.17-3ubuntu7                          powerpc      X.Org X server -- NV display driver

$ uname -a
Linux PowerBookG4 3.13.0-65-powerpc-smp #105-Ubuntu SMP Mon Sep 21 18:55:07 UTC 2015 ppc ppc ppc GNU/Linux

$ dpkg -l | grep mesa
ii  libegl1-mesa:powerpc                     10.1.3-0ubuntu0.4                          powerpc      free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:powerpc             10.1.3-0ubuntu0.4                          powerpc      free implementation of the EGL API -- hardware drivers
rc  libegl1-mesa-lts-utopic:powerpc          10.3.2-0ubuntu1~trusty2                    powerpc      free implementation of the EGL API -- runtime
ii  libgl1-mesa-dev                          10.1.3-0ubuntu0.4                          powerpc      free implementation of the OpenGL API -- GLX development files
ii  libgl1-mesa-dri:powerpc                  10.1.3-0ubuntu0.4                          powerpc      free implementation of the OpenGL API -- DRI modules
rc  libgl1-mesa-dri-lts-utopic:powerpc       10.3.2-0ubuntu1~trusty2                    powerpc      free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:powerpc                  10.1.3-0ubuntu0.4                          powerpc      free implementation of the OpenGL API -- GLX runtime
rc  libgl1-mesa-glx-lts-utopic:powerpc       10.3.2-0ubuntu1~trusty2                    powerpc      free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:powerpc                    10.1.3-0ubuntu0.4                          powerpc      free implementation of the GL API -- shared library
rc  libglapi-mesa-lts-utopic:powerpc         10.3.2-0ubuntu1~trusty2                    powerpc      free implementation of the GL API -- shared library
rc  libgles2-mesa:powerpc                    10.1.3-0ubuntu0.4                          powerpc      free implementation of the OpenGL|ES 2.x API -- runtime
rc  libgles2-mesa-lts-utopic:powerpc         10.3.2-0ubuntu1~trusty2                    powerpc      free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:powerpc                     9.0.0-2                                    powerpc      Mesa OpenGL utility library (GLU)
ii  libglu1-mesa-dev                         9.0.0-2                                    powerpc      Mesa OpenGL utility library -- development files
ii  libopenvg1-mesa:powerpc                  10.1.3-0ubuntu0.4                          powerpc      free implementation of the OpenVG API -- runtime
ii  libwayland-egl1-mesa:powerpc             10.1.3-0ubuntu0.4                          powerpc      implementation of the Wayland EGL platform -- runtime
rc  libwayland-egl1-mesa-lts-utopic:powerpc  10.3.2-0ubuntu1~trusty2                    powerpc      implementation of the Wayland EGL platform -- runtime
ii  mesa-common-dev                          10.1.3-0ubuntu0.4                          powerpc      Developer documentation for Mesa
ii  mesa-utils                               8.1.0-2                                    powerpc      Miscellaneous Mesa GL utilities

```

To get gparted installed, I had to let it replace display packages, install gparted, reinstall display packages, and restart lightdm:
```
sudo apt-mark unhold xserver-xorg-core
sudo apt-mark unhold xserver-xorg-video-nv
sudo apt-get -f install
sudo apt-get install gparted
sudo dpkg -i libxfixes3_5.0.1-1ubuntu1.1~blossom1_powerpc.deb xserver-xorg-core_1.11.4-1blossom1_powerpc.deb xserver-xorg-input-evdev_2.8.2-1ubuntu2~blossom1_powerpc.deb xserver-xorg-video-nv_2.1.17-3ubuntu7_powerpc.deb
sudo service lightdm restart

```


I did take photo of gparted with my phone:
[IMG]https://sites.google.com/site/lauriojansivu/PowerPC_photo.jpg[/IMG]

But when I take screenshot with pinta, it displays colors wrong:
[IMG]https://sites.google.com/site/lauriojansivu/PowerPC_screenshot.jpg[/IMG]

---

### Post by lauri-ojansivu on 2015-09-29
Hi,
those mesa-debs are from your post [http://ubuntuforums.org/showthread.php?t=2294789&p=13356139#post13356139](http://ubuntuforums.org/showthread.php?t=2294789&p=13356139#post13356139)

About YouTube HTML5 video in Firefox:
- sound plays fine
- video does not play smoothly, on some videos it's little jerky, on some videos more.

When I downloaded youtube-dl script to /usr/bin/ with wget, and used it to download YouTube video:
- sound plays fine
- video plays smoothly in Gnome Mplayer in small and maximixed window
- in full screen Mplayer shows black screen

I tried installing Minitube, but it had error displaying videos.

---

### Post by rsavage on 2015-09-29
I thought those were the mesa debs you meant.  Don't use them, they're just for radeon r300 users who want to use Kms.

Midori is better for YouTube, but still not perfect.  smplayer is good because you can paste the web address in and it will play the video.

---

### Post by Roger-H on 2015-10-07
Will the drivers posted in this thread work on 12.04 also?

---

### Post by Roger-H on 2015-10-08
Just posting that the drivers do work in 12.04. I now have Ubuntu running on an 800 mhz iMac G4. Thank you!

---

### Post by xeno74 on 2015-10-22
> **rsavage said:**
> Latest midori [http://1drv.ms/1Lfp3Id](http://1drv.ms/1Lfp3Id)

Many thanks! Could you post some compiling instructions? I'd like to try to compile it.

---

### Post by rsavage on 2015-12-30
Mate 1.12 debs - [http://1drv.ms/1R9ivwT](http://1drv.ms/1R9ivwT) .  The best thing to do is a create a local repository with them.

Also, bumping this as a possible fix for imacs - [http://ubuntuforums.org/showthread.php?t=2307087&page=2&p=13412995#post13412995](http://ubuntuforums.org/showthread.php?t=2307087&page=2&p=13412995#post13412995) .  It would be good if somebody could try it.  All you have to do is install dkms and then the imac-fix deb, wait for it to automatically compile and reboot.  Easy!

---

### Post by abtabt on 2016-01-01
[ATTACH=CONFIG]266489[/ATTACH][ATTACH=CONFIG]266490[/ATTACH]> **rsavage said:**
> 
Also, bumping this as a possible fix for imacs - [http://ubuntuforums.org/showthread.php?t=2307087&page=2&p=13412995#post13412995](http://ubuntuforums.org/showthread.php?t=2307087&page=2&p=13412995#post13412995) .  It would be good if somebody could try it.  All you have to do is install dkms and then the imac-fix deb, wait for it to automatically compile and reboot.  Easy!

i try this fix get me black screen build in , boot arg "quiet splash"

then i reboot and attached extern screen show me like attach photo 
nouveau E [DRM] DDC responded but no EDID for DVI-I-1 show it on and on 
 
intern screen black ,extern sceen show the messege (extern VGA dongle)


i try boot arg with "quiet splash nomodeset"
get uggly 4/8 Depth on both screen
intern and extern show same Depth and  res  1024x768

 (video memory: 768kB) (Xorg log) i think Offb take alot off memory


i try boot arg with "quiet splash nomodeset video=offb:off"
with nvidiafb and same with downgraded xorg nv driver

Intern screen  OK desktop ,Extern screen give Uggly 4/8 Depht and i think res 640x?

 (video memory: 32768kB) (Xorg log) 

see Attachments

---

### Post by rsavage on 2016-01-01
Thanks for testing.

> **abtabt said:**
> 

i try this fix get me black screen build in , boot arg "quiet splash"

then i reboot and attached extern screen show me like attach photo 
nouveau E [DRM] DDC responded but no EDID for DVI-I-1 show it on and on 


So is that some sort of progress then?

Is this on a real install, or persistent USB/fw?  


> 
 
intern screen black ,extern sceen show the messege (extern VGA dongle)


i try boot arg with "quiet splash nomodeset"
get uggly 4/8 Depth on both screen
intern and extern show same Depth and  res  1024x768

 (video memory: 768kB) (Xorg log) i think Offb take alot off memory


i try boot arg with "quiet splash nomodeset video=offb:off"
with nvidiafb and same with downgraded xorg nv driver

Intern screen  OK desktop ,Extern screen give Uggly 4/8 Depht and i think res 640x?

 (video memory: 32768kB) (Xorg log) 

see Attachments

Regarding the imac fix, not interested in anything with nomodeset since that disables nouveau.

---

### Post by abtabt on 2016-01-01
> **rsavage said:**
> Thanks for testing.


So is that some sort of progress then?

Is this on a real install, or persistent USB/fw?  




Regarding the imac fix, not interested in anything with nomodeset since that disables nouveau.

its a real install 14.04.3 lubuntu

So is that some sort of progress then? 


no arg exept quiet splash 

no picture intern  lcd (fade off )

 picture on the extern screen VGA  
first black then see Attachments then splash blue background and then change to black background, if i switch to tty 1 then see Attachments 
nouveau E [DRM] DDC responded but no EDID for DVI-I-1 ,go on and on  extern VGA 

i  disable  DVI-I-1 and this do it ,  intern and extern screen was black

---

### Post by rsavage on 2016-01-01
That's disappointing.  Have you got the nouveau xorg package installed?

---

### Post by abtabt on 2016-01-01
> **rsavage said:**
> That's disappointing.  Have you got the nouveau xorg package installed?

i think so 

see Attachments installedno


but i have one more in the list see Attachments alla no

have miss some thing ?  two nouveau driver one installed 
do i need modeset too two off these too ???

guide me 

edit some more

---

### Post by rsavage on 2016-01-01
Everything looks okay to me.  You could always install xserver-xorg-video-all to get back any packages you uninstalled.

---

### Post by rsavage on 2016-01-01
Mate 1.12 (and 1.10) broke the compiz-mate package I included earlier in this thread.  Attached is a recompiled deb that should fix it, but has not been tested.

---

### Post by Improntant on 2016-01-17
Thank you for this! After installing your driver packages, using my custom xorg file, and appending "quiet splash radeon.modeset=0 video=radeonfb:1280x960-32@60" to my yaboot.conf file (without this append I get a black screen), my PPC eMac G4 is finally using hardware acceleration and pushing over 4000 on glxgears and can play SD quality videos decently using SMPlayer.
Though I'm still having some issues. When I press "Mark All Upgrades" in Synaptic Package Manager (I use it instead of the software updater, because software updater gives errors) I get this: [http://i.imgur.com/4fKVQ5A.jpg](http://i.imgur.com/4fKVQ5A.jpg) (to be removed {your drivers}) . Updating apps means removing those drivers  you shared, and without them I don't have hardware acceleration. I tried locking these packages (xserver-xorg-video-ati, xserver-xorg-video-nv, xserver-xorg-video-ach64, xserver-xorg-video-all, xserver-xorg-video-r128), but that didn't work. How can I get around this issue?
Second issue is that every version of midori I tried does not launch but gives the error "Segmentation fault (core dumped)", including the one you shared. Is there another good browser besides firefox I could use, because not all non-flash websites work with firefox and Opera 10.63 is useless.
There are a couple of minor things too, like the keyboard's lights (num and caps) don't light up (the keys themselves work), and alt+f2 does open the app launch window.
Thanks again!

---

### Post by luigiburdo on 2016-01-18
> [COLOR=#000000]my PPC eMac G4 is finally using hardware acceleration and pushing over 4000 on glxgears[/COLOR]
Oh mamma mia! ... i took 1400 on glx gears on Quad G5 with Radeon HD 4650 .... i will check if the append will work here too!

---

### Post by Michelle_Hindenber on 2016-02-13
Hello. I have a Powerbook latest 15" Model (5,8) with Radeon 9700 graphics. Ubuntu 12.02 works like a charme but opengl Renderer works only in "Software Rasterizer". 

How can i easy activate hardware opengl renderer? 

Best Regards

---

