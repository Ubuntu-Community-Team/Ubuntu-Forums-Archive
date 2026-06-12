---
title: "Failed to upgrade: failed to exec tar..."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by jemmyyong on 2007-11-20
Hi....

I want to upgrade my Ubuntu with"sudo apt-get update" then "sudo apt-get upgrade"
After downloading files, here's the error log :

Preconfiguring packages ...
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/util-linux_2.12r-4ubuntu6.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.12r-4ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me!


Regards,
Jemmyyong

---

### Post by Arthur Archnix on 2007-11-20
The first thing I try when an update fails is
```
sudo apt-get clean
```
Then I try again.

---

### Post by stchman on 2007-11-20
> **jemmyyong said:**
> Hi....

I want to upgrade my Ubuntu with"sudo apt-get update" then "sudo apt-get upgrade"
After downloading files, here's the error log :

Preconfiguring packages ...
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/util-linux_2.12r-4ubuntu6.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.12r-4ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me!


Regards,
Jemmyyong

Are you talking about upgrading say Feisty to Gutsy?  If yes then just go to the Upgrade Manager and it will tell you there is a new distribution available.

---

### Post by jemmyyong on 2007-11-21
I didn't meant to upgrade from Dapper to Feisty or Gutsy, just upgrading installed packages.

After : "sudo apt-get clean", I try to upgrade packages but it didn't work.

dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
......................................

I cannot install/upgrade any packages. Is there any other way?

---

