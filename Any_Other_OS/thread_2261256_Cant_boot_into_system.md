---
title: "Cant boot into system"
date: 2015-01-17
forum: Any Other OS
---

### Post by william-r-stewart2013 on 2015-01-17
I recently installed a markdown editor on my Elementary OS Luna installation. Upon system restart I can no longer login to system.
I get an error [h=1][SIZE=3]"[mount: error while loading shared libraries: libudev.so.0 : no such file or directory' error while booting]("http://askubuntu.com/questions/354837/mount-error-while-loading-shared-libraries-libudev-so-0-no-such-file-or-dir")"[/SIZE][/h]Any suggestions on how to fix this?

Can it be fixed?

After this problem happened
I installed Freya alongside so I could access my Luna partition and backup my files.
If anyone can help me fix this problem it would be great. I do alot of work on this computer and it would suck to have to reinstall everything.
I have been using linux for years and have never had such a serious issue. System seems totally broken all from installing one piece of software.

---

### Post by william-r-stewart2013 on 2015-01-17
I should add I followed the suggestion on the link provided. I cant get the package to install.

---

### Post by Bashing-om on 2015-01-17
william-r-stewart; Hi !

> **william-r-stewart2013 said:**
> I should add I followed the suggestion on the link provided. I cant get the package to install.

We would need some additional info to work from here.


What 'link' did you follow specifically ?
What kernel are you running ? we try and find out if that 3rd party software that you attempted to install is compatible with the release you are running ?

I would imagine that from a full CHange Root one can undo the install of that 3rd party software - once we know how it was installed .

With time. effort and a LiveDVD
[INDENT][INDENT]it's all fixable
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
Hi,

