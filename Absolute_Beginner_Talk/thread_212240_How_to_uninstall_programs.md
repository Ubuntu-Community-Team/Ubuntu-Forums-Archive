---
title: "How to uninstall programs?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-09
Hi, I have Wallpapoz (listed under Applications-Accesories) and SMC [Secret Maryo Chronicals] (liisted under Applications-Games) and I want to uninstall them but I don't know how. When I installed SMC this is how the terminal looked:
```
gino@gino-laptop:~$ sudo su
Password:
root@gino-laptop:/home/gino# cd /root
root@gino-laptop:~# wget -N http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_install.sh
--15:01:39--  http://patrick295767.sitesled.com/easyscripts_installers/easy_smc_patrick_install.sh
           => `easy_smc_patrick_install.sh'
Resolving patrick295767.sitesled.com... 216.198.209.150
Connecting to patrick295767.sitesled.com|216.198.209.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,136 (1.1K) [application/x-sh]

100%[====================================>] 1,136         --.--K/s

15:01:40 (67.71 MB/s) - `easy_smc_patrick_install.sh' saved [1136/1136]

root@gino-laptop:~# sh easy_smc_patrick_install.sh

================================================
= Patrick Easy Install: Super Maryo Chronicles =
================================================

mkdir: cannot create directory `/root': File exists
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:5 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Get:6 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper/universe Packages
Get:7 http://us.archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:8 http://us.archive.ubuntu.com dapper-backports Release [19.6kB]
Get:9 http://security.ubuntu.com dapper-security/main Packages [27.4kB]
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Get:10 http://us.archive.ubuntu.com dapper-updates/main Packages [41.9kB]
Get:11 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:12 http://us.archive.ubuntu.com dapper-updates/main Sources [24.5kB]
Get:13 http://security.ubuntu.com dapper-security/restricted Packages [4253B]
Get:14 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:15 http://us.archive.ubuntu.com dapper-backports/main Packages [14B]
Get:16 http://us.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:17 http://us.archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:18 http://us.archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:19 http://security.ubuntu.com dapper-security/main Sources [7105B]
Get:20 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:21 http://security.ubuntu.com dapper-security/universe Packages [6042B]
Get:22 http://us.archive.ubuntu.com dapper-backports/main Sources [14B]
Get:23 http://us.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:24 http://us.archive.ubuntu.com dapper-backports/universe Sources [14B]
Get:25 http://us.archive.ubuntu.com dapper-backports/multiverse Sources [14B]
Get:26 http://security.ubuntu.com dapper-security/universe Sources [902B]
Fetched 195kB in 3s (58.7kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  debconf-utils debhelper html2text libbeecrypt6 librpm4 rpm
Suggested packages:
  lsb-rpm lintian dh-make
The following NEW packages will be installed:
  alien debconf-utils debhelper html2text libbeecrypt6 librpm4 rpm
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2387kB of archives.
After unpacking 7913kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main html2text 1.3.2a-3 [95.5kB]
Get:2 http://archive.ubuntu.com dapper/main debconf-utils 1.4.72ubuntu9 [30.9kB]Get:3 http://archive.ubuntu.com dapper/main debhelper 5.0.7ubuntu13 [506kB]
Get:4 http://archive.ubuntu.com dapper/main libbeecrypt6 4.1.2-4 [121kB]
Get:5 http://archive.ubuntu.com dapper/main librpm4 4.4.1-5ubuntu2 [933kB]
Get:6 http://archive.ubuntu.com dapper/main rpm 4.4.1-5ubuntu2 [597kB]
Get:7 http://archive.ubuntu.com dapper/main alien 8.64 [104kB]
Fetched 2387kB in 30s (79.1kB/s)
Selecting previously deselected package html2text.
(Reading database ... 98627 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.72ubuntu9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.7ubuntu13_all.deb) ...
Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-4_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.64_all.deb) ...
Setting up html2text (1.3.2a-3) ...

