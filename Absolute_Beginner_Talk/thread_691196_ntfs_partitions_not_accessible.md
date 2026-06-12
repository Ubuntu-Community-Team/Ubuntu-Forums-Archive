---
title: "ntfs partitions not accessible"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by shashank86 on 2008-02-08
Hi
I am on kubuntu 6.06. As of now i have managed to mount my windows partitions and change permissions on it. But when i try to access media files on those partitions i get this exact error

Could not enter folder /media/datapartition1.

I am using the players loaded by default i.e Amarok , Kaffeine.
Can something be done about this???
Thanks.

---

### Post by PmDematagoda on 2008-02-08
Did you install the ntfs-3g packages? Also, are you able to completely read and write to the NTFS drives?

---

### Post by hyper_ch on 2008-02-08
ntfs-3g was already available in Dapper?

---

### Post by shashank86 on 2008-02-08
no i have not installed any package... i am not able to access the drives at all.. the whole thing is mounted and when i change the permissions all the files on the drive is listed.. thats about it...

---

### Post by hyper_ch on 2008-02-08
well, you have read access only. Amarok needs write accdes - in case you want to modify the files. So you will have to get somehow ntfs-3g to gain write access.

---

### Post by PmDematagoda on 2008-02-08
> **hyper_ch said:**
> ntfs-3g was already available in Dapper?

No, it was not built-in until Ubuntu 7.10.

Install ntfs-3g using:-
```
sudo apt-get install ntfs-3g ntfs-config
```

Then open the NTFS configurator found in Applications>System Tools>NTFS Configuration Tool and enable all the choices. Then reboot your PC and see if your problem is solved.

---

### Post by shashank86 on 2008-02-08
can i not specify write permissions from the terminal itself without the package??? i ask this because i do not know how to install yet!!!!!!!!!!!!

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> can i not specify write permissions from the terminal itself without the package??? i ask this because i do not know how to install yet!!!!!!!!!!!!

You can, but trying to do that would take a lot more time  than would be needed to know how to install the packages and also would be much less reliable.

---

### Post by shashank86 on 2008-02-08
> **PmDematagoda said:**
> No, it was not built-in until Ubuntu 7.10.

Install ntfs-3g using:-
```
sudo apt-get install ntfs-3g ntfs-config
```

Then open the NTFS configurator found in Applications>System Tools>NTFS Configuration Tool and enable all the choices. Then reboot your PC and see if your problem is solved.

thanks man... will try it out... 
be back after ten mins... have to have some food...

---

### Post by shashank86 on 2008-02-08
Package not found..
```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

---

### Post by shashank86 on 2008-02-08
guys are you still there???

---

### Post by PmDematagoda on 2008-02-08
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by shashank86 on 2008-02-08
```

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://in.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://in.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://in.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> guys are you still there???

Please be patient, sometimes it takes a bit of time for us to make our reply and also we may want to clarify certain things

Speaking about "clarifying certain things", I just looked for ntfs-3g in Ubuntu Packages and it seems that the ntfs-3g package was not introduced to Dapper, in which case you may have to get ntfs-3g from a different version of Ubuntu such as [Edgy]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ntfs-3g&searchon=names&subword=1&version=edgy&release=all") or [Feisty]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ntfs-3g&searchon=names&subword=1&version=feisty&release=all"), but **_be careful_** with this since it may cause some problems on your system.

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> ```

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://in.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://in.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://in.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

It also seems that your repositories are improperly configured which may cause some problems, especially concerning updates. Set the repositories the way you want in Software Sources found in System>Administration>Software Sources.

---

### Post by shashank86 on 2008-02-08
Hey no problem man... will wait as long as it takes... just wanted to know that you guys were still there thats it...

What do i do with the new versions????

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> Hey no problem man... will wait as long as it takes... just wanted to know that you guys were still there thats it...

What do i do with the new versions????

Just download the .deb file and double click on it to start the installation, if you face any errors, post them here.

---

### Post by shashank86 on 2008-02-08
How do i set the repositories??? there is a package manager called adept.. is that the one you are talking about???

---

### Post by shashank86 on 2008-02-08
i get the error
```

The utility is not in your PATH.
Please install it or contact your system administrator.

```
And a blank page opens....

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> i get the error
```

The utility is not in your PATH.
Please install it or contact your system administrator.