I followed this link
[http://askubuntu.com/questions/354837/mount-error-while-loading-shared-libraries-libudev-so-0-no-such-file-or-dir](http://askubuntu.com/questions/354837/mount-error-while-loading-shared-libraries-libudev-so-0-no-such-file-or-dir)
I couldnt get the package to install. might be a user error on my end. 

Im running kernel 3.2.0-72-generic
I hope its ok to say the software. It was Hoorapad.

---

### Post by william-r-stewart2013 on 2015-01-17
Sorry, thats haroopad

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Humm ...

I do not see the relationship between " libudev.so.0 " as per that Askubuntu link and haroopad.
Is this the method you followed to install 'haroopad' :
[http://pad.haroopress.com/user.html](http://pad.haroopress.com/user.html)

And what are the particular errors you see presently ?
post back the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

``` let's make sure the package manager is stable before we do anything.

More to the point, perhaps, why "haroopad" (beta) as the markdown editor - though it sure looks powerful and full featured ? There are several choices available in the software repository ( for ubuntu) that are tested and known to work.
Why make life so difficult for yourself by trying to install OEM software ? -- just a thought .

Find what the problem is
[INDENT][INDENT][INDENT]isolate to a solution
[/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
In retrospect i should of installed a different markdown editior.
these are the steps I used to install.

[COLOR=#555555][FONT=consolas]wget [https://bitbucket.org/rhiokim/haroopad-download/downloads/haroopad-v0.12.2_amd64.deb](https://bitbucket.org/rhiokim/haroopad-download/downloads/haroopad-v0.12.2_amd64.deb)
[/FONT][/COLOR][COLOR=#555555][FONT=consolas]sudo apt-get install gdebi
[/FONT][/COLOR][COLOR=#555555][FONT=consolas]sudo gdebi haroopad-v0.12.2_amd64.deb

should i puut those terminal commands in the root shell prompt in recovery mode?
Keep in mind I cant login to my system and or do text login ctrl-alt-f1.[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Well, yeah ....

As I flounder on determining how to proceed. Do boot into "recovery" console and run the package management commands. Will require "enable networking" to use a browser.

Presently, what is your mind set ? To fix this install and 'haroopad' - resolve it's dependencies
OR
Remove 'haroopad' see then if that fixes the install ?

It may not be the 'buntu way
[INDENT][INDENT][INDENT]but we try and do what we can
[/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
I could care less about keeping haroopad if that was the cause of the problem. I say lets get ride of it see if that fixes the system.
Just want to be able to fix this thing whatever it takes.

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Ho-Kay;

Let's remove and fix,

I would say that the damage is done, and even when 'haroopad'  is removed we will still have some damage control to effect.

Let's see what results:
Boot to recovery console into the root terminal.
We will need r/w on the system:
```

mount -o remount rw / 

```
Now try and remove the application:
```

dpkg -P haroopad

```
If there are advisories and/or errors we need to see them -in context - to have an idea of how to cope with getting you booting up .

Else if there are NO errors .. try and reboot the system normally and advise then on a status .

We do try to effect control of the damage
[INDENT][INDENT][INDENT]and make things right
[/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
No errors was able to run commands. Still cant log in on restart getting the same " libudev.so.0" error as before

---

### Post by william-r-stewart2013 on 2015-01-17
Update. I went ahead and downloaded libudev0_175-0ubuntu9_amd64.deb placed it in my download directory of the partion i couldnt boot into.
Installed package from root shell prompt and restarted system I was able to log in. 
Is there any other steps I should take to make sure my system is running up to snuff?

Thanks for all your help by the way.

---

### Post by william-r-stewart2013 on 2015-01-17
Im getting this error message now that i can log in. cant install updates or software.
Error message from software center is

installArchives() failed: dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.7 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9)
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.7)
dpkg: dependency problems prevent configuration of popcorn-time:
 popcorn-time depends on libudev1 | libudev0; however:
  Package libudev1 is not installed.
  Package libudev0 is not configured yet.
dpkg: error processing popcorn-time (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 libudev0:i386
 libudev0
 popcorn-time
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.7)
dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.7 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9)
dpkg: dependency problems prevent configuration of popcorn-time:
 popcorn-time depends on libudev1 | libudev0; however:
  Package libudev1 is not installed.
  Package libudev0 is not configured yet.
dpkg: error processing popcorn-time (--configure):
 dependency problems - leaving unconfigured

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; OK, making progress.

The correct version, per:
[http://packages.ubuntu.com/search?keywords=libudev0&searchon=names&suite=precise-updates&section=all](http://packages.ubuntu.com/search?keywords=libudev0&searchon=names&suite=precise-updates&section=all)
is: 175-0ubuntu9.8: amd64 i386

We have installed both the 32 bit and 64 bit versions, and the versions conflict.

Next we try and remove the unwanted version .. 
Is your system 32 bit or 64 bit ?

Then we install the correct version .

[INDENT][INDENT]maybe it will be
[INDENT][INDENT]just that easy
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
64 bit

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Well

Let's do "try" 
```

sudo apt-get remove libudev0:i386 

```
see what results, maybe have to get the more drastic but, let's try the simpler approach 1st .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]probable, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
Ok. Got this output.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gvfs:i386 : Depends: libudev0:i386 (>= 147) but it is not going to be installed
 libgudev-1.0-0:i386 : Depends: libudev0:i386 (>= 165) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Hummm ..

That went better than I had anticipated, but;
That also makes me question what other 32 bit applications are installed ??
Before we go any more forward, let's look at what might be behind us:
```

apt-cache depends gvfs:i386
apt-cache depends libgudev-1.0-0:i386

```

I have heard it said
[INDENT][INDENT]a little bit of paranoia 
[INDENT][INDENT][INDENT]can go a long way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
got this output.

billy@billy-X58A-UD3R:~$ apt-cache depends gvfs:i386
gvfs:i386
  Depends: libc6:i386
  Depends: libdbus-1-3:i386
  Depends: libglib2.0-0:i386
  Depends: libudev0:i386
  Depends: gvfs-daemons:i386
    gvfs-daemons
  Depends: gvfs-daemons:i386
    gvfs-daemons
  Depends: gvfs-libs:i386
  Depends: <gvfs-common:i386>
    gvfs-common
  Suggests: gvfs-backends:i386
    gvfs-backends
  Breaks: brasero
  Breaks: brasero:i386
  Breaks: libgdu0
  Breaks: libgdu0:i386
  Breaks: libglib2.0-0
  Breaks: libglib2.0-0:i386
  Breaks: rhythmbox
  Breaks: rhythmbox:i386
  Replaces: gvfs
  Breaks: gvfs
billy@billy-X58A-UD3R:~$ apt-cache depends libgudev-1.0-0:i386
libgudev-1.0-0:i386
  Depends: libc6:i386
  Depends: libglib2.0-0:i386
  Depends: libudev0:i386
  PreDepends: multiarch-support:i386
    multiarch-support
  Replaces: libgudev-1.0-0
  Breaks: libgudev-1.0-0
billy@billy-X58A-UD3R:~$

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Welp;

I see nothing to be disconcerting .

Let's take the package managers 'general' advise and:
```

sudo apt-get -f install

```
and see what we do next.

[INDENT][INDENT]moving right on along
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
billy@billy-X58A-UD3R:~$ sudo apt-get -f install
[sudo] password for billy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libreoffice-l10n-es libopenal1:i386 bluez-alsa:i386
  libsdl-ttf2.0-0:i386 libgconf-2-4:i386 libatk1.0-0:i386 libstdc++5:i386
  ia32-libs-multiarch:i386 libqt4-declarative:i386 libxcomposite1:i386 libgail18:i386
  libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386 libqt4-qt3support:i386
  libroken18-heimdal:i386 libunistring0:i386 libcupsimage2:i386 libgphoto2-port0:i386
  libidn11:i386 libnss3:i386 libwrap0:i386 libcaca0:i386 gtk2-engines:i386
  libgudev-1.0-0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libcdparanoia0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 screen-resolution-extra libjpeg8:i386 ia32-libs
  libaio1:i386 libsane:i386 odbcinst1debian2 odbcinst1debian2:i386 libqt4-test:i386
  libqt4-script:i386 libqt4-designer:i386 qt-at-spi:i386 libsdl-mixer1.2:i386
  libqt4-network:i386 libqt4-dbus:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386 gvfs-libs:i386 m4
  libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386 libcapi20-3:i386 libibus-1.0-0:i386
  libcairo2:i386 odbcinst libgssapi3-heimdal:i386 libvisual-0.4-0:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386
  libqt4-opengl:i386 libsoup-gnome2.4-1:i386 sni-qt:i386 libmysqlclient18:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 libc6-i386 lib32gcc1
  libqt4-xmlpatterns:i386 librsvg2-common:i386 libdatrie1:i386 libiec61883-0:i386
  libjson0:i386 libgdk-pixbuf2.0-0:i386 libsdl-image1.2:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386 libcurl3:i386
  libqtcore4:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386 libxft2:i386 libcroco3:i386
  libpulse-mainloop-glib0:i386 libtheora0:i386 libaa1:i386 libspeexdsp1:i386
  libieee1284-3:i386 libthai0:i386 rsync libxml2:i386 libao4:i386 pax libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libqt4-sql:i386 esound-common libasound2:i386
  libxpm4:i386 libflac8:i386 libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386
  libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386
  libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 rpm librpmbuild2 libqt4-xml:i386
  libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libtiff4:i386 libsdl-net1.2:i386 libjasper1:i386
  libreoffice-help-es libvisual-0.4-plugins:i386 libgstreamer-plugins-base0.10-0:i386
  libudev0:i386 libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386 libqtgui4:i386
  libvdpau1 libtag1c2a:i386 librsvg2-2:i386 libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386
  libsasl2-2:i386 gtk2-engines-oxygen:i386 lib32z1 xaw3dg:i386 libpango1.0-0:i386
  libpulse0:i386 libheimntlm0-heimdal:i386 librpmsign0 libpulsedsp:i386 gvfs:i386
  libqt4-sql-mysql:i386 libxcb-render0:i386 libodbc1:i386 libexif12:i386
  libqt4-scripttools:i386 librtmp0:i386 libxi6:i386 libvorbis0a:i386 libqtwebkit4:i386
  lsb-core libgstreamer0.10-0:i386 libxp6:i386 libaudio2:i386 libxcursor1:i386
  libxcb-shm0:i386 libxt6:i386 alien libxv1:i386 ncurses-term libsasl2-modules:i386
  libxrandr2:i386 gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386
  libmng1:i386 libgtk2.0-0:i386 openoffice.org-hyphenation libltdl7:i386
  libkrb5-26-heimdal:i386 libssl1.0.0:i386 libasound2-plugins:i386 glib-networking:i386
  libsoup2.4-1:i386 libgphoto2-2:i386 libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libudev0:i386
The following packages will be upgraded:
  libudev0:i386
1 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.
3 not fully installed or removed.
Need to get 0 B/31.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.7 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9.8)
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9.8 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.7)
dpkg: dependency problems prevent configuration of popcorn-time:
 popcorn-time depends on libudev1 | libudev0; however:
  Package libudev1 is not installed.
  Package libudev0 is not configured yet.
dpkg: error processing popcorn-time (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
           Errors were encountered while processing:
 libudev0:i386
 libudev0
 popcorn-time
E: Sub-process /usr/bin/dpkg returned an error code (1)
billy@billy-X58A-UD3R:~$

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Hey;

That looks daunting, humm ....


Looks like we gotta have it, so:
```

sudo apt-get install --reinstall libudev0:i386

```
let's see if the correct version gets installed.

By the way, out puts are much more readable within "code tags":
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]round and around we go
[/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
```
billy@billy-X58A-UD3R:~$ sudo apt-get install --reinstall libudev0:i386[sudo] password for billy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libreoffice-l10n-es libopenal1:i386 bluez-alsa:i386
  libsdl-ttf2.0-0:i386 libgconf-2-4:i386 libatk1.0-0:i386 libstdc++5:i386
  ia32-libs-multiarch:i386 libqt4-declarative:i386 libxcomposite1:i386 libgail18:i386
  libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386 libqt4-qt3support:i386
  libroken18-heimdal:i386 libunistring0:i386 libcupsimage2:i386 libgphoto2-port0:i386
  libidn11:i386 libnss3:i386 libwrap0:i386 libcaca0:i386 gtk2-engines:i386
  libgudev-1.0-0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libcdparanoia0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 screen-resolution-extra libjpeg8:i386 ia32-libs
  libaio1:i386 libsane:i386 odbcinst1debian2 odbcinst1debian2:i386 libqt4-test:i386
  libqt4-script:i386 libqt4-designer:i386 qt-at-spi:i386 libsdl-mixer1.2:i386
  libqt4-network:i386 libqt4-dbus:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386 gvfs-libs:i386 m4
  libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386 libcapi20-3:i386 libibus-1.0-0:i386
  libcairo2:i386 odbcinst libgssapi3-heimdal:i386 libvisual-0.4-0:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386
  libqt4-opengl:i386 libsoup-gnome2.4-1:i386 sni-qt:i386 libmysqlclient18:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 libc6-i386 lib32gcc1
  libqt4-xmlpatterns:i386 librsvg2-common:i386 libdatrie1:i386 libiec61883-0:i386
  libjson0:i386 libgdk-pixbuf2.0-0:i386 libsdl-image1.2:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386 libcurl3:i386
  libqtcore4:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386 libxft2:i386 libcroco3:i386
  libpulse-mainloop-glib0:i386 libtheora0:i386 libaa1:i386 libspeexdsp1:i386
  libieee1284-3:i386 libthai0:i386 rsync libxml2:i386 libao4:i386 pax libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libqt4-sql:i386 esound-common libasound2:i386
  libxpm4:i386 libflac8:i386 libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386
  libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386
  libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 rpm librpmbuild2 libqt4-xml:i386
  libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libtiff4:i386 libsdl-net1.2:i386 libjasper1:i386
  libreoffice-help-es libvisual-0.4-plugins:i386 libgstreamer-plugins-base0.10-0:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386 libqtgui4:i386 libvdpau1
  libtag1c2a:i386 librsvg2-2:i386 libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386
  libsasl2-2:i386 gtk2-engines-oxygen:i386 lib32z1 xaw3dg:i386 libpango1.0-0:i386
  libpulse0:i386 libheimntlm0-heimdal:i386 librpmsign0 libpulsedsp:i386 gvfs:i386
  libqt4-sql-mysql:i386 libxcb-render0:i386 libodbc1:i386 libexif12:i386
  libqt4-scripttools:i386 librtmp0:i386 libxi6:i386 libvorbis0a:i386 libqtwebkit4:i386
  lsb-core libgstreamer0.10-0:i386 libxp6:i386 libaudio2:i386 libxcursor1:i386
  libxcb-shm0:i386 libxt6:i386 alien libxv1:i386 ncurses-term libsasl2-modules:i386
  libxrandr2:i386 gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386
  libmng1:i386 libgtk2.0-0:i386 openoffice.org-hyphenation libltdl7:i386
  libkrb5-26-heimdal:i386 libssl1.0.0:i386 libasound2-plugins:i386 glib-networking:i386
  libsoup2.4-1:i386 libgphoto2-2:i386 libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libudev0:i386
1 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.
3 not fully installed or removed.
Need to get 0 B/31.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.7 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9.8)
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9.8 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.7)
dpkg: dependency problems prevent configuration of popcorn-time:
 popcorn-time depends on libudev1 | libudev0; however:
  Package libudev1 is not installed.
  Package libudev0 is not configured yet.