Setting up debconf-utils (1.4.72ubuntu9) ...

Setting up debhelper (5.0.7ubuntu13) ...
Setting up libbeecrypt6 (4.1.2-4) ...

Setting up librpm4 (4.4.1-5ubuntu2) ...

Setting up rpm (4.4.1-5ubuntu2) ...

Setting up alien (8.64) ...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libaa1-dev libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev
  libesd0-dev libgl1-mesa-dev libglu1-mesa-dev libice-dev libncurses5-dev
  libslang2-dev libsm-dev libxt-dev mesa-common-dev
Suggested packages:
  libasound2-doc
The following NEW packages will be installed:
  libaa1-dev libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev
  libesd0-dev libgl1-mesa-dev libglu1-mesa-dev libice-dev libncurses5-dev
  libsdl1.2-dev libslang2-dev libsm-dev libxt-dev mesa-common-dev
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 4805kB of archives.
After unpacking 19.5MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main libice-dev 2:1.0.0-0ubuntu2 [49.1kB]Get:2 http://archive.ubuntu.com dapper/main libsm-dev 2:1.0.0-0ubuntu2 [19.2kB]
Get:3 http://archive.ubuntu.com dapper/main libxt-dev 1:1.0.0-0ubuntu3 [466kB]
Get:4 http://archive.ubuntu.com dapper/main libslang2-dev 2.0.5-1build2 [439kB]
Get:5 http://archive.ubuntu.com dapper/main libncurses5-dev 5.5-1ubuntu3 [1307kB]
Get:6 http://archive.ubuntu.com dapper/main libaa1-dev 1.4p5-30 [138kB]
Get:7 http://archive.ubuntu.com dapper/main libartsc0-dev 1.5.2-0ubuntu1 [21.3kB]
Get:8 http://archive.ubuntu.com dapper/main libasound2-dev 1.0.10-2ubuntu4 [454kB]
Get:9 http://archive.ubuntu.com dapper/main libaudiofile-dev 0.2.6-6ubuntu1 [112kB]
Get:10 http://archive.ubuntu.com dapper/main libesd0-dev 0.2.36-3ubuntu3 [22.8kB]
Get:11 http://archive.ubuntu.com dapper/main mesa-common-dev 6.4.1-0ubuntu8 [167kB]
Get:12 http://archive.ubuntu.com dapper/main libgl1-mesa-dev 6.4.1-0ubuntu8 [46.0kB]
Get:13 http://archive.ubuntu.com dapper/main libglu1-mesa-dev 6.4.1-0ubuntu8 [255kB]
Get:14 http://archive.ubuntu.com dapper/main libaudio-dev 1.7-3ubuntu3 [484kB]
Get:15 http://archive.ubuntu.com dapper/main libsdl1.2-dev 1.2.9-0.0ubuntu2 [825kB]
Fetched 4805kB in 57s (83.3kB/s)
Selecting previously deselected package libice-dev.
(Reading database ... 99135 files and directories currently installed.)
Unpacking libice-dev (from .../libice-dev_2%3a1.0.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libslang2-dev.
Unpacking libslang2-dev (from .../libslang2-dev_2.0.5-1build2_i386.deb) ...
Selecting previously deselected package libncurses5-dev.
Unpacking libncurses5-dev (from .../libncurses5-dev_5.5-1ubuntu3_i386.deb) ...
Selecting previously deselected package libaa1-dev.
Unpacking libaa1-dev (from .../libaa1-dev_1.4p5-30_i386.deb) ...
Selecting previously deselected package libartsc0-dev.
Unpacking libartsc0-dev (from .../libartsc0-dev_1.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libasound2-dev.
Unpacking libasound2-dev (from .../libasound2-dev_1.0.10-2ubuntu4_i386.deb) ...
Selecting previously deselected package libaudiofile-dev.
Unpacking libaudiofile-dev (from .../libaudiofile-dev_0.2.6-6ubuntu1_i386.deb) ...
Selecting previously deselected package libesd0-dev.
Unpacking libesd0-dev (from .../libesd0-dev_0.2.36-3ubuntu3_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.4.1-0ubuntu8_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.4.1-0ubuntu8_i386.deb) ...Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.4.1-0ubuntu8_i386.deb) ...
Selecting previously deselected package libaudio-dev.
Unpacking libaudio-dev (from .../libaudio-dev_1.7-3ubuntu3_i386.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.9-0.0ubuntu2_i386.deb) ...
Setting up libice-dev (1.0.0-0ubuntu2) ...
Setting up libsm-dev (1.0.0-0ubuntu2) ...
Setting up libxt-dev (1.0.0-0ubuntu3) ...
Setting up libslang2-dev (2.0.5-1build2) ...
Setting up libncurses5-dev (5.5-1ubuntu3) ...
Setting up libaa1-dev (1.4p5-30) ...

Setting up libartsc0-dev (1.5.2-0ubuntu1) ...
Setting up libasound2-dev (1.0.10-2ubuntu4) ...

Setting up libaudiofile-dev (0.2.6-6ubuntu1) ...
Setting up libesd0-dev (0.2.36-3ubuntu3) ...
Setting up mesa-common-dev (6.4.1-0ubuntu8) ...
Setting up libgl1-mesa-dev (6.4.1-0ubuntu8) ...
Setting up libglu1-mesa-dev (6.4.1-0ubuntu8) ...
Setting up libaudio-dev (1.7-3ubuntu3) ...
Setting up libsdl1.2-dev (1.2.9-0.0ubuntu2) ...

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libjpeg62-dev libsdl-image1.2 libtiff4-dev libtiffxx0c2
The following NEW packages will be installed:
  libjpeg62-dev libsdl-image1.2 libsdl-image1.2-dev libtiff4-dev libtiffxx0c2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 543kB of archives.
After unpacking 1536kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main libjpeg62-dev 6b-11 [185kB]
Get:2 http://security.ubuntu.com dapper-security/main libtiffxx0c2 3.7.4-1ubuntu3.1 [44.0kB]
Get:3 http://security.ubuntu.com dapper-security/main libtiff4-dev 3.7.4-1ubuntu3.1 [258kB]
Get:4 http://archive.ubuntu.com dapper/main libsdl-image1.2 1.2.4-1 [25.7kB]
Get:5 http://archive.ubuntu.com dapper/main libsdl-image1.2-dev 1.2.4-1 [30.7kB]Fetched 543kB in 6s (85.4kB/s)
Selecting previously deselected package libjpeg62-dev.
(Reading database ... 101304 files and directories currently installed.)
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-11_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.4-1_i386.deb) ...
Selecting previously deselected package libtiffxx0c2.
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.7.4-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.7.4-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2-dev.
Unpacking libsdl-image1.2-dev (from .../libsdl-image1.2-dev_1.2.4-1_i386.deb) ...
Setting up libjpeg62-dev (6b-11) ...
Setting up libsdl-image1.2 (1.2.4-1) ...