### Post by Arthur Archnix on 2007-11-21
First I would try and remove the offending package:
```
sudo rm /var/cache/apt/archives/util-linux_2.12r-4ubuntu6.1_i386.deb
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

**If** that fails then you can try
```
sudo apt-get install -f
```
Then try to update and upgrade again.

---

### Post by jemmyyong on 2007-11-23
sudo apt-get clean
  removes all files in /var/cache/apt/archives/

jemmy@jemmy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 164 not upgraded.

still doesn't work..!

---

### Post by xeth_delta on 2007-11-23
> **jemmyyong said:**
> I didn't meant to upgrade from Dapper to Feisty or Gutsy, just upgrading installed packages.

After : "sudo apt-get clean", I try to upgrade packages but it didn't work.

dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
......................................

I cannot install/upgrade any packages. Is there any other way?

I wonder if what is missing is actually tar itself.

```
aptitude search tar
```

If it is somehow not installed anymore, you can download the package manually from [http://packages.ubuntu.com]("http://packages.ubuntu.com") and then

```
dpkg -i tar-package.deb
```

Xeth

---

### Post by jemmyyong on 2007-11-23
jemmy@jemmy-desktop:~$ aptitude search tar
........
p   starvoyager                     - 2D space arcade game, themed around 'Star
p   starvoyager-data                - 2D space arcade game, themed around 'Star
p   system-config-kickstart         - graphical tool for creating Kickstart file
i   tar                             - GNU tar
p   tarcust                         - Tarball filter
p   tardy                           - A tar(5) post-processor
.......


after download tar_1.15.1-2ubuntu2.2_i386.deb :

jemmy@jemmy-desktop:~$ sudo dpkg -i tar_1.15.1-2ubuntu2.2_i386.deb
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing tar_1.15.1-2ubuntu2.2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 tar_1.15.1-2ubuntu2.2_i386.deb

---

### Post by xeth_delta on 2007-11-23
Maybe the logs give some information
```
cat /var/log/dpkg.log
```

Have you installed anything that might have broken the package system lately? Are you an Automatix user. I remember reading on a blog that sometimes under certain circumstances it can create some problems.

Xeth

[EDIT] Have you tried
```
sudo dpkg-reconfigure dpkg
```

---

### Post by jemmyyong on 2007-11-23
In the pass week I just tried to upgrade packages.
Here is result for "cat /var/log/dpkg.log"

.........
2007-11-03 21:52:12 status half-installed vim 1:7.0-035+1ubuntu5.1~dapper1
2007-11-03 21:52:12 status config-files vim 1:7.0-035+1ubuntu5.1~dapper1
2007-11-03 21:52:12 status config-files vim 1:7.0-035+1ubuntu5.1~dapper1
2007-11-03 21:52:13 install libltdl3 <none> 1.5.22-2
2007-11-03 21:52:13 status half-installed libltdl3 1.5.22-2
2007-11-03 21:52:13 status not-installed libltdl3 <none>
2007-11-03 21:52:13 status half-configured sun-java6-doc 6-00-0ubuntu1~dapper1
2007-11-21 03:00:48 upgrade bsdutils 1:2.12r-4ubuntu6 1:2.12r-4ubuntu6.1
2007-11-21 03:00:48 status half-configured bsdutils 1:2.12r-4ubuntu6
2007-11-21 03:00:48 status unpacked bsdutils 1:2.12r-4ubuntu6
2007-11-21 03:00:48 status half-installed bsdutils 1:2.12r-4ubuntu6
2007-11-21 03:00:49 status half-installed bsdutils 1:2.12r-4ubuntu6
2007-11-21 03:00:49 status unpacked bsdutils 1:2.12r-4ubuntu6.1
2007-11-21 03:00:49 status unpacked bsdutils 1:2.12r-4ubuntu6.1
2007-11-21 03:00:49 status unpacked bsdutils 1:2.12r-4ubuntu6.1
2007-11-21 03:00:49 status half-configured bsdutils 1:2.12r-4ubuntu6.1
2007-11-21 03:00:49 status installed bsdutils 1:2.12r-4ubuntu6.1
2007-11-21 03:00:49 upgrade tar 1.15.1-2ubuntu2.1 1.15.1-2ubuntu2.2
2007-11-21 03:00:49 status half-configured tar 1.15.1-2ubuntu2.1
2007-11-21 03:00:49 status unpacked tar 1.15.1-2ubuntu2.1
2007-11-21 03:00:49 status half-installed tar 1.15.1-2ubuntu2.1
2007-11-21 03:00:50 status half-installed tar 1.15.1-2ubuntu2.1
2007-11-21 03:00:50 status unpacked tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:50 status unpacked tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:50 status unpacked tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:50 status unpacked tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:50 status half-configured tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:51 status installed tar 1.15.1-2ubuntu2.2
2007-11-21 03:00:51 status half-configured sun-java6-doc 6-00-0ubuntu1~dapper1
2007-11-21 03:29:50 status half-configured sun-java6-doc 6-00-0ubuntu1~dapper1
2007-11-21 03:32:05 status half-configured sun-java6-doc 6-00-0ubuntu1~dapper1
2007-11-21 03:33:52 status installed sun-java6-doc 6-00-0ubuntu1~dapper1

The only major thing last week I installed second hardisk running windows as IDE master.
The first hardisk running ubuntu move to IDE slave. No dual boot.  

BTW what does Automatix user mean?

---

### Post by xeth_delta on 2007-11-23
Quoting from the net, "Automatix is tool that automates the addition of applications, codecs, fonts and libraries not provided directly by the software repositories of Debian-based distributions".
I really prefer to do those installations myself.

Did you try reconfiguring it?

Xeth

---

### Post by jemmyyong on 2007-11-23
I still failed to install Automatix.

jemmy@jemmy-desktop:~$ sudo dpkg -i automatix2_1.1-4.2-6.06dapper_i386.deb
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing automatix2_1.1-4.2-6.06dapper_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 automatix2_1.1-4.2-6.06dapper_i386.deb

Maybe it's the time to migrate from dapper to Gutsy.

---

### Post by xeth_delta on 2007-11-23
> **jemmyyong said:**
> I still failed to install Automatix.

jemmy@jemmy-desktop:~$ sudo dpkg -i automatix2_1.1-4.2-6.06dapper_i386.deb
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing automatix2_1.1-4.2-6.06dapper_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 automatix2_1.1-4.2-6.06dapper_i386.deb

Maybe it's the time to migrate from dapper to Gutsy.

Oh, I did not suggest to install automatix. I actually would not recommend it right now. Some people have had problems with it (see a previous post I wrote) :) Maybe an automatix user can shed more light on this.

Xeth

---

### Post by Arthur Archnix on 2007-11-23
Looks like you upgraded tar, and now its broken. Try removing it with the --purge option and then reinstalling?

I've never done anything like that before, and its convievable to me that after removing you will not be able to reinsatll (easily).

---

### Post by jemmyyong on 2007-11-23
Could You give the detail how to removing with the --purge option and then reinstalling?

---

### Post by xeth_delta on 2007-11-23
> **jemmyyong said:**
> Could You give the detail how to removing with the --purge option and then reinstalling?

To purge:
```
sudo aptitude purge tar
```

To install yet again:
```
sudo aptitude install tar
```

This last step might fail, in that case try installung the downloaded deb. Remember it has to be for your Ubuntu version

Xeth

---

### Post by Anicka on 2007-11-23
What does the command```
dpkg -C
```give?

---

### Post by jemmyyong on 2007-11-23
jemmy@jemmy-desktop:~$ sudo aptitude purge tar
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  file-roller
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file firefox firefox-gnome-support
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following packages will be REMOVED:
  tar{p}
0 packages upgraded, 0 newly installed, 1 to remove and 164 not upgraded.
Need to get 0B of archives. After unpacking 1827kB will be freed.
The following packages have unmet dependencies:
  file-roller: Depends: tar (>= 1.13.25) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
tar [1.15.1-2ubuntu2.2 (dapper-updates, dapper-security, now) -> 1.15.1-2ubuntu2(dapper)]

Score is 99964

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  tar
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file file-roller firefox
  firefox-gnome-support gedit gedit-common gimp gimp-data gimp-python
  gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 164 not upgraded.
Need to get 519kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main tar 1.15.1-2ubuntu2 [519kB]
Fetched 519kB in 16s (31.6kB/s)
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.15.1-2ubuntu2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.15.1-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by jemmyyong on 2007-11-23
jemmy@jemmy-desktop:~$ sudo dpkg -C
jemmy@jemmy-desktop:~$

---

### Post by xeth_delta on 2007-11-23
There is a broken package:
>   The following packages are BROKEN:
file-roller 

Try purging and reinstalling it. Then an **sudo apt-get autoclean** then **sudo apt-get install -f**

---

### Post by jemmyyong on 2007-11-23
While purge file-roller there is another broken packages "ubuntu-desktop"
> jemmy@jemmy-desktop:~$ sudo aptitude purge file-roller Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  ubuntu-desktop
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file firefox firefox-gnome-support
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following packages will be REMOVED:
  file-roller{p}
0 packages upgraded, 0 newly installed, 1 to remove and 163 not upgraded.
Need to get 0B of archives. After unpacking 4706kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: file-roller but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
file-roller [2.14.2-0ubuntu2 (dapper, now) -> 2.14.4-0ubuntu1 (dapper-updates)]

Score is 1

Accept this solution? [Y/n/q/?] Y
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file firefox firefox-gnome-support
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following packages will be upgraded:
  file-roller
1 packages upgraded, 0 newly installed, 0 to remove and 163 not upgraded.
Need to get 651kB of archives. After unpacking 53.2kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main file-roller 2.14.4-0ubuntu1 [651kB]
Fetched 651kB in 18s (34.4kB/s)
[B]dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/file-roller_2.14.4-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/file-roller_2.14.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]


Then:
> jemmy@jemmy-desktop:~$ sudo aptitude install file-roller
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file firefox firefox-gnome-support
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following packages will be upgraded:
  file-roller
1 packages upgraded, 0 newly installed, 0 to remove and 163 not upgraded.
Need to get 0B/651kB of archives. After unpacking 53.2kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
[B]dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/file-roller_2.14.4-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/file-roller_2.14.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]


Purge ubuntu-desktop:
> jemmy@jemmy-desktop:~$ sudo aptitude purge ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file file-roller firefox
  firefox-gnome-support gedit gedit-common gimp gimp-data gimp-python
  gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following packages will be REMOVED:
  ubuntu-desktop{p}
0 packages upgraded, 0 newly installed, 1 to remove and 164 not upgraded.
Need to get 0B of archives. After unpacking 41.0kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 83177 files and directories currently installed.)
Removing ubuntu-desktop ...
jemmy@jemmy-desktop:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  app-install-data-commercial apt apt-utils bind9-host cpio cupsys
  cupsys-bsd cupsys-client debconf debconf-i18n dnsutils dselect
  dvd+rw-tools evolution-data-server file file-roller firefox
  firefox-gnome-support gedit gedit-common gimp gimp-data gimp-python
  gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-desktop-data gnome-doc-utils gnome-games
  gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-terminal gnome-terminal-data
  gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 hal
  hal-device-manager iptables klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common libbind9-0 libc6 libc6-dev libc6-i686
  libcamel1.2-8 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdns21
  libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libexif12 libflac7
  libfreetype6 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15
  libgtksourceview-common libgtksourceview1.0-0 libhal-storage1 libhal1
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblircclient0
  liblwres9 libmagic1 libmagick9 libmetacity0 libmodplug0c2
  libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libpq4
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libssl-dev
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 linux-image-2.6.15-28-386
  linux-restricted-modules-2.6.15-28-386 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  poppler-utils samba-common smbclient synaptic tk8.4 udev update-manager
  util-linux vim-runtime vlc vlc-plugin-alsa wxvlc xscreensaver-data
  xscreensaver-gl xserver-xorg-core
The following NEW packages will be installed:
  ubuntu-desktop
0 packages upgraded, 1 newly installed, 0 to remove and 164 not upgraded.
Need to get 13.9kB of archives. After unpacking 41.0kB will be used.
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main ubuntu-desktop 0.120 [13.9kB]
Fetched 13.9kB in 2s (6294B/s)
[B]dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/ubuntu-desktop_0.120_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-desktop_0.120_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]


All package failed to install..

---

### Post by Arthur Archnix on 2007-11-23
Is a clean install of gutsy a viable option for you?

---

### Post by xeth_delta on 2007-11-23
Please do not remove ubuntu-desktop. It is an important package.
Right now I am out of ideas, sorry. What happened with **dpkg-reconfigure dpkg**?

Xeth

---

### Post by Arthur Archnix on 2007-11-23
Ubuntu desktop is just a meta-package. The only harm that comes from removing it is that you won't be able to update to the next version of ubuntu. Not really a concern when apt is apparently busted. I too am out of ideas., and the stuff I've seen online involves manual editing of apts config files. Not something I'd ever try myself. 

I hope you find your answer, but if this were me, I'd back up my files and get set for a clean install.

---

### Post by xeth_delta on 2007-11-23
> **Arthur Archnix said:**
> Ubuntu desktop is just a meta-package. The only harm that comes from removing it is that you won't be able to update to the next version of ubuntu.

I stand corrected :) 

> I hope you find your answer, but if this were me, I'd back up my files and get set for a clean install.

I agree, that's the only thing I can suggest right now, too.

Good luck and let us know of the progress,

Xeth

---

### Post by jemmyyong on 2007-11-23
Nothing hapenned with dpkg-reconfigure dpkg
> 
jemmy@jemmy-desktop:~$ sudo dpkg-reconfigure dpkg
jemmy@jemmy-desktop:~$


I am backing up my data and ready for clean install of Gutsy.

Thanks for all of your helps Arthur & Xeth


Regards
Jemmyyong

---