dpkg: error processing popcorn-time (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
           Errors were encountered while processing:
 libudev0:i386
 libudev0
 popcorn-time
E: Sub-process /usr/bin/dpkg returned an error code (1)
billy@billy-X58A-UD3R:~$
```

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Shucks;

We have to break this vicious circle somehow, so let's take it by force:
```

sudo dpkg --remove --force-remove-reinstreq libudev0:i386
sudo apt-get install libudev0:i386

```

[INDENT][INDENT]maybe now ?
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
It is a vicious cycle. ```
billy@billy-X58A-UD3R:~$ sudo dpkg --remove --force-remove-reinstreq libudev0:i386[sudo] password for billy: 
dpkg: dependency problems prevent removal of libudev0:i386:
 gvfs:i386 depends on libudev0 (>= 147).
 libgudev-1.0-0:i386 depends on libudev0 (>= 165).
dpkg: error processing libudev0:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libudev0:i386



```

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; surprise, surprise ...........

What should be:
> 
Package gvfs

precise-updates (libs): userspace virtual filesystem - GIO module 
1.12.1-0ubuntu1.2: amd64 i386


So let's look and see what is installed on the system for these packages
```

dpkg -l gvfs
dokg -l libgudev-1.0-0
apt-cache policy gvfs:i386
apt-cache policy libgudev-1.0-0:i386

```

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
```
billy@billy-X58A-UD3R:~$ dpkg -l gvfsDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version           Description
+++-=================-=================-==================================================
ii  gvfs              1.12.1-0ubuntu1.2 userspace virtual filesystem - GIO module
billy@billy-X58A-UD3R:~$ dpkg -l libgudev-1.0-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version           Description
+++-=================-=================-==================================================
ii  libgudev-1.0-0    1:175-0ubuntu9.7  GObject-based wrapper library for libudev
billy@billy-X58A-UD3R:~$ apt-cache policy gvfs:i386
gvfs:i386:
  Installed: 1.12.1-0ubuntu1.2
  Candidate: 1.12.1-0ubuntu1.2
  Version table:
 *** 1.12.1-0ubuntu1.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1.12.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
billy@billy-X58A-UD3R:~$ apt-cache policy libgudev-1.0-0:i386
libgudev-1.0-0:i386:
  Installed: 1:175-0ubuntu9.7
  Candidate: 1:175-0ubuntu9.8
  Version table:
     1:175-0ubuntu9.8 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
 *** 1:175-0ubuntu9.7 0
        100 /var/lib/dpkg/status
     1:175-0ubuntu9 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
billy@billy-X58A-UD3R:~$ 
```

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Well !

Guess what we now know .

This is the correct version:
> 
Package libgudev-1.0-0

precise-updates (libs): GObject-based wrapper library for libudev 
1:175-0ubuntu9.8: amd64 i386


But, but there is installed:
> 
libgudev-1.0-0:i386:
  Installed: 1:175-0ubuntu9.7


let's re-focus our attention and try and get libgudev-1.0-0:i386 updated .
```

sudo apt-get remove libgudev-1.0-0:i386
sudo apt-get install libgudev-1.0-0:i386

```

Maybe yes, and we can proceed :)
Maybe no, and more work :(

[INDENT][INDENT]anyway, we will know more
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
```
billy@billy-X58A-UD3R:~$ sudo apt-get remove libgudev-1.0-0:i386[sudo] password for billy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gstreamer0.10-plugins-good:i386 : Depends: libgudev-1.0-0:i386 (>= 147) but it is not going to be installed
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is to be installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ sudo apt-get install libgudev-1.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgudev-1.0-0 : Breaks: libgudev-1.0-0:i386 (!= 1:175-0ubuntu9.7) but 1:175-0ubuntu9.8 is to be installed
 libgudev-1.0-0:i386 : Breaks: libgudev-1.0-0 (!= 1:175-0ubuntu9.8) but 1:175-0ubuntu9.7 is to be installed
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is to be installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ 
```

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Sheessshhh .. as

Around and round we go:
```

sudo apt-get remove libudev0
sudo apt-get remove libudev0:i386
sudo apt-get install libudev0
sudo apt-get install libudev0:i386

```

Hoping IF we remove both, we can then install ..

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-17
```
billy@billy-X58A-UD3R:~$ sudo apt-get remove libudev0[sudo] password for billy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bluez : Depends: libudev0 (>= 147) but it is not going to be installed
 chromium-browser : Depends: libudev0 (>= 147) but it is not going to be installed
 dmsetup : Depends: libudev0 (>= 147) but it is not going to be installed
 google-chrome-stable : Depends: libudev0 (>= 147) but it is not going to be installed or
                                 libudev1 (>= 198) but it is not installable
 gvfs : Depends: libudev0 (>= 147) but it is not going to be installed
 gvfs-daemons : Depends: libudev0 (>= 147) but it is not going to be installed
 initramfs-tools-bin : Depends: libudev0 (>= 147) but it is not going to be installed
 libatasmart4 : Depends: libudev0 (>= 147) but it is not going to be installed
 libdevmapper1.02.1 : Depends: libudev0 (>= 147) but it is not going to be installed
 libgudev-1.0-0 : Depends: libudev0 (>= 165) but it is not going to be installed
 mountall : Depends: libudev0 (>= 151) but it is not going to be installed
 popcorn-time : Depends: libudev1 but it is not installable or
                         libudev0 but it is not going to be installed
 pulseaudio : Depends: libudev0 (>= 147) but it is not going to be installed
 system-config-printer-udev : Depends: libudev0 (>= 161) but it is not going to be installed
 udev : Depends: libudev0 (>= 175) but it is not going to be installed
 udisks : Depends: libudev0 (>= 147) but it is not going to be installed
 upstart : Depends: libudev0 (>= 151) but it is not going to be installed
 xserver-xorg-core : Depends: libudev0 (>= 147) but it is not going to be installed
 xserver-xorg-video-intel : Depends: libudev0 (>= 147) but it is not going to be installed
 xserver-xorg-video-nouveau : Depends: libudev0 (>= 147) but it is not going to be installed
 xserver-xorg-video-radeon : Depends: libudev0 (>= 147) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ sudo apt-get remove libudev0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gvfs:i386 : Depends: libudev0:i386 (>= 147) but it is not going to be installed
 libgudev-1.0-0:i386 : Depends: libudev0:i386 (>= 165) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ sudo apt-get install libudev0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libudev0 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is to be installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ sudo apt-get install libudev0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libreoffice-l10n-es libopenal1:i386 bluez-alsa:i386
  libsdl-ttf2.0-0:i386 libgconf-2-4:i386 libatk1.0-0:i386 libstdc++5:i386
  ia32-libs-multiarch:i386 libqt4-declarative:i386 libxcomposite1:i386 libgail18:i386
  libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386 libqt4-qt3support:i386
  libroken18-heimdal:i386 libunistring0:i386 libcupsimage2:i386 libgphoto2-port0:i386
  libidn11:i386 libnss3:i386 libwrap0:i386 libcaca0:i386 gtk2-engines:i386
  libgudev-1.0-0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libcdparanoia0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 screen-resolution-extra libjpeg8:i386 ia32-libs
  libaio1:i386 libsane:i386 odbcinst1debian2 odbcinst1debian2:i386 libqt4-test:i386
  libqt4-script:i386 libqt4-designer:i386 qt-at-spi:i386 libsdl-mixer1.2:i386
  libqt4-network:i386 libqt4-dbus:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386 gvfs-libs:i386 m4
  libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386 libcapi20-3:i386 libibus-1.0-0:i386
  libcairo2:i386 odbcinst libgssapi3-heimdal:i386 libvisual-0.4-0:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386
  libqt4-opengl:i386 libsoup-gnome2.4-1:i386 sni-qt:i386 libmysqlclient18:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 libc6-i386 lib32gcc1
  libqt4-xmlpatterns:i386 librsvg2-common:i386 libdatrie1:i386 libiec61883-0:i386
  libjson0:i386 libgdk-pixbuf2.0-0:i386 libsdl-image1.2:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386 libcurl3:i386
  libqtcore4:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386 libxft2:i386 libcroco3:i386
  libpulse-mainloop-glib0:i386 libtheora0:i386 libaa1:i386 libspeexdsp1:i386
  libieee1284-3:i386 libthai0:i386 rsync libxml2:i386 libao4:i386 pax libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libqt4-sql:i386 esound-common libasound2:i386
  libxpm4:i386 libflac8:i386 libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386
  libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386
  libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 rpm librpmbuild2 libqt4-xml:i386
  libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libtiff4:i386 libsdl-net1.2:i386 libjasper1:i386
  libreoffice-help-es libvisual-0.4-plugins:i386 libgstreamer-plugins-base0.10-0:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386 libqtgui4:i386 libvdpau1
  libtag1c2a:i386 librsvg2-2:i386 libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386
  libsasl2-2:i386 gtk2-engines-oxygen:i386 lib32z1 xaw3dg:i386 libpango1.0-0:i386
  libpulse0:i386 libheimntlm0-heimdal:i386 librpmsign0 libpulsedsp:i386 gvfs:i386
  libqt4-sql-mysql:i386 libxcb-render0:i386 libodbc1:i386 libexif12:i386
  libqt4-scripttools:i386 librtmp0:i386 libxi6:i386 libvorbis0a:i386 libqtwebkit4:i386
  lsb-core libgstreamer0.10-0:i386 libxp6:i386 libaudio2:i386 libxcursor1:i386
  libxcb-shm0:i386 libxt6:i386 alien libxv1:i386 ncurses-term libsasl2-modules:i386
  libxrandr2:i386 gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386
  libmng1:i386 libgtk2.0-0:i386 openoffice.org-hyphenation libltdl7:i386
  libkrb5-26-heimdal:i386 libssl1.0.0:i386 libasound2-plugins:i386 glib-networking:i386
  libsoup2.4-1:i386 libgphoto2-2:i386 libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libudev0:i386
1 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.
3 not fully installed or removed.
Need to get 0 B/31.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.7 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9.8)
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9.8 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.7)
dpkg: dependency problems prevent configuration of popcorn-time:
 popcorn-time depends on libudev1 | libudev0; however:
  Package libudev1 is not installed.
  Package libudev0 is not configured yet.