Setting up libtiffxx0c2 (3.7.4-1ubuntu3.1) ...

Setting up libtiff4-dev (3.7.4-1ubuntu3.1) ...

Setting up libsdl-image1.2-dev (1.2.4-1) ...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libsdl-gfx1.2-4
The following NEW packages will be installed:
  libsdl-gfx1.2-4 libsdl-gfx1.2-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 438kB of archives.
After unpacking 791kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/universe libsdl-gfx1.2-4 2.0.13-1 [39.7kB]
Get:2 http://archive.ubuntu.com dapper/universe libsdl-gfx1.2-dev 2.0.13-1 [398kB]
Fetched 438kB in 5s (82.7kB/s)
Selecting previously deselected package libsdl-gfx1.2-4.
(Reading database ... 101406 files and directories currently installed.)
Unpacking libsdl-gfx1.2-4 (from .../libsdl-gfx1.2-4_2.0.13-1_i386.deb) ...
Selecting previously deselected package libsdl-gfx1.2-dev.
Unpacking libsdl-gfx1.2-dev (from .../libsdl-gfx1.2-dev_2.0.13-1_i386.deb) ...
Setting up libsdl-gfx1.2-4 (2.0.13-1) ...

Setting up libsdl-gfx1.2-dev (2.0.13-1) ...
Reading package lists... Done
Building dependency tree... Done
Package libsdl-gfx1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl-gfx1.2-dev
E: Package libsdl-gfx1.2 has no installation candidate
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--15:03:58--  http://superb-west.dl.sourceforge.net/sourceforge/smclone/smc-0.96-jdsrX.4.i386.rpm
           => `smc-0.96-jdsrX.4.i386.rpm'
Resolving superb-west.dl.sourceforge.net... 209.160.59.253
Connecting to superb-west.dl.sourceforge.net|209.160.59.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,586,223 (6.3M) [application/x-redhat-package-manager]

100%[====================================>] 6,586,223     88.48K/s    ETA 00:00

15:05:12 (87.09 KB/s) - `smc-0.96-jdsrX.4.i386.rpm' saved [6586223/6586223]

 Installing via alien ...