```
And a blank page opens....

Where does this occur? In Adept or when trying to install ntfs-3g?

---

### Post by shashank86 on 2008-02-08
while i double click on the .deb file... i have closed adept.. did not understand a thing in that....

---

### Post by shashank86 on 2008-02-08
the same thing for all the versions of edgy... will give feisty a try now...

---

### Post by PmDematagoda on 2008-02-08
From the error you get, I think it would be just a waste of time. But I may be wrong, if you wait then someone could post a better solution to your problem.

---

### Post by shashank86 on 2008-02-08
no use man... fiesty files are throwing up the same error....

---

### Post by shashank86 on 2008-02-08
you think so??? that waiting will get a better solution??? coz once the thread goes cold not many look at it....

---

### Post by hyper_ch on 2008-02-08
For your repos:

(1) make a backup
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

```

(2) Open it
```

gksu gedit /etc/apt/sources.list

```

(3) replace the content with

```

deb http://in.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

(4) Update the packages list
```

sudo apt-get update

```

(5) Upgrade the system
```

sudo apt-get upgrade

```
DO NOT UPGRADE BUT DO POST THE OUTPUT OF IT!

That should at least fix now the sources.list

---

### Post by shashank86 on 2008-02-08
> **hyper_ch said:**
> 

(4) Update the packages list
```

sudo apt-get update

```

(5) Upgrade the system
```

sudo apt-get upgrade

```
DO NOT UPGRADE BUT DO POST THE OUTPUT OF IT!

That should at least fix now the sources.list
are not these two the same?

---

### Post by shashank86 on 2008-02-08
sorry... my bad... read upgrade as update....
will do that...

---

### Post by shashank86 on 2008-02-08
here is the o/p of the get update
```


Get:2 http://in.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://in.archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:4 http://in.archive.ubuntu.com dapper Release [34.8kB]
Get:5 http://in.archive.ubuntu.com dapper-updates Release [50.9kB]
Get:6 http://in.archive.ubuntu.com dapper-backports Release [38.4kB]
Get:7 http://in.archive.ubuntu.com dapper/main Packages [619kB]
Get:8 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:9 http://security.ubuntu.com dapper-security Release [50.9kB]
Get:10 http://in.archive.ubuntu.com dapper/restricted Packages [4571B]
Get:11 http://in.archive.ubuntu.com dapper/universe Packages [2458kB]
Get:12 http://security.ubuntu.com dapper-security/main Packages [140kB]
Get:13 http://security.ubuntu.com dapper-security/restricted Packages [7842B]
Get:14 http://security.ubuntu.com dapper-security/universe Packages [91.5kB]
Get:15 http://security.ubuntu.com dapper-security/multiverse Packages [8162B]
Get:16 http://in.archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get:17 http://in.archive.ubuntu.com dapper-updates/main Packages [265kB]
Get:18 http://in.archive.ubuntu.com dapper-updates/restricted Packages [6378B]
Get:19 http://in.archive.ubuntu.com dapper-updates/universe Packages [105kB]
Get:20 http://in.archive.ubuntu.com dapper-updates/multiverse Packages [11.2kB]
Get:21 http://in.archive.ubuntu.com dapper-backports/main Packages [19.8kB]
Get:22 http://in.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:23 http://in.archive.ubuntu.com dapper-backports/universe Packages [61.7kB]
Get:24 http://in.archive.ubuntu.com dapper-backports/multiverse Packages [12.2kB]
Fetched 4081kB in 2m51s (23.8kB/s)
Reading package lists... Done