dpkg: error processing popcorn-time (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
           Errors were encountered while processing:
 libudev0:i386
 libudev0
 popcorn-time
E: Sub-process /usr/bin/dpkg returned an error code (1)
billy@billy-X58A-UD3R:~$ 



```

---

### Post by Bashing-om on 2015-01-17
william-r-stewart2013; Why am I not surprised ?

Ok, where did you get 'popcorn-time' ?
```

apt-cache show popcorn-time

``` as I can not see it in my install.

Let's see if this can/does us any good:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
85 not upgraded does have my attention

I am afraid to remove the obsolete packages until we have this present situation under control.

still after all this ->
[INDENT][INDENT]going round and around
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013; Hey;

I am done for this session/ Think'n getting cloudy and forced.
We sleep on this, and perhaps come up with an avenue of attack.
I will return after Church tomorrow.

[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-18
Ran the last set of commands heres the result
```
billy@billy-X58A-UD3R:~$ apt-cache show popcorn-timePackage: popcorn-time
Priority: extra
Section: net
Installed-Size: 124
Maintainer: Alin Andrei <webupd8@gmail.com>
Architecture: all
Version: 0.3.7.1-1~webupd8~0
Depends: libudev1 | libudev0
Pre-Depends: wget, binutils, debconf (>= 0.5) | debconf-2.0
Filename: pool/main/p/popcorn-time/popcorn-time_0.3.7.1-1~webupd8~0_all.deb
Size: 66832
MD5sum: 9a13f1c9defd1f5724497c9732c7119c
SHA1: 60384347a21fde826798d578fd38c9782da75b44
SHA256: 2ec4dcb243bdd71d0e0c94e1e175cd0d87c8d70710a693c27e19c260586509d8
Description-en: Popcorn Time
 Watch Movies and TV Shows instantly
 .
 Popcorn Time streams movies and TV shows from torrents
 .
 Important: Downloading copyrighted material may be illegal in your country. Use at your own risk.
Description-md5: 0cf1cbb0de1e555211f315b5fd931408


Package: popcorn-time
Status: install ok half-configured
Priority: extra
Section: net
Installed-Size: 124
Maintainer: Alin Andrei <webupd8@gmail.com>
Architecture: all
Version: 0.3.6-1~webupd8~0
Config-Version: 0.3.5.3-1~webupd8~1
Depends: libudev1 | libudev0
Pre-Depends: wget, binutils, debconf (>= 0.5) | debconf-2.0
Description-en: Popcorn Time
 Watch Movies and TV Shows instantly
 .
 Popcorn Time streams movies and TV shows from torrents
 .
 Important: Downloading copyrighted material may be illegal in your country. Use at your own risk.
Homepage: https://popcorntime.io/


billy@billy-X58A-UD3R:~$ 
billy@billy-X58A-UD3R:~$ sudo apt-get update
[sudo] password for billy: 
Hit http://repo.steampowered.com precise Release.gpg
Hit http://repo.steampowered.com precise Release                                              
Hit http://dl.google.com stable Release.gpg                                                   
Hit http://repo.steampowered.com precise/steam Sources                                        
Hit http://us.archive.ubuntu.com precise Release.gpg                                          
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                                  
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                
Hit http://dl.google.com stable Release                                                       
Hit http://us.archive.ubuntu.com precise Release                                              
Hit http://us.archive.ubuntu.com precise-updates Release                                      
Hit http://repo.steampowered.com precise/steam amd64 Packages                                 
Hit http://security.ubuntu.com precise-security Release.gpg                                   
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://download.virtualbox.org precise Release.gpg                                        
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Ign http://ppa.launchpad.net precise Release.gpg                                              
Hit http://us.archive.ubuntu.com precise-backports Release                                    
Hit http://security.ubuntu.com precise-security Release                                       
Hit http://dl.google.com stable/main amd64 Packages                                           
Hit http://repo.steampowered.com precise/steam i386 Packages                                  
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://download.virtualbox.org precise Release                                            
Hit http://us.archive.ubuntu.com precise/main Sources                                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                                   
Hit http://us.archive.ubuntu.com precise/universe Sources                                     
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                   
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                  
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                            
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages                              
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages                            
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                   
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                             
Hit http://security.ubuntu.com precise-security/main Sources                                  
Hit http://ppa.launchpad.net precise Release.gpg                                              
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                                    
Hit http://downloads.sourceforge.net all Release.gpg                                          
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                                    
Hit http://dl.google.com stable/main i386 Packages                                            
Hit http://download.virtualbox.org precise/contrib amd64 Packages                             
Hit http://security.ubuntu.com precise-security/restricted Sources                            
Hit http://security.ubuntu.com precise-security/universe Sources                              
Hit http://security.ubuntu.com precise-security/multiverse Sources                            
Hit http://security.ubuntu.com precise-security/main amd64 Packages                           
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                     
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                       
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                     
Hit http://security.ubuntu.com precise-security/main i386 Packages                            
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                      
Hit http://security.ubuntu.com precise-security/universe i386 Packages                        
Ign http://dl.google.com stable/main TranslationIndex                                         
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                               
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                             
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                          
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                          
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                            
Hit http://us.archive.ubuntu.com precise-updates/main Sources                                 
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources                           
Hit http://us.archive.ubuntu.com precise-updates/universe Sources                             
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources                           
Hit http://download.virtualbox.org precise/contrib i386 Packages                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Ign http://repo.steampowered.com precise/steam TranslationIndex                               
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages                          
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages                           
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages                     
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages                     
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                        
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                  
Hit http://archive.getdeb.net trusty-getdeb Release.gpg                                       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                      
Hit http://security.ubuntu.com precise-security/main TranslationIndex                         
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                   
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                     
Ign http://download.virtualbox.org precise/contrib TranslationIndex                           
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                  
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                    
Hit http://us.archive.ubuntu.com precise-backports/main Sources                               
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                         
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                           
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                         
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                        
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                  
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                  
Hit http://security.ubuntu.com precise-security/main Translation-en                           
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                     
Hit http://security.ubuntu.com precise-security/restricted Translation-en                     
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://security.ubuntu.com precise-security/universe Translation-en                       
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                         
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                   
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                     
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                   
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                      
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                
Hit http://downloads.sourceforge.net all Release                                              
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Ign http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                  
Hit http://us.archive.ubuntu.com precise/main Translation-en                                  
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                            
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                            
Hit http://us.archive.ubuntu.com precise/universe Translation-en                              
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                          
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                    
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                      
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                  
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                    
Get:3 http://ppa.launchpad.net precise Release [12.9 kB]                                      
Get:4 http://ppa.launchpad.net precise Release [12.9 kB]                                      
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://downloads.sourceforge.net all/main amd64 Packages                                  
Ign http://dl.google.com stable/main Translation-en_US                                        
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://archive.getdeb.net trusty-getdeb Release                                           
Ign http://dl.google.com stable/main Translation-en                                           
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://download.virtualbox.org precise/contrib Translation-en_US                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Ign http://download.virtualbox.org precise/contrib Translation-en                             
Ign http://downloads.sourceforge.net all/main TranslationIndex                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://downloads.sourceforge.net all/main i386 Packages                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                               
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                 
Hit https://private-ppa.launchpad.net precise Release.gpg                                     
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                  
Hit http://ppa.launchpad.net precise/main i386 Packages                                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Get:5 http://ppa.launchpad.net precise/main Sources [18.6 kB]                                 
Get:6 http://ppa.launchpad.net precise/main amd64 Packages [23.2 kB]                          
Get:7 http://ppa.launchpad.net precise/main i386 Packages [23.2 kB]                           
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                                
Ign http://archive.getdeb.net trusty-getdeb/apps TranslationIndex                             
Get:8 http://ppa.launchpad.net precise/main TranslationIndex [202 B]                          
Get:9 http://ppa.launchpad.net precise/main Sources [30.7 kB]                                 
Get:10 http://ppa.launchpad.net precise/main amd64 Packages [21.5 kB]                         
Ign http://downloads.sourceforge.net all/main Translation-en_US                               
Hit https://private-ppa.launchpad.net precise Release                                         
Ign http://repo.steampowered.com precise/steam Translation-en_US                              
Ign http://downloads.sourceforge.net all/main Translation-en                                  
Get:11 http://ppa.launchpad.net precise/main i386 Packages [21.5 kB]                          
Get:12 http://ppa.launchpad.net precise/main TranslationIndex [202 B]                         
Hit http://ppa.launchpad.net precise/main Sources                                             
Ign http://repo.steampowered.com precise/steam Translation-en                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources                  
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages           
Hit http://ppa.launchpad.net precise/main i386 Packages            
Ign http://ppa.launchpad.net precise/main TranslationIndex         
Hit http://ppa.launchpad.net precise/main Sources                  
Hit http://ppa.launchpad.net precise/main amd64 Packages           
Hit http://ppa.launchpad.net precise/main i386 Packages            
Ign http://ppa.launchpad.net precise/main TranslationIndex          
Hit http://ppa.launchpad.net precise/main Sources                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                             
Hit http://ppa.launchpad.net precise/main i386 Packages                              
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit https://private-ppa.launchpad.net precise/main amd64 Packages                             
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                         
Hit http://ppa.launchpad.net precise/main i386 Packages                          
Hit http://ppa.launchpad.net precise/main TranslationIndex                       
Hit http://ppa.launchpad.net precise/main Sources                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                         
Hit http://ppa.launchpad.net precise/main i386 Packages                          
Hit http://ppa.launchpad.net precise/main TranslationIndex                       
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit https://private-ppa.launchpad.net precise/main i386 Packages                           
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                  
Get:13 http://ppa.launchpad.net precise/main Translation-en [12.1 kB]    
Get:14 http://ppa.launchpad.net precise/main Translation-en [6,316 B]                         
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                        
Hit http://ppa.launchpad.net precise/main Translation-en                        
Get:15 https://private-ppa.launchpad.net precise/main TranslationIndex [357 B]
Ign https://private-ppa.launchpad.net precise/main TranslationIndex                           
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                  
Err http://ppa.launchpad.net precise/main Sources                                             
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages                     
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                      
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en         
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US                          
Ign https://private-ppa.launchpad.net precise/main Translation-en                             
Fetched 184 kB in 7s (24.9 kB/s)                                                              
W: Failed to fetch http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
billy@billy-X58A-UD3R:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is installed
W: Duplicate sources.list entry http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main amd64 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main i386 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
billy@billy-X58A-UD3R:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is installed
E: Unmet dependencies. Try using -f.
billy@billy-X58A-UD3R:~$ 



```

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013; More progress ... good .


Seeking what is holding 'libudev0:i386 ' to that lower version ->
OK, we now know that 'popcorn-time' is the source of at least one problem, from:
> 
Package: popcorn-time
Status: install ok half-configured

&&
Filename: pool/main/p/popcorn-time/popcorn-time_0.3.7.1-1~webupd8~0_all.deb

&&
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                             
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/precise/main/source/Sources)  404  Not Found

elementaeyart is NOT supported in precise; per:
> 
[http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/](http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu/dists/)

-there is no listing for "precise".

So the 1st order of business now is the disable that PPA too .
Then we focus on what it takes to remove 'popcorn-time' and see what it takes to (re-)install 'popcorn-time' .
The good news is that 'popcorn-time continues to have full support from the maintainer .

Meanwhile, back at the ranch
[INDENT][INDENT]doing my homework to find a proper way to (re-)install 'pop-corn'
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013;; Got it !

A quick search on Google and the author advises on the steps:
```

Andrew Admin  Pete Jones • 8 months ago
I've added a work-around which will hopefully get the installer to work now. So remove it, update the software sources and try to install it again:
sudo apt-get remove popcorn-time
sudo apt-get update
sudo apt-get install popcorn-time

Let me know if it works now!

```

So once the offending PPA for elementaryart is disabled, see if/what happens with removing/reinstalling 'popcorn-time'.

[INDENT][INDENT]I rest my case, pending 
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-18
I disable that software source in softwre center.
Ran the list commands. Heres the output.
```
billy@billy-X58A-UD3R:~$ sudo apt-get remove popcorn-time[sudo] password for billy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is to be installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ sudo apt-get update
Hit http://repo.steampowered.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg                                   
Hit http://repo.steampowered.com precise Release                                              
Hit http://download.virtualbox.org precise Release.gpg                                        
Hit http://dl.google.com stable Release.gpg                                                   
Hit http://security.ubuntu.com precise-security Release                                       
Hit http://download.virtualbox.org precise Release                                            
Hit http://us.archive.ubuntu.com precise Release.gpg                                          
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                                  
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                
Hit http://security.ubuntu.com precise-security/main Sources                                  
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://dl.google.com stable Release                                                       
Hit http://us.archive.ubuntu.com precise Release                                              
Hit http://us.archive.ubuntu.com precise-updates Release                                      
Hit http://download.virtualbox.org precise/contrib amd64 Packages                             
Hit http://security.ubuntu.com precise-security/restricted Sources                            
Hit http://security.ubuntu.com precise-security/universe Sources                              
Hit http://security.ubuntu.com precise-security/multiverse Sources                            
Hit http://security.ubuntu.com precise-security/main amd64 Packages                           
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                     
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                       
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                     
Hit http://security.ubuntu.com precise-security/main i386 Packages                            
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                      
Hit http://security.ubuntu.com precise-security/universe i386 Packages                        
Hit http://us.archive.ubuntu.com precise-backports Release                                    
Hit http://dl.google.com stable/main amd64 Packages                                           
Hit http://download.virtualbox.org precise/contrib i386 Packages                              
Hit http://us.archive.ubuntu.com precise/main Sources                                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                                   
Hit http://us.archive.ubuntu.com precise/universe Sources                                     
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                   
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                  
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                            
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages                              
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages                            
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                   
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                             
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://repo.steampowered.com precise/steam Sources                                        
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                               
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                             
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                          
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                          
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                            
Hit http://dl.google.com stable/main i386 Packages                                            
Ign http://dl.google.com stable/main TranslationIndex                                         
Ign http://download.virtualbox.org precise/contrib TranslationIndex                           
Hit http://us.archive.ubuntu.com precise-updates/main Sources                                 
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources                           
Hit http://us.archive.ubuntu.com precise-updates/universe Sources                             
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources                           
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                      
Hit http://security.ubuntu.com precise-security/main TranslationIndex                         
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                   
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages                          
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages                           
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                     
Hit http://archive.getdeb.net trusty-getdeb Release.gpg                                       
Hit http://downloads.sourceforge.net all Release.gpg                                          
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages                     
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages                     
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                        
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                  
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                  
Hit http://security.ubuntu.com precise-security/main Translation-en                           
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                     
Hit http://security.ubuntu.com precise-security/restricted Translation-en                     
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                    
Hit http://us.archive.ubuntu.com precise-backports/main Sources                               
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                         
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                           
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                         
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                        
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                  
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                  
Hit http://security.ubuntu.com precise-security/universe Translation-en                       
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                         
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                   
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                     
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                   
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                      
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                
Hit http://repo.steampowered.com precise/steam amd64 Packages                                 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                  
Hit http://us.archive.ubuntu.com precise/main Translation-en                                  
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                            
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                            
Hit http://us.archive.ubuntu.com precise/universe Translation-en                              
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                          
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                    
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                      
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                  
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                    
Hit http://repo.steampowered.com precise/steam i386 Packages                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://downloads.sourceforge.net all Release                                              
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                  
Ign http://repo.steampowered.com precise/steam TranslationIndex                               
Hit http://archive.getdeb.net trusty-getdeb Release                                           
Ign http://download.virtualbox.org precise/contrib Translation-en_US                          
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Ign http://dl.google.com stable/main Translation-en_US                                        
Ign http://download.virtualbox.org precise/contrib Translation-en                             
Ign http://dl.google.com stable/main Translation-en                                           
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit https://private-ppa.launchpad.net precise Release.gpg                                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit https://private-ppa.launchpad.net precise Release                                         
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit https://private-ppa.launchpad.net precise/main amd64 Packages                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                                 
Hit http://downloads.sourceforge.net all/main amd64 Packages                                  
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                                
Ign http://archive.getdeb.net trusty-getdeb/apps TranslationIndex                             
Ign http://downloads.sourceforge.net all/main TranslationIndex                                
Hit https://private-ppa.launchpad.net precise/main i386 Packages                              
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://downloads.sourceforge.net all/main i386 Packages                                   
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Get:1 https://private-ppa.launchpad.net precise/main TranslationIndex [357 B]                 
Ign https://private-ppa.launchpad.net precise/main TranslationIndex                           
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Sources                                             
Hit http://ppa.launchpad.net precise/main amd64 Packages                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                    
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Ign http://repo.steampowered.com precise/steam Translation-en_US                              
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Ign http://repo.steampowered.com precise/steam Translation-en                                 
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Ign http://downloads.sourceforge.net all/main Translation-en_US                               
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Ign http://downloads.sourceforge.net all/main Translation-en                                  
Hit http://ppa.launchpad.net precise/main Translation-en                                      
Hit http://ppa.launchpad.net precise/main Translation-en                 
Hit http://ppa.launchpad.net precise/main Translation-en                 
Ign http://ppa.launchpad.net precise/main Translation-en_US                                   
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en
Reading package lists... Done                                                                 
W: Duplicate sources.list entry http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main amd64 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main i386 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
billy@billy-X58A-UD3R:~$ sudo apt-get install popcorn-time
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libudev0 : Breaks: libudev0:i386 (!= 175-0ubuntu9.8) but 175-0ubuntu9.7 is to be installed
 libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) but 175-0ubuntu9.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@billy-X58A-UD3R:~$ 