Warning: Skipping conversion of scripts in package smc: postinst
Warning: Use the --scripts parameter to include the scripts.
 Installation done.
smc: /usr/games/smc /usr/games/smc.x /usr/local/bin/smc.x
 Sun Jul  9 15:05:34 EDT 2006: You just need to type into the console either:
 smc
 or :
 smc.x
 to run the game

 Enjoy !!

```

I don't have the other terminal but I got the instructions from [here.]("http://www.ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz")

Thanks for your help!

---

### Post by GStubbs43 on 2006-07-09
There is also a wallpapoz-0.2 folder on the desktop that I can't delete. Does anyone know how to do these things?:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by Kilz on 2006-07-09
> **GStubbs43 said:**
> There is also a wallpapoz-0.2 folder on the desktop that I can't delete. Does anyone know how to do these things?:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:
To remove the folder
```
sudo rm -fdr ~/Desktop/wallpapoz-0.2
```

To uninstall the programs go to System > Administration > Synaptic
Search for the programs, click on them, and chose remove.

---

### Post by GStubbs43 on 2006-07-09
> **Kilz said:**
> To remove the folder
```
sudo rm -fdr ~/Desktop/wallpapoz-0.2
```

All right... 1/3 down 2 left...

Oh... and I hope that didn't mess up my uninstallation of wallpapoz. [-o<

I didn't see them in synaptic... I'll look again.

---

### Post by GStubbs43 on 2006-07-09
SMC is *gone* But Wallpapoz wasn't listed. :(

---

### Post by RaZer0r on 2006-07-09
and
```
sudo dpkg -r Wallpapoz
```
??

---

### Post by GStubbs43 on 2006-07-09
[quote=RaZer0r]and
```
sudo dpkg -r Wallpapoz
```
??[/quote]

```
gino@gino-laptop:~$ sudo dpkg -r Wallpapoz
Password:
dpkg - warning: ignoring request to remove wallpapoz which isn't installed.
gino@gino-laptop:~$

```

But it *is* under Applications-Accesories

---

### Post by GStubbs43 on 2006-07-09
Anyone else have an idea... or am I stuck with it?

---

### Post by merinda on 2006-07-25
Hi,

Remember when you try to install wallpapoz by doing something like this: python install.py install

The install script can uninstall too
Try doing this:
sudo python install.py uninstall

Tell me if it's not work.

---

### Post by Rome.konig on 2008-02-03
im having a hard time unistalling wallpapoz, 

but the was i got rid of the wallpapoz icon under my accessories screen, by was going to applications/[preferences/Main menu. i unceck the wallpapoz icon and pressed closed. 

the way how i deleted wallpapoz was using a gnome-opener launcher to delete the folders

---