```
Should i go with the upgrade???

---

### Post by shashank86 on 2008-02-08
here is the o/p of the upgrade line
```


Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amarok amarok-xine kopete linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  acpi-support adept app-install-data apt apt-utils base-files bind9-host
  binutils-static bsdutils cpio cupsys cupsys-bsd cupsys-client dbus debconf
  debconf-i18n dnsutils dpkg dselect dvd+rw-tools e2fslibs e2fsprogs file
  gnupg gzip hal imagemagick info initramfs-tools iptables k3b kate kcontrol
  kde-guidance kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-bin
  kdelibs-data kdelibs4c2a kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdeprint kdesktop kdm kdnssd kfind khelpcenter kicker klipper
  klogd kmenuedit koffice-data koffice-libs konqueror konqueror-nsplugins
  konsole konversation kpf kppp krdc krfb krita krita-data ksmserver ksplash
  ksysguard ksysguardd ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-desktop kubuntu-docs kwin language-pack-en
  language-pack-en-base language-pack-kde-en language-pack-kde-en-base
  language-selector-common language-selector-qt libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-qt3-1 libbind9-0 libblkid1
  libc6 libc6-i686 libcairo2 libcomerr2 libcupsimage2 libcupsys2 libcurl3
  libcurl3-gnutls libdbus-1-2 libdbus-glib-1-2 libdbus-qt-1-1c2 libdns21
  libexif12 libflac++5c2 libflac7 libfreetype6 libgd2-noxpm libgeoip1
  libglib2.0-0 libgnutls12 libgpgme11 libgstreamer-plugins-base0.10-0
  libhal-storage1 libhal1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1
  libk3b2 libkonq4 libkrb53 liblwres9 libmagic1 libmagick9 libmodplug0c2
  libmusicbrainz4c2a libmysqlclient15off libnspr4 libnss3 liboggflac3 libpcre3
  libperl5.8 libpng12-0 libpoppler1 libpoppler1-qt libpq4 libqt3-mt libruby1.8
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libss2 libssl0.9.8
  libtag1c2a libtheora0 libtiff4 libtunepimp2c2a libuuid1 libvorbis0a
  libvorbisenc2 libvorbisfile3 libwpd8c2a libx11-6 libxfont1 libxine-main1
  libxml2 linux-386 linux-restricted-modules-common locales login lvm2 mount
  mysql-common openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  openssh-client openssl passwd pcmcia-cs perl perl-base perl-modules
  perl-suid pmount poppler-utils popularity-contest ppp python-apt
  python-pyorbit python-uno python2.4 python2.4-apt python2.4-dbus
  python2.4-dev python2.4-examples python2.4-gdbm python2.4-libxml2
  python2.4-minimal python2.4-pyorbit python2.4-tk readahead rsync
  samba-common screen slocate smbclient sysklogd tar tcpdump tk8.4
  ttf-opensymbol ubuntu-base ubuntu-minimal ubuntu-standard udev util-linux
  vim vim-common vim-runtime w3m wpasupplicant xinit xserver-xorg-core
  xserver-xorg-input-mouse
224 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 259MB of archives.
After unpacking 35.5MB of additional disk space will be used.
Do you want to continue [Y/n]?    

```

---

### Post by shashank86 on 2008-02-08
will hit the sack now... thanks for the help....

---

### Post by hyper_ch on 2008-02-08
you could directly run the dist-upgrade:

```

sudo apt-get dist-upgrade

```

you'll get new kernel and stuff...

---

### Post by PmDematagoda on 2008-02-08
> **hyper_ch said:**
> you could directly run the dist-upgrade:

```

sudo apt-get dist-upgrade

```

you'll get new kernel and stuff...

But be warned that doing an upgrade could cause problems and there have been rare occasions where the entire system was rendered useless.

If you do want to do an upgrade, please **backup** all your important files and data before doing so.

---

### Post by shashank86 on 2008-02-08
do you mean that if i go in for the dist upgrade then even my windows files will be affected???

---

### Post by ispy on 2008-02-08
Probably not, if they are partitioned on another separate primary partition. if they're on a logical partition within the Ubuntu partition, that might happen, but is very unlikely.

what kind of machine do you have?
(year, brand, HDD, RAM, etc...)

---

### Post by shashank86 on 2008-02-08
Processor: P4 2.66 ghz
Motherboard: asrok 915 gl
HDD 80gb seagate sata
ram: 256mb ddr1

---

### Post by ispy on 2008-02-08
which OS did you install first?

Windows or Ubuntu?

---

### Post by PmDematagoda on 2008-02-08
> **shashank86 said:**
> 
ram: 256mb ddr1
I rather doubt if the upgrade would be healthy when you consider the amount of RAM, this is because Ubuntu 7.04 and above requires about 384Mb of RAM minimum and your RAM is below this number, if you do upgrade you may have to think of using a lighter DE(Desktop Environment) such as XFCE or Fluxbox.

---

### Post by RussellGee on 2008-02-08
EDIT: Sry nvm

---

### Post by shashank86 on 2008-02-08
> **ispy said:**
> which OS did you install first?

Windows or Ubuntu?

Windows... that is still my main OS... i shifted to kubuntu only around a week back...

> **PmDematagoda said:**
> I rather doubt if the upgrade would be healthy when you consider the amount of RAM, this is because Ubuntu 7.04 and above requires about 384Mb of RAM minimum and your RAM is below this number, if you do upgrade you may have to think of using a lighter DE(Desktop Environment) such as XFCE or Fluxbox.

you mean to say that i remove the whole of kubuntu and then install fluxbox

> **RussellGee said:**
> EDIT: Sry nvm

what is this for mate???

---

### Post by PmDematagoda on 2008-02-08
> you mean to say that i remove the whole of kubuntu and then install fluxbox
I am afraid that is the case, Kubuntu 7.04(and above) may be too resource-heavy for your current amount of RAM. Try using Xubuntu or Fluxbox instead.

---

### Post by shashank86 on 2008-02-08
will do that man.... thanks for everything... :)

---