```

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013; shucks,

So much for that thought.
1) Fix the sources list files again.
Fire up a text editor and find the duplicates:
> 
W: Duplicate sources.list entry [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main amd64 Packages

Check both "/etc/apt/sources.list" file and in the 3rd party directory " /etc/apt/sources.list.d " Remove one of those listings. If the duplicate is in "/etc/apt/sources.list" file .. remove it from that file as it properly belongs in that 3rd party directory .

2) popcorn-time: That so far we can not remove
What returns:
```

apt-cache policy popcorn-time
apt-cache depends popcorn-time
apt-cache rdepends popcorn-time

```

As I consider **IF** it is time to manually intervene in the package manager's business .

[INDENT][INDENT]what to do, oh what to do
[/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-18
So i should delete the file elementaryart-elementary-dev-precise.list? theres also a elementaryart-elementary-dev-precise.list.save.
Sorry this is gettin a bit confusing for me. Also scared of breaking system now that Im finally able to log back in.

Heres the result of the command for popcorn-time
```
billy@billy-X58A-UD3R:~$ apt-cache policy popcorn-timepopcorn-time:
  Installed: 0.3.6-1~webupd8~0
  Candidate: 0.3.7.1-1~webupd8~0
  Version table:
     0.3.7.1-1~webupd8~0 0
        500 http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu/ precise/main amd64 Packages
 *** 0.3.6-1~webupd8~0 0
        100 /var/lib/dpkg/status
billy@billy-X58A-UD3R:~$ apt-cache depends popcorn-time
popcorn-time
 |Depends: <libudev1>
  Depends: libudev0
  PreDepends: wget
    wget:i386
  PreDepends: binutils
 |PreDepends: debconf
  PreDepends: <debconf-2.0>
    cdebconf
    debconf
billy@billy-X58A-UD3R:~$ apt-cache rdepends popcorn-time
popcorn-time
Reverse Depends:
billy@billy-X58A-UD3R:~$ 
```

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013; Well, well ..

> 
apt-cache policy popcorn-timepopcorn-time:
  Installed: 0.3.6-1~webupd8~0
  Candidate: 0.3.7.1-1~webupd8~0

&&
popcorn-time
 |Depends: <libudev1>
  Depends: libudev0


But we can not remove 'popcorn-time' or reinstall it due to that dependency issue between ' libudev0 " and ' libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) ' .
I am presently stuck on a way to proceed .. but I am giving it great consideration; hoping to stay within the package manager .

For our thought process, though .. what is in the file " /var/lib/dpkg/status" for the stanza - search term - Package: libudev0  ?
Fire up a text editor to that fie, and copy and paste the stanza back to the forum for our inspection .. maybe get an idea of where to go from here .

OK. editing out that duplicate : ..post back again an updated:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

``` and I hunt up where the duplicate entry is and advise on the means to remove it.

[INDENT][INDENT]there is that way forward,
[INDENT][INDENT][INDENT][INDENT]somehow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-01-18
william-r-stewart2013; Well, well ..

> 
apt-cache policy popcorn-timepopcorn-time:
  Installed: 0.3.6-1~webupd8~0
  Candidate: 0.3.7.1-1~webupd8~0

&&
popcorn-time
 |Depends: <libudev1>
  Depends: libudev0


But we can not remove 'popcorn-time' or reinstall it due to that dependency issue between ' libudev0 " and ' libudev0:i386 : Breaks: libudev0 (!= 175-0ubuntu9.7) ' .
I am presently stuck on a way to proceed .. but I am giving it great consideration; hoping to stay within the package manager .

For our thought process, though .. what is in the file " /var/lib/dpkg/status" for the stanza - search term - Package: libudev0:i386 ?
Fire up a text editor to that fie, and copy and paste the stanza back to the forum for our inspection .. maybe get an idea of where to go from here .

OK. editing out that duplicate : ..post back again an updated:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

``` and I hunt up where the duplicate entry is and advise on the means to remove it.

[INDENT][INDENT]there is that way forward,
[INDENT][INDENT][INDENT][INDENT]somehow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by william-r-stewart2013 on 2015-01-19
I'm throwing in the towel my friend. Appreciate all the help. I was able to finish some work and backup my files.
At this point its going to be easier to just re-install. 
This is a bad problem. Hope nobody runs into it in the future. 
One of the only problems I have ever had on a linux distro that had no solutions online.
Crazy!!

---

### Post by Bashing-om on 2015-01-19
william-r-stewart2013; Welp, yeah ...

It is faster and easier to just take the nuclear solution and (RE-)install. Taking what you have learned and applying it in the new install. 
In the log run, in this situation a fresh install might be the better thing to do. As you now know, introducing 3rd party software into ubuntu is not without some hazards. It always warrants keeping an eye on a continued relationship ; How that 3rd party software keeps up in a changing environment (system updates/upgrades) .

As much as I would like to know this solution, I do realize
[INDENT][INDENT]time is an essence
[/INDENT][/INDENT]

---

