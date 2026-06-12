---
title: "[SOLVED] is there a list of programs avavile to d/l with the extra sources lines to a"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-18
is there somewhere on the net where a list of exptra programs are available to d/l for Ubuntu and the extra source code lines you need to install to the sources list make d/l and install them

---

### Post by Hobo Joe on 2007-07-18
Synaptic package manager.

It's loaded with all the programs you could want and more.

---

### Post by pyros on 2007-07-18
> **stinger30au said:**
> is there somewhere on the net where a list of exptra programs are available to d/l for Ubuntu and the extra source code lines you need to install to the sources list make d/l and install them

not a universal one, no. anyone can create a repository.

---

### Post by stinger30au on 2007-07-18
> **Hobo Joe said:**
> Synaptic package manager.

It's loaded with all the programs you could want and more.

thats what i thought, but i have been reading some posts here and there is extra programs you can add if you add extra lines.

i have found these goodies
[http://www.debianadmin.com/adding-ubuntu-repositories.html](http://www.debianadmin.com/adding-ubuntu-repositories.html)

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by stinger30au on 2007-07-18
this is something like what i was looking for

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by pyros on 2007-07-18
> **stinger30au said:**
> this is something like what i was looking for

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Yes, but it is the same program list as synaptic will give you.

---

### Post by stinger30au on 2007-07-19
is is another handy site i found with groovy repos on it

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/)

how many more sites are there like this??mabe a web site may already be setup with these sorts of links in it already

---

### Post by pyros on 2007-07-19
It seems to me that google is your best bet at this point. for example, searching for the words feisty and repository.

---

### Post by stinger30au on 2007-07-19
> **pyros said:**
> It seems to me that google is your best bet at this point. for example, searching for the words feisty and repository.

excellent advise. id did that.even went looking to see if there is a central web place with links and nothing available, so i created one a wiki


[http://en.wikipedia.org/wiki/Ubuntu_repository](http://en.wikipedia.org/wiki/Ubuntu_repository)

---

### Post by stinger30au on 2007-07-19
well it did not take long for that to be ripped down from the wiki

---

### Post by Tomosaur on 2007-07-19
> **stinger30au said:**
> well it did not take long for that to be ripped down from the wiki

You should add it to the actual Ubuntu documentation wiki, not Wikipedia :P

---

### Post by stinger30au on 2007-07-19
where is the ubuntu wiki??

If your like me and moving from Windows XP to Ubuntu this info below is very handy to have


here is a start of extra repos i have been gathering.now i have started to put this together im finding how amazingly easy it is to work with ubuntu

im amazed theres nothing like this already
if you know of extras please post them here.
maybe an admin may be so kind to step in and help out and perhaps move this info to a sticky perhaps

---------------------------------------------------------------------------------------------------------------------------
before editing the sources.list file back it up first like this
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

then edit it with this
 sudo gedit /etc/apt/sources.list
---------------------------------------------------------------------------------------------------------------------------
get a good terminal program use this
sudo apt-get install xfce4-terminal
---------------------------------------------------------------------------------------------------------------------------
if you need a ram disk, dont stress, it come with one built in
 Re: Setting up a ramdisk
Ubuntu and Debian auto-mount a ramdisk using tmpfs. This gets mounted to /dev/shm and is usable by anyone (just cd to /dev/shm and start plonking files in there).

the ram disk is dynamic, not static (resizes automatically and will use up to half your available ram)
---------------------------------------------------------------------------------------------------------------------------

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0


Authenticated packages
Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is DD800CD9. You can enter this key into the APT trusted keys database with the following command:

    wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -


[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/)


if you liked video maker under xp pro, get this utility
kdenlive
---------------------------------------------------------------------------------------------------------------------------
[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

Import signing key into APT

Signing is available to ensure that you download packages I really made myself
The key finger print is :

0DDB 9651 40FC 8BBD 31F9 98D3 8CC6 8B39 7E2E 4741

You have to download the Morgoth signing key, import it into APT trusted repositories database by issuing the following command in a shell (terminal) :

wget -O - [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc) | sudo apt-key add -
Add this repository to your sources list

To add this repository to your « /etc/apt/sources.list », append this line :

deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

If you also wish to access the Source packages, append this line too :

deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main 

---------------------------------------------------------------------------------------------------------------------------

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

Component thunderbird

Thunderbird 2 feisty backport

You can use apt to download and install the packages. Use the following lines in /etc/apt/sources.list and use the command sudo apt-get update to enable downloading from this component.

Don't forget to read the notice on the frontpage!
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird 

also make sure to add the sidebar addon
[https://addons.mozilla.org/en-US/thunderbird/addon/70](https://addons.mozilla.org/en-US/thunderbird/addon/70)

add a pretty colour scheme to it as well
[https://addons.mozilla.org/en-US/thunderbird/addon/891](https://addons.mozilla.org/en-US/thunderbird/addon/891)


---------------------------------------------------------------------------------------------------------------------------
[http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)

The qBittorrent project was created in March 2006 with the idea of developping a new Bittorrent client for Linux (and possibly other systems) that would be easy to use, good looking, featureful but lightweight.

Ubuntu packages (i386 only)
Ubuntu

We packaged qBittorrent and libtorrent for Ubuntu for easy install. Please add the following lines to your /etc/apt/sources.list if you are using Ubuntu Feisty (v7.04 - stable) or Ubuntu Gutsy (v7.10 - unstable - BROKEN):

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./

Ubuntu Edgy (v6.10) packages are still available here but outdated:

deb [http://hydr0g3n.free.fr/qbittorrent/edgy/](http://hydr0g3n.free.fr/qbittorrent/edgy/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/edgy/](http://hydr0g3n.free.fr/qbittorrent/edgy/) ./

Then, you can install qBittorrent using your favourite packet manager (synaptic, adept...) or you can type this in a console:

sudo apt-get update && sudo apt-get install qbittorrent


---------------------------------------------------------------------------------------------------------------------------

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)  (install pages)
if your dvd drive is new you may need to set the region code, follow this link
[http://linvdr.org/projects/regionset/](http://linvdr.org/projects/regionset/)

    *
          o
                + amarok
                      # amarok-engines  1.4.5-0ubuntu7+medibuntu1
                      # amarok-engines  1.4.5-0ubuntu7+medibuntu1
                      # amarok-engines  1.4.5-0ubuntu7+medibuntu1
                      # amarok-xine  1.4.5-0ubuntu7+medibuntu1
                      # amarok-xine  1.4.5-0ubuntu7+medibuntu1
                      # amarok-xine  1.4.5-0ubuntu7+medibuntu1
                      # amarok  1.4.5-0ubuntu7+medibuntu1
                      # amarok  1.4.5-0ubuntu7+medibuntu1
                      # amarok  1.4.5-0ubuntu7+medibuntu1
          o b
                + bmp-wma
                      # bmp-wma  1.0.5-1medibuntu3
          o f
                + ffmpeg
                      # ffmpeg  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # ffmpeg  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # ffmpeg  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavcodec0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libavformat0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc-dev  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc0d  0.cvs20060823-3.1ubuntu4+medibuntu2
                      # libpostproc0d  0.cvs20060823-3.1ubuntu4+medibuntu2
          o h
                + hot-babe
                      # hot-babe  0.2.2-3medibuntu1+b1
                      # hot-babe  0.2.2-3medibuntu1+b1
                      # hot-babe  0.2.2-3medibuntu1+b1
                      # hot-babe  0.2.2-3medibuntu1
                      # hot-babe  0.2.2-3medibuntu1
                      # hot-babe  0.2.2-3medibuntu1
                      # hot-babe  0.2.2-3medibuntu2
                      # hot-babe  0.2.2-3medibuntu2
                      # hot-babe  0.2.2-3medibuntu2
                      # hot-babe  0.2.2-3medibuntu3
                      # hot-babe  0.2.2-3medibuntu3
          o k
                + k3b
                      # k3b  1.0-0ubuntu2+medibuntu1
                      # k3b  1.0-0ubuntu2+medibuntu1
                      # k3b  1.0-0ubuntu2+medibuntu1
                      # libk3b-dev  1.0-0ubuntu2+medibuntu1
                      # libk3b-dev  1.0-0ubuntu2+medibuntu1
                      # libk3b-dev  1.0-0ubuntu2+medibuntu1
                      # libk3b2-mp3  1.0-0ubuntu2+medibuntu1
                      # libk3b2-mp3  1.0-0ubuntu2+medibuntu1
                      # libk3b2-mp3  1.0-0ubuntu2+medibuntu1
                      # libk3b2  1.0-0ubuntu2+medibuntu1
                      # libk3b2  1.0-0ubuntu2+medibuntu1
                      # libk3b2  1.0-0ubuntu2+medibuntu1
                + kaffeine
                      # kaffeine-xine  0.8.3-0ubuntu7+medibuntu1
                      # kaffeine-xine  0.8.3-0ubuntu7+medibuntu1
                      # kaffeine-xine  0.8.3-0ubuntu7+medibuntu1
                      # kaffeine  0.8.3-0ubuntu7+medibuntu1
                      # kaffeine  0.8.3-0ubuntu7+medibuntu1
                      # kaffeine  0.8.3-0ubuntu7+medibuntu1
          o libd
                + libdvdcss
                      # libdvdcss2-dev  1.2.9-2medibuntu2+build1
                      # libdvdcss2-dev  1.2.9-2medibuntu2+b1
                      # libdvdcss2-dev  1.2.9-2medibuntu2+b1
                      # libdvdcss2-dev  1.2.9-2medibuntu2+b1
                      # libdvdcss2-dev  1.2.9-2medibuntu2+build1
                      # libdvdcss2-dev  1.2.9-2medibuntu2+build1
                      # libdvdcss2  1.2.9-2medibuntu2+build1
                      # libdvdcss2-dev  1.2.9-2medibuntu2
                      # libdvdcss2-dev  1.2.9-2medibuntu2
                      # libdvdcss2-dev  1.2.9-2medibuntu2
                      # libdvdcss2  1.2.9-2medibuntu2+b1
                      # libdvdcss2  1.2.9-2medibuntu2+b1
                      # libdvdcss2  1.2.9-2medibuntu2+b1
                      # libdvdcss2  1.2.9-2medibuntu2+build1
                      # libdvdcss2  1.2.9-2medibuntu2+build1
                      # libdvdcss2  1.2.9-2medibuntu2
                      # libdvdcss2  1.2.9-2medibuntu2
                      # libdvdcss2  1.2.9-2medibuntu2
                + libdvdcss2
                      # libdvdcss2-dev  1.2.9-1plf3
                      # libdvdcss2-dev  1.2.9-1plf3
                      # libdvdcss2-dev  1.2.9-1plf3
                      # libdvdcss2  1.2.9-1plf3
                      # libdvdcss2  1.2.9-1plf3
                      # libdvdcss2  1.2.9-1plf3
          o m
                + mplayer
                      # mplayer-nogui  1.0~rc1-0ubuntu9+medibuntu1
                      # mencoder  1.0~rc1-0ubuntu9+medibuntu1
                      # mplayer-doc  1.0~rc1-0ubuntu9+medibuntu1
                      # mplayer  1.0~rc1-0ubuntu9+medibuntu1
          o x
                + xmms-wma
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.06
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.06
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.06
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.10
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.10
                      # beep-media-player-wma  1.0.5-3~0medibuntu6.10
                      # bmp-wma  1.0.5-1medibuntu1
                      # xmms-wma  1.0.5-3~0medibuntu6.06
                      # xmms-wma  1.0.5-3~0medibuntu6.06
                      # xmms-wma  1.0.5-3~0medibuntu6.06
                      # xmms-wma  1.0.5-3~0medibuntu6.10
                      # xmms-wma  1.0.5-3~0medibuntu6.10
                      # xmms-wma  1.0.5-3~0medibuntu6.10

    * non-free
          o a
                + acroread
                      # acroread-escript  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # acroread-escript  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # acroread-plugins  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # acroread-plugins  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu2
                      # mozilla-acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu2
          o g
                + googleearth
                      # googleearth-data  4.0.2735.0-0medibuntu2~dapper0.1
                      # googleearth-data  4.0.2735.0-0medibuntu2~edgy0.1
                      # googleearth-data  4.0.2735.0-0medibuntu4
                      # googleearth-data  4.1.7076.4458-0medibuntu2
                      # googleearth  4.0.2735.0-0medibuntu2~dapper0.1
                      # googleearth  4.0.2735.0-0medibuntu2~dapper0.1
                      # googleearth  4.0.2735.0-0medibuntu2~edgy0.1
                      # googleearth  4.0.2735.0-0medibuntu2~edgy0.1
                      # googleearth  4.0.2735.0-0medibuntu4
                      # googleearth  4.0.2735.0-0medibuntu4
                      # googleearth  4.1.7076.4458-0medibuntu2
                      # googleearth-data  4.1.7076.4458-0medibuntu2~feisty0.1
                      # googleearth  4.1.7076.4458-0medibuntu2~feisty0.1
                      # googleearth  4.1.7076.4458-0medibuntu2
                      # googleearth  4.1.7076.4458-0medibuntu2~feisty0.1
          o i
                + ibm-j2re1.5
                      # ibm-j2re1.5  1.5.0-0medibuntu1
                      # ibm-j2re1.5  1.5.0
                + ibm-j2sdk1.5
                      # ibm-j2sdk1.5  1.5.0-0medibuntu1
                      # ibm-j2sdk1.5  1.5.0
          o o
                + opera
                      # opera  8.51-20051114.6
          o p
                + ppc-codecs
                      # ppc-codecs  20051120-0plf6.10
                      # ppc-codecs  20061022-0medibuntu2
          o r
                + realplay
                      # realplay  10.0.6.776-1plf1
          o s
                + skype-static
                      # skype-static  1.3.0.53-2medibuntu1+b1
                      # skype-static  1.3.0.53-2medibuntu1
                      # skype-static  1.3.0.53-2medibuntu2
                      # skype-static  1.4.0.74-0medibuntu1
                + skype
                      # skype  1.2.0.18-1
                      # skype  1.3.0.53-1medibuntu1+b1
                      # skype  1.3.0.53-1medibuntu1
                      # skype  1.3.0.53-1medibuntu2
                      # skype  1.4.0.74-0medibuntu1~feisty0.1
                      # skype  1.4.0.74-0medibuntu2
                + sun-j2re1.5
                      # sun-j2re1.5  1.5.0+update09
                + sun-j2sdk1.5
                      # sun-j2sdk1.5  1.5.0+update09
          o w
                + w32codecs
                      # w32codecs  20061022-0medibuntu1+b1
                      # w32codecs  20050412-1plf4
                      # w32codecs  20061022-0medibuntu1+build1
                      # w32codecs  20061022-0medibuntu1
                + w64codecs
                      # w64codecs  20061203-0medibuntu1
---------------------------------------------------------------------------------------------------------------------------

[http://mighmos.org/packages.php](http://mighmos.org/packages.php)
Dapper Drake (6.06)
Package Name     Package Version     Link     Source     Depends
Gaim     2.0.0 beta5     i386
AMD64
PPC     Original
Patches     Gaim Data Files
Gaim Encryption     3.0.0beta6     i386
AMD64
PPC     Source     Gaim (-beta3.1)
Last Exit     1.0-1     i386
AMD64     Source     N/A
Mugshot     1.1.13     i386
AMD64     Source     N/A
Rhythmbox     0.9.6     AMD64
i386
PPC     Source     None
Breezy Badger (5.10)
Package Name     Package Version     Link     Source     Depends
GTK Engines (Cairo)     2.7.4     Clearlooks i386 Crux i386
Clearlooks AMD64 Crux AMD64     Source     N/A
Gaim     2.0.0beta3     i386
AMD64
Data Files (REQUIRED)
PPC (beta2)     Source     N/A
Gaim Encryption     3.0.0beta4     i386
AMD64     Source     Gaim
Rhythmbox     0.9.4.1     i386
AMD64     Source     libgpod
libgpod-common
libgpod     0.3.0     AMD64 AMD64 dev
i386 i386 dev
Common Files (required)     Source     N/A
libpoppler     0.5.0     AMD64 libpoppler
AMD64 libpoppler Glib
i386 libpoppler
i386 libpoppler Glib     Source     N/A
---------------------------------------------------------------------------------------------------------------------------
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Automatix2 comes with a graphical interface, but in order to install Automatix2 there are a few steps we have to do on the command line. Go to Applications > Accessories > Terminal to open a command line window.

In the command line window, type in the following commands to install Automatix:

echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list

You might have to provide your password. Afterwards, run

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key

gpg --export --armor E23C5FC3 | sudo apt-key add -

nd update the packages database:

sudo apt-get update

Finally, install Automatix:

sudo apt-get install automatix2

Then close the command line window. After Automatix has been installed, you can find it under Applications -> System Tools -> Automatix: 



---------------------------------------------------------------------------------------------------------------------------

[http://seveas.theplayboymansion.net/seveas/](http://seveas.theplayboymansion.net/seveas/)
---------------------------------------------------------------------------------------------------------------------------

build your own repositorys
[https://launchpad.net/falcon](https://launchpad.net/falcon)
---------------------------------------------------------------------------------------------------------------------------
[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)
falcon
    Version    2.0.0~beta2-0ubuntu1 (changes)

    falcon (2.0.0~beta2-0ubuntu1) feisty; urgency=low

        * Warn when syncing if you installed packages after the last export

        * Checksum/size checking in falcon-import

        * Allow binary-only packages to be in morguefiles

        * Create file lists (Contents-$arch.tar.gz)

        * New action: clean -- the same as scan, but pocket.keepfiles is emptiedbefore scanning.

        * Make sure controlfiles (.dsc and control part of .deb) are utf-8 encodedso django doesn't b0rk.

        * Exit gracefully when file access issues are found

        * Support a proxy in falcon-import

        * Plugin system is now actually usable. Plugins available:

        *
              o SSH agent starter

        *
              o Mail maintainer on installs

        *
              o Run packages through linda/lintian

  *

    Source (.dsc)    falcon_2.0.0~beta2-0ubuntu1.dsc
    Source (.tar.gz)    falcon_2.0.0~beta2.orig.tar.gz
    Source (.diff.gz)    falcon_2.0.0~beta2-0ubuntu1.diff.gz

    falcon
        Description    Repository manager for .deb packages (More...)

        Falcon is a tool that generates the repository meta-information (such as package listings and release files) in order to transform a set of packages into a proper repository.

        Features * Every subdir of the pool is automatically a pocket * Support for metacomponents to make it easier to use * GPG signed Release files * Easy template based HTML output for repository indices * Morgueing of old packages * Easy support for complete and partial mirrors * Easy creation of .iso files * Easy import of sources from other debian repositories

        This is a development snapshot of falcon 2.0
        Package    falcon_2.0.0~beta2-0ubuntu1_all.deb

freenx
    Version    0.6.0-0~seveas2 (changes)

    freenx (0.6.0-0~seveas2) feisty; urgency=low

        * Re-introduce dpatch, no more patch-embedded-in-diff.gz

    Source (.dsc)    freenx_0.6.0-0~seveas2.dsc
    Source (.tar.gz)    freenx_0.6.0.orig.tar.gz
    Source (.diff.gz)    freenx_0.6.0-0~seveas2.diff.gz

    freenx
        Description    The FreeNX application/thin-client server based on NX technology (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        This package contains a free (GPL) implementation of the nxserver component.
        Package    freenx_0.6.0-0~seveas2_i386.deb

gftp
    Version    2.0.18-16ubuntu2seveas1
    Source (.dsc)    gftp_2.0.18-16ubuntu2seveas1.dsc
    Source (.tar.gz)    gftp_2.0.18.orig.tar.gz
    Source (.diff.gz)    gftp_2.0.18-16ubuntu2seveas1.diff.gz

    gftp
        Description    X/GTK+ FTP client (More...)

        gFTP is a multithreaded FTP client, available in two versions: * version for X, written using GLib and GTK+ * version for the console, using only GLib

        This is an upgrade convenience package, it's only useful for depending on.
        Package    gftp_2.0.18-16ubuntu2seveas1_all.deb
    gftp-common
        Description    shared files for other gFTP packages (More...)

        gFTP is a multithreaded FTP client. This package contains the locale data used by both gftp-gtk and gftp-text, along with a common manual page.

        gFTP features: * simultaneous downloads, * resuming of interrupted file transfers, * file transfer queues, * downloading of entire directories, * FTP and HTTP proxy support, * remote directory caching, * passive and non-passive file transfers, * drag-n-drop support, * bookmarks menu, * support for SSH and SSH2 file transfers, * support FXP transferts, * stop button, and many more features.

        Author: Brian Masney Homepage: [http://www.gftp.org](http://www.gftp.org)
        Package    gftp-common_2.0.18-16ubuntu2seveas1_i386.deb
    gftp-gtk
        Description    X/GTK+ FTP client (More...)

        gFTP is a multithreaded FTP client. This version of it runs under X and was written using GLib/GTK+.

        gFTP features: * simultaneous downloads, * resuming of interrupted file transfers, * file transfer queues, * downloading of entire directories, * FTP and HTTP proxy support, * remote directory caching, * passive and non-passive file transfers, * drag-n-drop support, * bookmarks menu, * support for SSH and SSH2 file transfers, * support FXP transfers, * stop button, and many more features.

        Author: Brian Masney Homepage: [http://www.gftp.org](http://www.gftp.org)
        Package    gftp-gtk_2.0.18-16ubuntu2seveas1_i386.deb
    gftp-text
        Description    colored FTP client using GLib (More...)

        gFTP is a multithreaded FTP client. This version of it runs under console and was written using GLib.

        gFTP features: * simultaneous downloads, * resuming of interrupted file transfers, * file transfer queues, * downloading of entire directories, * FTP and HTTP proxy support, * remote directory caching, * passive and non-passive file transfers, * drag-n-drop support, * bookmarks menu, * support for SSH and SSH2 file transfers, * support FXP transferts, * stop button, and many more features.

        Author: Brian Masney Homepage: [http://www.gftp.org](http://www.gftp.org)
        Package    gftp-text_2.0.18-16ubuntu2seveas1_i386.deb

libdvdcss
    Version    1.2.9-0.0ubuntu6
    Source (.dsc)    libdvdcss_1.2.9-0.0ubuntu6.dsc
    Source (.tar.gz)    libdvdcss_1.2.9.orig.tar.gz
    Source (.diff.gz)    libdvdcss_1.2.9-0.0ubuntu6.diff.gz

    libdvdcss2
        Description    Simple foundation for reading DVDs - runtime libraries (More...)

        To allow applications to access some of the more advanced features of the DVD format.
        Package    libdvdcss2_1.2.9-0.0ubuntu6_i386.deb
    libdvdcss2-dev
        Description    Simple foundation for reading DVDs - devel files (More...)

        To allow applications to access some of the more advanced features of the DVD format.
        Package    libdvdcss2-dev_1.2.9-0.0ubuntu6_i386.deb

lives
    Version    1:0.9.8.4-0.0~seveas1
    Source (.dsc)    lives_0.9.8.4-0.0~seveas1.dsc
    Source (.tar.gz)    lives_0.9.8.4.orig.tar.gz
    Source (.diff.gz)    lives_0.9.8.4-0.0~seveas1.diff.gz

    lives
        Description    Linux Video Editing System (More...)

        LiVES lets you start editing and making video right away, without having to worry about formats, frame sizes, or framerates. LiVES will let you start creating your own tools, utilities and effects via the built in RFX builder.

        LiVES is aimed at the digital video artist who wants to create their own content, the video editor who wants to produce professional looking video, and the VJ who wants to captivate with spectacular images.

        [http://lives.sourceforge.net/](http://lives.sourceforge.net/)
        Package    lives_0.9.8.4-0.0~seveas1_i386.deb

nx
    Version    2.1.0-0~seveas2
    Source (.dsc)    nx_2.1.0-0~seveas2.dsc
    Source (.tar.gz)    nx_2.1.0.orig.tar.gz
    Source (.diff.gz)    nx_2.1.0-0~seveas2.diff.gz

    libxcomp-dev
        Description    NoMachine NX - NX compression library (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        This package contains the development files for the libxcomp library.
        Package    libxcomp-dev_2.1.0-0~seveas2_all.deb
    libxcomp2
        Description    NoMachine NX - NX compression library (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        This package contains the X compression library.
        Package    libxcomp2_2.1.0-0~seveas2_i386.deb
    libxcompext-dev
        Description    NoMachine NX - NX compression library (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        This package contains the development files for the libxcompext library.
        Package    libxcompext-dev_2.1.0-0~seveas2_all.deb
    libxcompext2
        Description    NoMachine NX - NX compression library (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        This package contains the development files for the libxcomp library.
        Package    libxcompext2_2.1.0-0~seveas2_i386.deb
    nxagent
        Description    NoMachine NX - nesting X server with roundtrip suppression (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        Nxagent is an X server based on Xnest, but modified for the purpose of reducing roundtrips over high-latency networks significantly. It is run on the client side of X that is, on the machine where X clients run. It connects, over the wire to your regular X server, possibly through nxproxy.
        Package    nxagent_2.1.0-0~seveas2_i386.deb
    nxagent-dev
        Description    NoMachine NX - nesting X server with roundtrip suppression (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        Nxagent is an X server based on Xnestbut modified for the purpose of reducing roundtrips over high-latency networks significantly. It is run on the client side of X that is, on the machine where X clients run. It connects, over the wire to your regular X server, possibly through nxproxy.

        The nxagent-dev package contains the development libraries shared among different NX agents (nxdesktop, nxviewer).
        Package    nxagent-dev_2.1.0-0~seveas2_all.deb
    nxlibs
        Description    NoMachine NX - common agent libraries (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        The nxlibs package contains the libraries shared among different NX agents (nxdesktopnxagent, nxviewer).
        Package    nxlibs_2.1.0-0~seveas2_i386.deb
    nxlibs-dev
        Description    NoMachine NX - common agent libraries (More...)

        NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.

        The nxlibs-dev package contains the development libraries shared among different NX agents (nxdesktop, nxagent, nxviewer).
        Package    nxlibs-dev_2.1.0-0~seveas2_all.deb

nxclient
    Version    2.1.0-17

    nxclient
        Description    NX Client (More...)

        . NoMachine NX is a fast and scalable terminal server system based on the X11 protocol. NX lets you work fluently even across slow links like modems and provides a full set of administration tools that make it a complete desktop virtualization solution for your organization.

        This package contains the graphical front-end used to access X, RDP and RFB sessions on a remote NX Server. It also includes NX X compression libraries and utilities needed by both NX Client and Server.

        Baseline:

        nx-X11: 2.1.0-3 nxauth: 2.1.0-2 nxwin: 2.1.0-3 nxssh: 2.1.0-2 nxcomp: 2.1.0-8 nxesd: 2.1.0-3 nxkill: 2.1.0-2 nxservice: 2.1.0-11 nxcompsh: 2.1.0-3
        Package    nxclient_2.1.0-17_i386.deb

nxplugin
    Version    2.1.0-5

    nxplugin
        Description    NX Web Companion (More...)

        NoMachine NX is a fast and scalable terminal server system based on the X11 protocol. NX lets you work fluently even across slow links like modems and provides a full set of administration tools that make it a complete desktop virtualization solution for your organization This package contains the NX Web Companion Java applet and the set of NX client plugins for the supported platforms. Baseline: nxapplet-2.1.0-6 Windows/nxclient-2.1.0-17 Linux/nxclient-2.1.0-17 MacOSX/nxclient-2.1.0-17 Solaris/nxclient-2.1.0-17
        Package    nxplugin_2.1.0-5_i386.deb

openftd
    Version    0.98.6-0~feisty1.1 (changes)

    openftd (0.98.6-0~feisty1.1) feisty; urgency=low

        * Feisty build

    Source (.dsc)    openftd_0.98.6-0~feisty1.1.dsc
    Source (.tar.gz)    openftd_0.98.6.orig.tar.gz
    Source (.diff.gz)    openftd_0.98.6-0~feisty1.1.diff.gz

    openftd
        Description    FTD 4 linux usenet organizer (common files) (More...)

        The program FTD is used by many people to tell what they will post and is therefore a beautiful way to see what is posted in the binary newsgroups. FTD4Linux is the Open Source equivalent.

        This package contains common libraries and files
        Package    openftd_0.98.6-0~feisty1.1_i386.deb
    openftd-gtkhtml
        Description    FTD 4 linux usenet organizer (gtkhtml version) (More...)

        The program FTD is used by many people to tell what they will post and is therefore a beautiful way to see what is posted in the binary newsgroups. FTD4Linux is the Open Source equivalent.

        This version uses the gtkhtml as rendering engine
        Package    openftd-gtkhtml_0.98.6-0~feisty1.1_i386.deb
    openftd-mozilla
        Description    FTD 4 linux usenet organizer (firefox version) (More...)

        The program FTD is used by many people to tell what they will post and is therefore a beautiful way to see what is posted in the binary newsgroups. FTD4Linux is the Open Source equivalent.

        This version uses firefox as rendering engine
        Package    openftd-mozilla_0.98.6-0~feisty1.1_i386.deb

openssh
    Version    1:4.6p1-2~feisty1
    Source (.dsc)    openssh_4.6p1-2~feisty1.dsc
    Source (.tar.gz)    openssh_4.6p1.orig.tar.gz
    Source (.diff.gz)    openssh_4.6p1-2~feisty1.diff.gz

    openssh-client
        Description    secure shell client, an rlogin/rsh/rcp replacement (More...)

        This is the portable version of OpenSSH, a free implementation of the Secure Shell protocol as specified by the IETF secsh working group.

        Ssh (Secure Shell) is a program for logging into a remote machine and for executing commands on a remote machine. It provides secure encrypted communications between two untrusted hosts over an insecure network. X11 connections and arbitrary TCP/IP ports can also be forwarded over the secure channel. It is intended as a replacement for rlogin, rsh and rcp, and can be used to provide applications with a secure communication channel.

        This package provides the ssh, scp and sftp clients, the ssh-agent and ssh-add programs to make public key authentication more convenient, and the ssh-keygen, ssh-keyscan, ssh-copy-id and ssh-argv0 utilities.

        In some countries it may be illegal to use any encryption at all without a special permit.
        Package    openssh-client_4.6p1-2~feisty1_i386.deb
    openssh-client-udeb
        Description    secure shell client for the Debian installer (More...)

        This is the portable version of OpenSSH, a free implementation of the Secure Shell protocol as specified by the IETF secsh working group.

        This package provides the ssh client for use in debian-installer.
        Package    openssh-client-udeb_4.6p1-2~feisty1_i386.udeb
    openssh-server
        Description    secure shell server, an rshd replacement (More...)

        This is the portable version of OpenSSH, a free implementation of the Secure Shell protocol as specified by the IETF secsh working group.

        Ssh (Secure Shell) is a program for logging into a remote machine and for executing commands on a remote machine. It provides secure encrypted communications between two untrusted hosts over an insecure network. X11 connections and arbitrary TCP/IP ports can also be forwarded over the secure channel. It is intended as a replacement for rlogin, rsh and rcp, and can be used to provide applications with a secure communication channel.

        This package provides the sshd server.

        In some countries it may be illegal to use any encryption at all without a special permit.
        Package    openssh-server_4.6p1-2~feisty1_i386.deb
    openssh-server-udeb
        Description    secure shell server for the Debian installer (More...)

        This is the portable version of OpenSSH, a free implementation of the Secure Shell protocol as specified by the IETF secsh working group.

        This package provides the sshd server for use in debian-installer. Since it is expected to be used in specialized situations (e.g. S/390 installs with no console), it does not provide any configuration.
        Package    openssh-server-udeb_4.6p1-2~feisty1_i386.udeb
    ssh
        Description    secure shell client and server (transitional package) (More...)

        This is a transitional package depending on both the OpenSSH client and the OpenSSH server, which are now in separate packages. You may remove it once the upgrade is complete and nothing depends on it.
        Package    ssh_4.6p1-2~feisty1_all.deb
    ssh-askpass-gnome
        Description    interactive X program to prompt users for a passphrase for ssh-add (More...)

        This has been split out of the main ssh package, so that the ssh will not need to depend upon the Gnome libraries.

        You probably want the ssh-askpass package instead, but this is provided to add to your choice and/or confusion.
        Package    ssh-askpass-gnome_4.6p1-2~feisty1_i386.deb
    ssh-krb5
        Description    secure shell client and server (transitional package) (More...)

        This is a transitional package depending on the regular Debian OpenSSH client and server, which now support GSSAPI natively. It will add the necessary GSSAPI options to the server configuration file. You can remove it once the upgrade is complete and nothing depends on it.
        Package    ssh-krb5_4.6p1-2~feisty1_all.deb

seveas-meta
    Version    7.04-7
    Source (.dsc)    seveas-meta_7.04-7.dsc
    Source (.tar.gz)    seveas-meta_7.04-7.tar.gz

    ubuntu-apt-utils
        Description    Utilities for the APT system (More...)

        This package will install a suite of useful utilities for the apt and dpkg systems.

        It is safe to remove this package once installed, the pacakges themself don't depend on it.
        Package    ubuntu-apt-utils_7.04-7_all.deb
    ubuntu-devel
        Description    Ubuntu development packages (More...)

        This package will install a complete Ubuntu development suite.

        It is safe to remove this package once installed, the pacakges themself don't depend on it.
        Package    ubuntu-devel_7.04-7_all.deb
    ubuntu-games
        Description    Several games (More...)

        This package will install several games Ubuntu provides. The package itself can safely be removed afterward.
        Package    ubuntu-games_7.04-7_all.deb
    ubuntu-lamp
        Description    Packages for a LAMP setup (More...)

        This package gives you a complete 1-machine LAMP system.

        It is safe to remove this package again after installed, the services themself will not be removed with it
        Package    ubuntu-lamp_7.04-7_all.deb
    ubuntu-multimedia-gnome
        Description    Ubuntu multimedia packages - GNOME version (More...)

        This package will install a complete multimedia system for the GNOME desktop, including codecs, players and catalog programs

        It is safe to remove this package again after installed, the services themself will not be removed with it
        Package    ubuntu-multimedia-gnome_7.04-7_i386.deb
    ubuntu-multimedia-kde
        Description    Ubuntu multimedia packages - KDE version (More...)

        This package will install a complete multimedia system for the KDE desktop, including codecs, players and catalog programs

        It is safe to remove this package again after installed, the services themself will not be removed with it
        Package    ubuntu-multimedia-kde_7.04-7_i386.deb
    ubuntu-seveas
        Description    A personal selection of software (More...)

        This package installs my favourite software, probably it's not useful to anyone else :)
        Package    ubuntu-seveas_7.04-7_i386.deb
    ubuntu-sysadmin
        Description    Systm administration tools (More...)

        This package installs some system adminstration tools. The package itself can be safely removed afterward.
        Package    ubuntu-sysadmin_7.04-7_all.deb

supertuxkart
    Version    0.3~svn1162-0ubuntu1 (changes)

    supertuxkart (0.3~svn1162-0ubuntu1) feisty; urgency=low

        * Update to latest svn, which has many improvements

        * Update build-depends accordingly

        * Modify debian/rules for SVN builds (autogen.sh and cleanup)

    Source (.dsc)    supertuxkart_0.3~svn1162-0ubuntu1.dsc
    Source (.tar.gz)    supertuxkart_0.3~svn1162.orig.tar.gz
    Source (.diff.gz)    supertuxkart_0.3~svn1162-0ubuntu1.diff.gz

    supertuxkart
        Description    a kart racing game (More...)

        SuperTuxKart is an enhanced version of TuxKart. The kart racing game, originaly done by Steve Baker, featuring Tux and a bunch of his friends. SuperTuxKart is the work of the GotM run for TuxKart at happypenguin.org. Due to some disagreements that happened in that time this fork of TuxKart was done. SuperTuxKart features include: new characters new tracks a completly new userinterface some smaller graphical improvemnts (skidmarks, smoke, animated wheels, etc.) whole bunch of new bugs, in its current state its not really playable

        Homepage: [http://supertuxkart.berlios.de/](http://supertuxkart.berlios.de/)
        Package    supertuxkart_0.3~svn1162-0ubuntu1_i386.deb
    supertuxkart-data
        Description    data files for supertuxkart, a kart racing game (More...)

        SuperTuxKart is an enhanced version of TuxKart. The kart racing game, originaly done by Steve Baker, featuring Tux and a bunch of his friends. SuperTuxKart is the work of the GotM run for TuxKart at happypenguin.org. Due to some disagreements that happened in that time this fork of TuxKart was done. SuperTuxKart features include: new characters new tracks a completly new userinterface some smaller graphical improvemnts (skidmarks, smoke, animated wheels, etc.) whole bunch of new bugs, in its current state its not really playable

        This package contains data files for the game supertuxkart

        Homepage: [http://supertuxkart.berlios.de/](http://supertuxkart.berlios.de/)
        Package    supertuxkart-data_0.3~svn1162-0ubuntu1_all.deb

ttf-fossfonts
    Version    0.0.3
    Source (.dsc)    ttf-fossfonts_0.0.3.dsc
    Source (.tar.gz)    ttf-fossfonts_0.0.3.tar.gz

    ttf-fossfonts
        Description    Collection of 108 GPL/Public-Domain TTF fonts (More...)

        ttf-fossfonts is a collection of 108 GPL/Public-Domain licenced .ttf fonts. Included are the Tuffy family with extended members, and the Open Bar Codes project fonts.

        The package suggests several other worthwhile font packages.
        Package    ttf-fossfonts_0.0.3_all.deb

w32codecs
    Version    20061022-1~seveas1 (changes)

    w32codecs (20061022-1~seveas1) feisty; urgency=low

        * Swutch to medibuntu as upstream

    Source (.dsc)    w32codecs_20061022-1~seveas1.dsc
    Source (.tar.gz)    w32codecs_20061022.orig.tar.gz
    Source (.diff.gz)    w32codecs_20061022-1~seveas1.diff.gz

    w32codecs
        Description    Win32 codec binaries (More...)

        This package contains Win32 codec binaries, required for the decompression of video formats that have no open source alternative.

        Homepage: [http://www4.mplayerhq.hu/](http://www4.mplayerhq.hu/)

        This is in Medibuntu for it's non-free license.
        Package    w32codecs_20061022-1~seveas1_i386.deb

xmoto
    Version    0.3.0-2~feisty1
    Source (.dsc)    xmoto_0.3.0-2~feisty1.dsc
    Source (.tar.gz)    xmoto_0.3.0.orig.tar.gz
    Source (.diff.gz)    xmoto_0.3.0-2~feisty1.diff.gz

    xmoto
        Description    2D motocross platform game (More...)

        X-Moto is a challenging 2D motocross platform game, where physics play an all important role in the gameplay. You need to control your bike to its limit, if you want to have a chance finishing the more difficult of the challenges.
        Package    xmoto_0.3.0-2~feisty1_i386.deb
    xmoto-data
        Description    2D motocross platform game (More...)

        X-Moto is a challenging 2D motocross platform game, where physics play an all important role in the gameplay. You need to control your bike to its limit, if you want to have a chance finishing the more difficult of the challenges.

        This package contains the data files needed by xmoto.
        Package    xmoto-data_0.3.0-2~feisty1_all.deb
---------------------------------------------------------------------------------------------------------------------------
[http://ubuntu.beryl-project.org/index.html](http://ubuntu.beryl-project.org/index.html)
Ubuntu Beryl Repository
---------------------------------------------------------------------------------------------------------------------------
[http://cl.aist-nara.ac.jp/~eric-n/ubuntu-nlp/]("http://cl.aist-nara.ac.jp/%7Eeric-n/ubuntu-nlp/")
The Ubuntu NLP Repository
Packages

amarok-moodbar
    Version:    0.1.2-1nlp3~0feisty1 (changes)

    amarok-moodbar (0.1.2-1nlp3~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    amarok-moodbar_0.1.2-1nlp3~0feisty1.dsc
    Source (tar.gz):    amarok-moodbar_0.1.2-1nlp3~0feisty1.tar.gz
amarok-moodbar
    Description:    Moodbar plugin for Amarok More...

    The Amarok Moodbar analyzes songs and displays their moods in the Amarok GUI.
    Package:    amarok-moodbar_0.1.2-1nlp3~0feisty1_i386.deb
    Package:    amarok-moodbar_0.1.2-1nlp3~0feisty1_amd64.deb
geniatagger
    Version:    3.0-1nlp2~0feisty1 (changes)

    geniatagger (3.0-1nlp2~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    geniatagger_3.0-1nlp2~0feisty1.dsc
    Source (tar.gz):    geniatagger_3.0-1nlp2~0feisty1.tar.gz
geniatagger
    Description:    GENIA Tagger - English part-of-speech tagger and shallow parser More...

    The GENIA tagger analyzes English sentences and outputs the base forms,
    part-of-speech tags, and chunk tags. The tagger is specifically tuned
    for biomedical text such as MEDLINE abstracts. If you need to extract
    information from biomedical documents, this tagger could be a useful
    preprocessing tool.

    This package contains the GENIA Tagger program.
    Package:    geniatagger_3.0-1nlp2~0feisty1_i386.deb
    Package:    geniatagger_3.0-1nlp2~0feisty1_amd64.deb
geniatagger-doc
    Description:    Documentation for the GENIA Tagger More...

    The GENIA tagger analyzes English sentences and outputs the base forms,
    part-of-speech tags, and chunk tags. The tagger is specifically tuned
    for biomedical text such as MEDLINE abstracts. If you need to extract
    information from biomedical documents, this tagger could be a useful
    preprocessing tool.

    This package contains documentation for the GENIA Tagger.
    Package:    geniatagger-doc_3.0-1nlp2~0feisty1_all.deb
giza++
    Version:    2.0.20030930gcc41-3nlp1~0feisty1 (changes)

    giza++ (2.0.20030930gcc41-3nlp1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    giza++_2.0.20030930gcc41-3nlp1~0feisty1.dsc
    Source (tar.gz):    giza++_2.0.20030930gcc41-3nlp1~0feisty1.tar.gz
giza++
    Description:    A tool for training statistical alignment models More...

    GIZA++: Training of statistical translation models.

    GIZA++ is an extension of the program GIZA (part of the SMT toolkit EGYPT)
    which was developed by the Statistical Machine Translation team during the
    summer workshop in 1999 at the Center for Language and Speech Processing
    at Johns-Hopkins University (CLSP/JHU). GIZA++ includes a lot of additional
    features. The extensions of GIZA++ were designed and written by Franz Josef
    Och.

    About GIZA++

    The program includes the following extensions to GIZA:

    * IBM Model 4;
    * IBM Model 5;
    * Alignment models depending on word classes
    * Implements the HMM alignment model: Baum-Welch training, Forward-Backward
    algorithm, empty word, dependency on word classes, transfer to fertility
    models
    * Includes a variant of Model 3 and Model 4 which allow the training of the
    parameter p_0;
    * Various smoothing techniques for fertility, distortion/alignment parameters;
    * Significant more efficient training of the fertility models;
    * Correct implementation of pegging as described in (Brown et al. 1993), a
    series of heuristics in order to make pegging sufficiently efficient;

    For more information, consult the following publication:

    @ARTICLE{och03:asc,
    AUTHOR = {Franz Josef Och and Hermann Ney},
    TITLE = {A Systematic Comparison of Various Statistical Alignment Models},
    JOURNAL= {Computational Linguistics},
    NUMBER = 1,
    VOLUME = 29,
    YEAR = 2.0.2003,
    PAGES = {19--51}}

    or the GIZA++ project homepage <http://www.fjoch.com/GIZA++.html>
    Package:    giza++_2.0.20030930gcc41-3nlp1~0feisty1_i386.deb
    Package:    giza++_2.0.20030930gcc41-3nlp1~0feisty1_amd64.deb
mecab
    Version:    0.95-1nlp3~0feisty1 (changes)

    mecab (0.95-1nlp3~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    mecab_0.95-1nlp3~0feisty1.dsc
    Source (tar.gz):    mecab_0.95-1nlp3~0feisty1.tar.gz
libmecab-dev
    Description:    Header files of Mecab More...

    This package provides header files which are necessary to development
    programs using runtime libraries of Mecab, that is a Japanese
    morphological analysis system.
    Package:    libmecab-dev_0.95-1nlp3~0feisty1_i386.deb
    Package:    libmecab-dev_0.95-1nlp3~0feisty1_amd64.deb
libmecab1
    Description:    Libraries of Mecab More...

    This package provides runtime libraries of Mecab, that is a Japanese
    morphological analysis system.
    Package:    libmecab1_0.95-1nlp3~0feisty1_i386.deb
    Package:    libmecab1_0.95-1nlp3~0feisty1_amd64.deb
mecab
    Description:    Japanese morphological analysis system More...

    Mecab is a morphological analysis system. It reads Japanese
    sentences from the standard input, segments them into morpheme
    sequences, and outputs them to the standard output with many
    additional pieces of information (pronunciation, semantic
    information, etc).
    Package:    mecab_0.95-1nlp3~0feisty1_i386.deb
    Package:    mecab_0.95-1nlp3~0feisty1_amd64.deb
mecab-utils
    Description:    Support programs of Mecab More...

    This package provides the dictionary compiler to convert a dictionary
    written in text format to a binary data for Mecab, that is a Japanese
    morphological analysis system. This package is necessary to install
    dictionary packages for Mecab like mecab-jumandic.
    Package:    mecab-utils_0.95-1nlp3~0feisty1_i386.deb
    Package:    mecab-utils_0.95-1nlp3~0feisty1_amd64.deb
mecab-ipadic
    Version:    2.7.0-20060707-1nlp3~0feisty1 (changes)

    mecab-ipadic (2.7.0-20060707-1nlp3~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    mecab-ipadic_2.7.0-20060707-1nlp3~0feisty1.dsc
    Source (tar.gz):    mecab-ipadic_2.7.0-20060707-1nlp3~0feisty1.tar.gz
mecab-ipadic
    Description:    IPA dictionary compiled for Mecab More...

    This package provides IPA dictionary converted for Mecab, that is a
    Japanese morphological analysis system. This dictionary written in
    IPA grammar system.
    Package:    mecab-ipadic_2.7.0-20060707-1nlp3~0feisty1_all.deb
mkcls
    Version:    2.0.20030930gcc41-1nlp2~0feisty1 (changes)

    mkcls (2.0.20030930gcc41-1nlp2~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    mkcls_2.0.20030930gcc41-1nlp2~0feisty1.dsc
    Source (tar.gz):    mkcls_2.0.20030930gcc41-1nlp2~0feisty1.tar.gz
mkcls
    Description:    A tool for training statistical alignment models More...

    mkcls: word class training with maximum likelihood-criterion.

    mkcls is a tool to train word classes by using a maximum-likelihood-criterion.
    The resulting word classes are especially suited for language models or
    statistical translation models. The program mkcls was written by Franz Josef
    Och.

    For more information, consult the following publication:

    * Franz Josef Och: "An Efficient Method for Determining Bilingual Word
    Classes"; pp. 71-76, Ninth Conf. of the Europ. Chapter of the Association
    for Computational Linguistics; EACL'99, Bergen, Norway, June 1999.

    or the mkcls project homepage <http://www.fjoch.com/mkcls.html>
    Package:    mkcls_2.0.20030930gcc41-1nlp2~0feisty1_i386.deb
    Package:    mkcls_2.0.20030930gcc41-1nlp2~0feisty1_amd64.deb
moses
    Version:    20070717svn-2nlp1~0feisty1 (changes)

    moses (20070717svn-2nlp1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    moses_20070717svn-2nlp1~0feisty1.dsc
    Source (tar.gz):    moses_20070717svn-2nlp1~0feisty1.tar.gz
moses
    Description:    Moses: a factored phrase-based beam-search decoder for machine translation More...

    Moses is a statistical machine translation system that allows you to automatically train translation
    models for any language pair. All you need is a collection of translated texts (parallel corpus).
    * beam-search: an efficient search algorithm finds quickly the highest probability translation
    among the exponential number of choices
    * phrase-based: the state-of-the-art in statistical machine translation allows the translation of
    short text chunks
    * factored: words may have factored representation (surface forms, lemma, part-of-speech,
    morphology, word classes...)

    Features
    * Moses is a drop-in replacement for Pharaoh, the popular phrase-based decoder, with many extensions.
    * Moses allows the decoding of confusion networks, enabling easy integration with ambiguous
    upstream tools, such as automatic speech recognizers
    * Moses features novel factored translation models, which enable the integration linguistic and
    other information at many stages of the translation process

    For more information, visit <http://www.statmt.org/moses/>
    Package:    moses_20070717svn-2nlp1~0feisty1_i386.deb
    Package:    moses_20070717svn-2nlp1~0feisty1_amd64.deb
moses-doc
    Description:    Documentation for Moses More...

    Moses is a statistical machine translation system that allows you to automatically train translation
    models for any language pair. All you need is a collection of translated texts (parallel corpus).
    * beam-search: an efficient search algorithm finds quickly the highest probability translation
    among the exponential number of choices
    * phrase-based: the state-of-the-art in statistical machine translation allows the translation of
    short text chunks
    * factored: words may have factored representation (surface forms, lemma, part-of-speech,
    morphology, word classes...)

    Features
    * Moses is a drop-in replacement for Pharaoh, the popular phrase-based decoder, with many extensions.
    * Moses allows the decoding of confusion networks, enabling easy integration with ambiguous
    upstream tools, such as automatic speech recognizers
    * Moses features novel factored translation models, which enable the integration linguistic and
    other information at many stages of the translation process

    This package contains additional documentation for Moses.
    Package:    moses-doc_20070717svn-2nlp1~0feisty1_all.deb
nauty
    Version:    2.2-1nlp2 (changes)

    nauty (2.2-1nlp2) unstable; urgency=low

        * Renamed Nauty homepage file to nauty.html

    Source (dsc):    nauty_2.2-1nlp2.dsc
    Source (tar.gz):    nauty_2.2-1nlp2.tar.gz
nauty
    Description:    A program for computing automorphism groups of graphs and digraphs More...

    The world's fastest isomorphism testing program is Nauty, by Brendan D. McKay.
    Nauty (No AUTomorphisms, Yes?) is a set of very efficient C language procedures
    for determining the automorphism group of a vertex-colored graph. It provides
    this information in the form of a set of generators, the size of group, and the
    orbits of the group. Nauty is also able to produce a canonically-labeled
    isomorph of the graph, to assist in isomorphism testing. It was the basis of
    the first program to generate all the 11-vertex graphs without isomorphs, and
    can test most graphs of less than 100 vertices in well under a second. Nauty
    has been successfully ported to a variety of operating systems and C compilers.
    It may be obtained from [http://cs.anu.edu.au/people/bdm/](http://cs.anu.edu.au/people/bdm/). It is free for
    educational and research applications, but for commercial use contact the
    author at [EMAIL="bdm@cs.anu.edu.au"]bdm@cs.anu.edu.au[/EMAIL].

    Description courtesy of The Stony Brook Algorithm Repository
    <http://www.cs.sunysb.edu/~algorith/index.html>
    Package:    nauty_2.2-1nlp2_i386.deb
    Package:    nauty_2.2-1nlp2_amd64.deb
python-chasen
    Version:    0.01-1nlp2~0feisty1 (changes)

    python-chasen (0.01-1nlp2~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-chasen_0.01-1nlp2~0feisty1.dsc
    Source (tar.gz):    python-chasen_0.01-1nlp2~0feisty1.tar.gz
python-chasen
    Description:    Python interface to ChaSen More...

    python-chasen is a python interface for the Japanese morphological analyzer,
    ChaSen.

    ChaSen is a morphological analysis system. It reads Japanese sentences from
    the standard input, segments them into morpheme sequences, and outputs them
    to the standard output with many additional pieces of information
    (pronunciation, semantic information, etc).

    For more information, see [http://www.chasen.org/](http://www.chasen.org/) (available in Japanese only).
    Package:    python-chasen_0.01-1nlp2~0feisty1_i386.deb
    Package:    python-chasen_0.01-1nlp2~0feisty1_amd64.deb
python-nltk-lite
    Version:    0.7.3-5nlp1~0feisty1 (changes)

    python-nltk-lite (0.7.3-5nlp1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-nltk-lite_0.7.3-5nlp1~0feisty1.dsc
    Source (tar.gz):    python-nltk-lite_0.7.3-5nlp1~0feisty1.tar.gz
python-nltk-lite
    Description:    Natural Language Toolkit Lite More...

    The Natural Langauge Toolkit (NLTK-Lite) is a Python package for
    processing natural language text. It was developed as a simpler,
    lightweight version of NLTK. NLTK-Lite requires Python 2.4 or higher.

    For more information, see the project homepage:
    <http://nltk.sourceforge.net>
    .
    Package:    python-nltk-lite_0.7.3-5nlp1~0feisty1_i386.deb
    Package:    python-nltk-lite_0.7.3-5nlp1~0feisty1_amd64.deb
python-nltk-lite-corpora
    Version:    0.7.3-2nlp1~0feisty1 (changes)

    python-nltk-lite-corpora (0.7.3-2nlp1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-nltk-lite-corpora_0.7.3-2nlp1~0feisty1.dsc
    Source (tar.gz):    python-nltk-lite-corpora_0.7.3-2nlp1~0feisty1.tar.gz
python-nltk-lite-corpora
    Description:    Natural Language Toolkit Lite Corpora More...

    The Natural Langauge Toolkit (NLTK-Lite) is a Python package for
    processing natural language text. It was developed as a simpler,
    lightweight version of NLTK. NLTK-Lite requires Python 2.4 or higher.

    For more information, see the project homepage:
    <http://nltk.sourceforge.net>

    This package contains corpora for use with NLTK-Lite.
    Package:    python-nltk-lite-corpora_0.7.3-2nlp1~0feisty1_all.deb
python-nltk-lite-doc
    Version:    0.7.3-1~0feisty1 (changes)

    python-nltk-lite-doc (0.7.3-1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-nltk-lite-doc_0.7.3-1~0feisty1.dsc
    Source (tar.gz):    python-nltk-lite-doc_0.7.3-1~0feisty1.tar.gz
python-nltk-lite-doc
    Description:    Natural Language Toolkit Lite Documentation More...

    The Natural Langauge Toolkit (NLTK-Lite) is a Python package for
    processing natural language text. It was developed as a simpler,
    lightweight version of NLTK. NLTK-Lite requires Python 2.4 or higher.

    For more information, see the project homepage:
    <http://nltk.sourceforge.net>

    This package contains documentation for NLTK-Lite.
    Package:    python-nltk-lite-doc_0.7.3-1~0feisty1_all.deb
python-pywordnet
    Version:    2.0.1-1nlp2~0feisty1 (changes)

    python-pywordnet (2.0.1-1nlp2~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-pywordnet_2.0.1-1nlp2~0feisty1.dsc
    Source (tar.gz):    python-pywordnet_2.0.1-1nlp2~0feisty1.tar.gz
python-pywordnet
    Description:    Python interface to WordNet 2.0 More...

    PyWordNet is a Python interface to the WordNet database
    of word meanings and lexical relationships[1].

    PyWordNet presents a concise interface to WordNet,
    that allows the user to type expressions such as
    N['dog'], hyponyms(N['dog'][0]), and
    closure(ADJ['red'], SYNONYM) to query the database.

    >>> N['dog']
    dog(n.)
    >>> N['dog'].getSenses()
    ('dog' in {noun: dog, domestic dog, Canis familiaris},
    'dog' in {noun: frump, dog}, 'dog' in {noun: dog},
    'dog' in {noun: cad, bounder, blackguard, dog, hound, heel},
    'dog' in {noun: pawl, detent, click, dog},
    'dog' in {noun: andiron, firedog, dog, dogiron})

    For more information, see [http://sourceforge.net/projects/pywordnet](http://sourceforge.net/projects/pywordnet)
    Package:    python-pywordnet_2.0.1-1nlp2~0feisty1_i386.deb
    Package:    python-pywordnet_2.0.1-1nlp2~0feisty1_amd64.deb
python-romkan
    Version:    0.02-2nlp2~0feisty1 (changes)

    python-romkan (0.02-2nlp2~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    python-romkan_0.02-2nlp2~0feisty1.dsc
    Source (tar.gz):    python-romkan_0.02-2nlp2~0feisty1.tar.gz
python-romkan
    Description:    Romaji <-> Kana conversion module for Python More...

    python-romkan is a Python rewrite of the Text::Romkan Romaji <-> Kana conversion Perl module.
    Package:    python-romkan_0.02-2nlp2~0feisty1_i386.deb
    Package:    python-romkan_0.02-2nlp2~0feisty1_amd64.deb
srilm
    Version:    1.5.2-2nlp1~0feisty1 (changes)

    srilm (1.5.2-2nlp1~0feisty1) feisty; urgency=low

        * Ported to feisty.

    Source (dsc):    srilm_1.5.2-2nlp1~0feisty1.dsc
    Source (tar.gz):    srilm_1.5.2-2nlp1~0feisty1.tar.gz
srilm
    Description:    The SRI Language Model Toolkit More...

    SRILM is a toolkit for building and applying statistical language models (LMs),
    primarily for use in speech recognition, statistical tagging and segmentation.
    It has been under development in the SRI Speech Technology and Research
    Laboratory since 1995.

    SRILM consists of the following components:

    * A set of C++ class libraries implementing language models, supporting data
    stuctures and miscellaneous utility functions.
    * A set of executable programs built on top of these libraries to perform
    standard tasks such as training LMs and testing them on data, tagging or
    segmenting text, etc.
    * A collection of miscellaneous scripts facilitating minor related tasks.

    For more information, visit <http://www.speech.sri.com/projects/srilm/>
    Package:    srilm_1.5.2-2nlp1~0feisty1_i386.deb
    Package:    srilm_1.5.2-2nlp1~0feisty1_amd64.deb
srilm-dev
    Description:    The SRI Language Model Toolkit More...

    SRILM is a toolkit for building and applying statistical language models (LMs),
    primarily for use in speech recognition, statistical tagging and segmentation.
    It has been under development in the SRI Speech Technology and Research
    Laboratory since 1995.

    SRILM consists of the following components:

    * A set of C++ class libraries implementing language models, supporting data
    stuctures and miscellaneous utility functions.
    * A set of executable programs built on top of these libraries to perform
    standard tasks such as training LMs and testing them on data, tagging or
    segmenting text, etc.
    * A collection of miscellaneous scripts facilitating minor related tasks.

    This package contains headers and other files used for development with SRILM.
    Package:    srilm-dev_1.5.2-2nlp1~0feisty1_i386.deb
    Package:    srilm-dev_1.5.2-2nlp1~0feisty1_amd64.deb
srilm-doc
    Description:    Documentation for the SRI Language Model Toolkit More...

    SRILM is a toolkit for building and applying statistical language models (LMs),
    primarily for use in speech recognition, statistical tagging and segmentation.
    It has been under development in the SRI Speech Technology and Research
    Laboratory since 1995.

    SRILM consists of the following components:

    * A set of C++ class libraries implementing language models, supporting data
    stuctures and miscellaneous utility functions.
    * A set of executable programs built on top of these libraries to perform
    standard tasks such as training LMs and testing them on data, tagging or
    segmenting text, etc.
    * A collection of miscellaneous scripts facilitating minor related tasks.

    This package contains additional documentation for SRILM.
    Package:    srilm-doc_1.5.2-2nlp1~0feisty1_i386.deb
    Package:    srilm-doc_1.5.2-2nlp1~0feisty1_amd64.deb
---------------------------------------------------------------------------------------------------------------------------
[http://scibuntu.sourceforge.net/](http://scibuntu.sourceforge.net/)
This is Scibuntu, Ubuntu Linux for scientists and science students. Scibuntu is a script that adds scientific programs and other convenient tools to the plain desktop Ubuntu.

Scibuntu 0.4-beta includes a graphical chooser where you can choose between lots of programs for differens scientific areas.
PACKAGES IN SCIBUNTU
acroread

acroread (7.0.1-0.0.ubuntu1) [multiverse] Adobe Acrobat Reader: Portable Document Format file viewer
acroread-plugins

acroread-plugins (7.0.1-0.0.ubuntu1) [multiverse] Plugins for Adobe Acrobat(R) Reader
binutils

binutils (2.16.1cvs20060117-1ubuntu2.1) [security] The GNU assembler, linker and binary utilities
bioperl

bioperl (1.4-1) [universe] Perl tools for computational molecular biology
blast2

blast2 (1:2.2.13.20051206-1ubuntu1) [universe] Basic Local Alignment Search Tool
build-essential

build-essential (11.1) informational list of build-essential packages
celestia

celestia (1.3.2-3.1ubuntu3) [universe] A real-time visual space simulation (KDE frontend)
cernlib

cernlib (2005.05.09.dfsg-4ubuntu1) [universe] almost complete set of Debian Cernlib packages
cernlib-base

cernlib-base (2005.05.09.dfsg-4ubuntu1) [universe] script to determine Cernlib library dependencies
cernlib-core

cernlib-core (2005.05.09.dfsg-4ubuntu1) [universe] Cernlib main libraries and programs
cernlib-core-dev

cernlib-core-dev (2005.05.09.dfsg-4ubuntu1) [universe] Cernlib development headers, tools, and static libraries
cernlib-extras

cernlib-extras (2005.05.09.dfsg-4ubuntu1) [universe] miscellaneous Cernlib programs unlikely to be used by many
cernlib-montecarlo

cernlib-montecarlo (2005.05.09.dfsg-4ubuntu1) [universe] Cernlib Monte Carlo libraries
chemtool

chemtool (1.6.7-2ubuntu2) [universe] Chemical structures drawing program
clustalw

clustalw (1.83-1) [multiverse] [Biology] Global multiple nucleotide or peptide sequence alignment
clustalx

clustalx (1.83-1) [multiverse] [Biology] GUI for clustalw
emacs21

emacs21 (21.4a-3ubuntu2) The GNU Emacs editor
g77

g77 (4:3.4.6-1) The GNU Fortran 77 compiler
gfortran

gfortran (4.0.3-1) [universe] The GNU Fortran 95 compiler
gnuplot

gnuplot (4.0.0-2.1) [universe] A command-line driven interactive plotting program
gpc

gpc (4:3.4.6-1) [universe] The GNU Pascal compiler
grace

grace (1:5.1.18-4ubuntu1) [universe] An XY plotting tool
gromacs

gromacs (3.3-2) [universe] Molecular dynamics simulator, with building and analysis tools
gromacs-doc

gromacs-doc (3.3-2) [universe] GROMACS molecular dynamics sim, documentation
gs

gs (8.15-4ubuntu3) Transitional package
gv

gv (1:3.6.1-12) [universe] PostScript and PDF viewer for X
ipython

ipython (0.7.1.fix1-1ubuntu) [universe] enhanced interactive Python shell [dummy package]
kile

kile (1:1.8.1-3.2ubuntu1) [universe] KDE Integrated LaTeX Environment
labplot

labplot (1.5.0.5-1ubuntu1) [universe] data plotting and function analysis tool for KDE
mozilla-acroread

mozilla-acroread (7.0.1-0.0.ubuntu1) [multiverse] Adobe Acrobat(R) Reader plugin for mozilla / konqueror
ncbi-tools-bin

ncbi-tools-bin (6.1.20051206-1ubuntu1) [universe] NCBI libraries for biology applications (text-based utilities)
ncbi-tools-x11

ncbi-tools-x11 (6.1.20051206-1ubuntu1) [universe] NCBI libraries for biology applications (X-based utilities)
octave

octave (1:2.1.72-8) [universe] GNU Octave language for numerical computations (2.1 branch)
openbabel

openbabel (1.100.2-4) [universe] Convert and manipulate chemical data files
pymol

pymol (0.98-1ubuntu2) [universe] An OpenGL Molecular Graphics System written in Python
python-biopython

python-biopython (1.41-1ubuntu2) [universe] Python library for bioinformatics
python-matplotlib

python-matplotlib (0.82-5ubuntu1) [universe] python based plotting system in a style similar to Matlab
python-scipy

python-scipy (0.3.2-8ubuntu2) [universe] scientific tools for Python
qalculate-gtk

qalculate-gtk (0.9.2-1) [universe] Powerful and easy to use desktop calculator - GTK version
rasmol

rasmol (2.7.2.1.1-3ubuntu3) [universe] Visualize biological macromolecules
r-base

r-base (2.2.1-2) [universe] GNU R statistical computing language and environment
sharutils

sharutils (1:4.2.1-15) shar, unshar, uuencode, uudecode
sysutils

sysutils (2.0.1) Miscellaneous small system utilities - dummy package
t-coffee

t-coffee (2.50-1) [universe] [Biology] Multiple Sequence Alignment
tetex-base

tetex-base (3.0-15build1) Basic library files of teTeX
tetex-bin

tetex-bin (3.0-13ubuntu6) The teTeX binary files
tetex-extra

tetex-extra (3.0-15build1) Additional library files of teTeX
tree-puzzle

tree-puzzle (5.2-1) [universe] [Biology] Reconstruction of phylogenetic trees by maximum likelihood
wxmaxima

wxmaxima (0.6.4-1ubuntu1) [universe] a wxWidgets GUI for the computer algebra system maxima 
---------------------------------------------------------------------------------------------------------------------------
newest version of wine
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
---------------------------------------------------------------------------------------------------------------------------
to play encrypted dvds
sudo apt-get install  libdvdread3

more info here
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html)

also medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

sudo apt-get install libdvdcss2

also this web site has goodies too
[http://debian.video.free.fr/index.html](http://debian.video.free.fr/index.html)
If you can't move to etch the new stable branch, add the following URL in you sources.list :
deb [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) sarge main 

Which is the difference between the official mplayer package and the one here ?

Here is the output of the configure script for i386 (only disabled options).

Official package :
Disabled optional drivers :
Input : vstream radio live555 mpdvdkit2 dvdnav smb
Codecs : x264 xvid libdv amr_wb amr_nb faac musepack twolame toolame
Audio output : sun openal jack polyp arts ivtv dxr2 nas
Video output : winvidix bl zr zr2 ivtv dxr3 dxr2 vesa aa ggi tdfx_vid s3fb

debian-multimedia package :
Disabled optional drivers :
Input : libdvdcss
Codecs : toolame
Audio output : sun ivtv dxr2
Video output : winvidix bl zr zr2 ivtv dxr2 vesa tdfx_vid 3dfx

==================
 Won't play encrypted dvds even with libdvdcss2 installed.
Okay, well it's fixed now; the problem was totem wasn't able to use libdvdcss.

A "sudo ldconfig" fixed it,

==================
also if that fails, uninstall the codecs etc with automatix or how ever you installed, then reinstall codecs. i had too. now it works
---------------------------------------------------------------------------------------------------------------------------
if you want a right click open command prompt do this
sudo apt-get install nautilus-open-terminal 
---------------------------------------------------------------------------------------------------------------------------
Superuser its the root .... to get a root terminal with superuser privileges do:
$ su
 $ password: rootpassword
if you don't have a root password first need to do:
$sudo passwd root
 $New Password: typeyourpassword
 $Retype password: Again
thats all you have to do before "dpkg --configure -a"
---------------------------------------------------------------------------------------------------------------------------
Ubuntu Ultimate repository

[http://repoubuntusoftware.info/](http://repoubuntusoftware.info/)


contains these packages
2h4u 2h4u-data 3v1n0-sources-list abe abe-data accelerator3d
  acroread acroread-escript acroread-plugins actioncube afterbirth
  alienarena2007 alsa-oss amarok amarok-engines amarok-xine amaya
  amoebax amoebax-data amsn angrydd app-install-data ardour
  armagetronad asc asc-data astromenace audacity automatix2
  automatix2bleeder avant-window-navigator avidemux azureus balder2d
  balder2d-data ballz basic256 berusky berusky-data beryl beryl-core
  beryl-dev beryl-manager beryl-plugins beryl-plugins-data beryl-
  plugins-unsupported beryl-plugins-unsupported-data beryl-plugins-
  unsupported-dbg beryl-settings beryl-settings-bindings beryl-
  settings-simple beryl-vidcap bibledave bibus bibus-doc-en
  blinkensisters blobandconquer blobandconquer-data blobby blueclock
  boinc-client boinc-manager boswars boswars-data brasero briquolo
  briquolo-data bum bumprace bumprace-data canorus catfish cgmail
  checkinstall columba compiz compiz-config-gnome compiz-config-ini
  compiz-core compiz-dev compiz-extra-plugins compiz-freedesktop
  compiz-gtk compiz-kde compiz-plugins computertemp conduit crimson
  dangerdeep dark-oberon dark-oberon-data deluge-torrent desktop-data-
  manager devede dirac disksearch divfixplusplus dosbox drapes
  dreamchess dreamchess-data emacs-snapshot-bin-common emacs-snapshot-
  common emacs-snapshot-gtk emelfm2 emerald emerald-dbg emerald-themes
  emesene envy epdfview exaile extrema f-spot faac faad ffmpeg fglrx-
  control fglrx-kernel-source fglrx-sources filezilla filezilla-common
  filezilla-locales flashplayer-nonfree flashplugin-nonfree flock
  freecol frostwire funnyboat fuse-utils fuzzy gajim gbtsco geany
  gfreqlet gftp gftp-common gftp-gtk gftp-text ghex gimmie gimmix
  gimp-ufraw gkrellm glchess glest glest-data glob2 glob2-data
  gmusicbrowser gnome-app-install gnome-hideseek gnome-mastermind
  gnome-mplayer gnome-subtitles gnomeradio googleearth goonies gospy-
  applet gossip gourmet gparted gpg-crypter gqview grandr-applet
  graphmonkey graphthing gridwars gsfonts-other gsfonts-x11 gssmp gstm
  gstreamer0.10-pitfdll gsynaptics gtetrinet gtk-recordmydesktop
  gtweakui gtwitter gurlchecker gwget gxine gxineplugin hal hal-
  device-manager hal-info hannah happydigger hardinfo hedgewars
  hedgewars-data heliodor heliodor-dbg heliodor-dev hipo hot-babe
  hydrogen iceape-browser iceape-calendar iceape-chatzilla iceape-
  mailnews incollector isomaster istanbul istream java-common
  jdiskreport k3b kaffeine kalva kchmviewer kcometen3 kdebase-kio-
  plugins kflickr-mt kftpgrabber kino kipi-plugins kmediafactory
  kmobiletools kompozer konversation kplayer ktorrent lame
  ldapexplorertool leafpad lemonrip lftp lg3d-core lg3d-java3d lg3d-
  jdk libavcodec0d libavcodeccvs51 libavformat0d libavutilcvs49
  libberyldecoration0 libberylsettings-dev libberylsettings0
  libberylsettings0-dbg libberylsettings0-gconf libcairo2 libcairo2-
  dev libdecoration0 libdirac0 libdivx0-binary libdivxdecore0-binary
  libdivxencore0-binary libdvdcss2-dev libdvdplay0 libdvdread3
  libemeraldengine-dev libemeraldengine0 libemeraldengine0-dbg
  libexiv2-0.12 libfaac-dev libfaac0 libfaad2-0 libfaad2-dev
  libfreetype6 libfreetype6-dev libfuse2 libglitz-glx1 libglitz1
  libgnome-compiz-manager0 libgnome-compiz-manager0-dev libgpod0
  libgpod1 libhal-storage1 libhal1 libk3b2 libk3b2-mp3 liblame-dev
  liblame0 libltdl3 libmjpegtools0 libmono-cairo1.0-cil libmono-
  corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-
  security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-
  system1.0-cil libmono-system2.0-cil libmono2.0-cil libmp4v2-0
  libmusicbrainz4c2a libnm-glib0 libntfs-3g0 libntfs-3g2 libntfs8
  libportaudio0 libpostproc0d libpostproccvs51 librte1 libseom
  libseom-dev libspeex1 libtwolame-dev libtwolame0 libxft-dev libxft2
  libxss1 libxvidcore4 liferea liferea-mozilla lives lybniz m4 magicor
  make-jpkg-mustang mandvd maniadrive maniadrive-data marble marble-
  data mednafen megamario mencoder mesa-utils mesk metamorphose
  mhwaveedit mirage misfitmodel3d monkeymessenger mozilla-mplayer
  mplayer mplayer-doc msttcorefonts mtpaint multiget mysql-admin
  mysql-admin-common nautilus-image-converter nautilus-search-tool
  news-notification nicotine nikwi nikwi-data notecase ntfs-3g ntfs-
  config ntfsprogs ntfstools odbcinst1debian1 ogmrip openarena
  openldev openyahtzee pagenda pandodl pangzero pcmanfm pdfedit
  pengupop picasa pidgin pidgin-guifications pidgin-libnotify plarpebu
  pmount pokerth polypuzzle projectx psxrip pterm putty putty-tools
  python-launchpad-bugs python-wxversion pytraffic pytraffic-data
  qcomicbook qlandkarte quodlibet radrails rawstudio rdesktop
  reconstructor recordmydesktop referencer revelation rgbpaint
  rhythmbox ripdvd rocksndiamonds sauerbraten sauerbraten-data
  sauerbraten-server scourge scourge-data scribes searchmonkey
  secondlife-install seom shared-mime-info sharpconstruct-0.12-1sbx
  skype skype-gnome smc smc-data smplayer sonata songbird specto
  sportstracker sqliteman squeeze startupmanager stax straw
  subtitleeditor sum sun-j2re1.5 sun-java6-bin sun-java6-jre sun-
  java6-plugin supertux supertux-data sweep symbolica symbolica-data
  t1-xfree86-nonfree taskbar-compiz tea tea-data tellico tellico-data
  thunderbird-locale-en-gb timer-applet tomatoes tomatoes-data tomboy
  tovid toycars toycars-data transmission trix tsclient ttf-dustin
  ttf-f500 ttf-fossfonts ttf-isabella ttf-larabie-deco ttf-larabie-
  straight ttf-larabie-uncommon ttf-staypuft ttf-summersby ttf-ubuntu-
  title twolame ubuntu-apt-utils ubuntu-devel ubuntu-multimedia-gnome
  ufoai ufoai-data ufraw unace unixodbc update-manager update-manager-
  core usbsink usplash-switcher vcdgear vdrift vdrift-full vdrift-
  minimal vertris virtualbox volleyball volleyball-data w32codecs
  warsow warsow-data warsow-server warzone2100 warzone2100-data
  webilder webilder-gnome wengophone wesnoth wesnoth-data wesnoth-
  music wesnoth-trow wesnoth-tsg wesnoth-ttb wesnoth-utbs wine
  wlassistant wpasupplicant wxdfast xarchiver xfonts-artwiz xfonts-
  intl-european xmlcopyeditor xmms-mp4 xmoto xmoto-data xorg-driver-
  fglrx xorg-driver-fglrx-dev xserver-xgl yamipod zim zsnes
---------------------------------------------------------------------------------------------------------------------------

Even if you use OpenOffice, you might still want all the Microsoft TrueType fonts so that documents created using Word or PowerPoint look as they were supposed to when you open them with OpenOffice. Also, with the Microsoft Fonts installed we browsing will be better since the pages will look as the designer originally intended them to. Most webpages are designed with Microsoft fonts in mind. The stylesheet specify these fonts. On Linux, when these specified fonts are not available on your computer, they are replaced with generic equivalents. With these fonts installed, you will see the page as it was designed. To install the fonts, all you need to do in Ubuntu is to install the msttcorefonts package. Instructions for installation are given below.

The Truetype Microsoft fonts provided by the package include:

Andale Mono 
Arial Black 
Arial (Bold, Italic, Bold Italic) 
Comic Sans MS (Bold) 
Courier New (Bold, Italic, Bold Italic) 
Georgia (Bold, Italic, Bold Italic) 
Impact 
Times New Roman (Bold, Italic, Bold Italic) 
Trebuchet (Bold, Italic, Bold Italic) 
Verdana (Bold, Italic, Bold Italic) 
Webdings 
Installing Microsoft Truetype fonts on Ubuntu
You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the &#8220;Universe&#8221; component of the repositories. This is done by default in Feisty. After you do that, use the following command from the command line:

$sudo apt-get install msttcorefonts

This will give you the core fonts, but if there are other TrueType fonts that you want installed, it is as easy as copying the font files to the ~/.fonts/ directory. 

After installing new fonts, you will have to log out and log in again to be able to see and use the new fonts. If you want to avoid this, you can regenerate the fonts cache by issuing the following command:

$sudo fc-cache -fv

---------------------------------------------------------------------------------------------------------------------------
and for doom , hexen, heretic, make sure to use doomsday

Re: Doomsday engine, has anyone gotten this to work? 

---------------------------------------------------------------------------------------------------------------------------

I did specify the iwad path for prboom and it works... but just for the first room! As i try to shoot the first enemy the game freezes and i have to close it!! Lxdoom instead is semi -transparent if i use emeral as window manager but it works with metacity! Remember: i think the problem with these two ports is beryl, so if you didn't install it you should have no problem!

To install doomsday on feisty however you just have to add these who lines to your /etc/apt/sources.list:

#doom 3d! HEHEHHEHEH! Thanks Yagisan!
deb [http://eyagi.bpa.nu/~jamie/ubuntu]("http://eyagi.bpa.nu/%7Ejamie/ubuntu") current main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu]("http://eyagi.bpa.nu/%7Ejamie/ubuntu") current main restricted universe multiverse

and then apt-get install deng-jdoom-ui and the iwad installer you need! I still miss the 3d effects even if i installed the deng-jdoom-rp packages, but i'll post here the solution when i'll find it!


---------------------------------------------------------------------------------------------------------------------------
handy serial terminal
apt-get install cutecom
---------------------------------------------------------------------------------------------------------------------------
handy printer config
sudo apt-get install system-config-printer

for printer drivers go here
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---------------------------------------------------------------------------------------------------------------------------
take ownership of your ntfs drives
[http://ubuntuforums.org/showthread.php?t=503400](http://ubuntuforums.org/showthread.php?t=503400)
---------------------------------------------------------------------------------------------------------------------------
setup samba to talk to windows machines
 sudo apt-get install samba smbclient smbfs
may need to sync passwords like this
 sudo smbpasswd -a "user"

where "user" is type in your username
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Regarding usernames and passwords:

You have your Samba user/pass, and your Linux user/pass. These need to be in sync.

To change the password you want to use when connecting from a Windows box, from a command prompt type

Quote:
sudo passwd username
sudo smbpasswd username
Substitute "username" with the name of the user account on the Linux machine you want to log in to from the Windows machine.

handy screencast here
[http://screencasts.ubuntu.com/SAMBA_Filesharing#comment-121](http://screencasts.ubuntu.com/SAMBA_Filesharing#comment-121)
also a tip - "You may have problems accessing your share from other computers afterwards. To fix this issue do the following things. Launch the run dialog by pressing Alt+F2. Enter the command gksudo gedit /etc/samba/smb.conf then enter your password when prompted. Find the security section of the configuration file. Change "user" to "share" and remove the semicolon from the start of the line. Find the guest account section. Change "nobody" to your account's username and remove the semi colon from the start of the line. Save the file and restart your computer"

Samba essential reading
[http://samba.org/samba/docs/man/Samba-Guide/](http://samba.org/samba/docs/man/Samba-Guide/)

---------------------------------------------------------------------------------------------------------------------------
if you need a convertor for all sorts of stuff use this
[http://joshmadison.com/software/convert/](http://joshmadison.com/software/convert/)
run it using wine. 
it may not display correctly and have lines everywhere. to fix this statup convert and then click options preferences then click the tab that says "tabs" and remove tick from "display multiple lines"  
---------------------------------------------------------------------------------------------------------------------------
free books that are VERY handy
[http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html](http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html)
---------------------------------------------------------------------------------------------------------------------------
if you have CHM files (compressed html files) to view so to synaptic program manager and search on chm view.select the gnome viewer & install
---------------------------------------------------------------------------------------------------------------------------
Install KDAR (Backup program) very handy
[http://ubuntuforums.org/showthread.php?t=500492&highlight=install+kdar+fiesty](http://ubuntuforums.org/showthread.php?t=500492&highlight=install+kdar+fiesty)

another handy thread on backup is this
[http://ubuntuforums.org/showthread.php?t=81311&highlight=kdar](http://ubuntuforums.org/showthread.php?t=81311&highlight=kdar)

handy tutorial on kdar
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)

---------------------------------------------------------------------------------------------------------------------------


incase your wondering here is my sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

#thunderbird 2 install
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird

#Wine update
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

#all sorts extra goodies like divx
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

#even more goodies about 47
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

#doomsday engine doom,hexen,heretic
deb [http://eyagi.bpa.nu/~jamie/ubuntu]("http://eyagi.bpa.nu/%7Ejamie/ubuntu") current main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu]("http://eyagi.bpa.nu/%7Ejamie/ubuntu") current main restricted universe multiverse

#allow install of KDAR.once you have got it put the hash back in front
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
---------------------------------------------------------------------------------------------------------------------------
i used to use the freeware version of syncback on my xp machine to keep my data backed up across multiple drives, i had a seperate program to back up to DVD with.
you can copy one directory from one to another like this

cp -vR /directory_to_be_copied /backup_disc

The R flag gives a recursive copy so all subfolders and contents get copied and the v (verbose) flag tells you what's going on.

But  you'll lose ownerships and permissions copying to a fat32 drive. That's OK for personal data files, but no good for system backups.

better yet, install wine and run the freeware version of syncback
[http://ubuntuforums.org/showthread.php?t=506827](http://ubuntuforums.org/showthread.php?t=506827)

after installing Ubuntu Ultimate i found that Syncback would install and try and run, but would abort the copy process.
so i went looking for a replacement.goto Applications and add/remove programs. search on grsync and install it.
homepage for grsync [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---------------------------------------------------------------------------------------------------------------------------
Have you got a Windows machine that needs access to a Linux Ext2 Partition???
This little ripper will do the job and you get read/write access and its free
[http://www.fs-driver.org/](http://www.fs-driver.org/)
---------------------------------------------------------------------------------------------------------------------------
another handy ubuntu s/w site is this one
[http://www.getdeb.net/](http://www.getdeb.net/)
---------------------------------------------------------------------------------------------------------------------------
 apt-get can it save files so you can burn them to disc 
[http://ubuntuforums.org/showthread.php?p=3060988#post3060988](http://ubuntuforums.org/showthread.php?p=3060988#post3060988)
---------------------------------------------------------------------------------------------------------------------------
mounting windows partition in ubuntu
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

and this will also help
Windows NTFS partitions easy read/write
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
---------------------------------------------------------------------------------------------------------------------------
dont forget a copy of iso master
[http://littlesvr.ca/isomaster/index.php](http://littlesvr.ca/isomaster/index.php)
SO Master is an open-source, easy to use, graphical CD image editor for Linux and BSD. Basically you can use this program to extract files from an ISO, add files to an ISO, and create bootable ISOs - all in a graphical user interface. It can open both ISO and NRG files but can only save as ISO.


there is also this handy iso util
kiso
sudo apt-get kiso


---------------------------------------------------------------------------------------------------------------------------
Handy tips for beginners
#1] The man command:

If you ever need help regarding a program, or even a basic command in Linux, simply type man, and then the name of the command.

eg. man ls

Man pages are like help pages. And they are way easier to read then doing something like this &#8220;ls &#8211;?&#8221;. They are well laid out, and often times have examples of how to use the commands.

Man pages aren&#8217;t just good for looking up commands, they are also amazing for looking up coding information. For example, if you are curious about a system function in c++, there are usually man pages for that too. Try it out, and open a new world of learning in the Unix environment.

#2: apropos

The apropos command is fantastic. Once you use it once, you will never be able to go back. I guarantee it.

If you ever forget a command at the terminal, all you have to do is type apropos, and then any keyword that has something to do with that command. For example, if you wanted to list the contents of the directory that you were currently in, but you forgot what the command was, all you have to do is type:

apropos directory

This will give you all of that commands that have something to do with directories.

#3: ls

If you tried the apropos trick above, you would have found out that the command ls, is just like the command &#8220;dir&#8221; in dos. It lists the entire contents of the current directory, or if you add some extra parameters, any other directory in the system. Try typing &#8220;man ls&#8221; and see if you can figure out how to list the directories in colour.

#4. Find hidden files:

In Linux there are a lot of times when you will need to edit a hidden file to configure applications. Most hidden files on a Unix machine start with a period. So for example, if you had the file myfile.doc and you wanted to make it hidden, you could simply rename it to .myfile.doc and the system would recognize it as hidden. To see the hidden files that currently reside in the directory that you are in, type &#8220;ls -a&#8221;

5. Change directories

The command &#8220;cd&#8221; is the exact same as it was in dos. To get to a certain directory on your computer, simply type &#8220;cd&#8221; and then the name of the directory. There are some cool tricks that you might not know about. &#8220;cd -&#8221; takes you back to the previous directory that you were in, and is a great way to toggle between two directories that you are working in on the system. &#8220;cd ..&#8221; will take you one directory up.

6. Copying files:

The command is not copy like it was in dos, it&#8217;s &#8220;cp&#8221;. &#8220;cp&#8221; can copy files from one place to another in your file system. However, if you are trying to copy a directory, you will need to add the &#8220;-r&#8221; flag to the &#8220;cp&#8221; command, to make sure that it gets all of the subdirectories below it. &#8220;-r&#8221; stands for recursive.

eg. &#8220;cp -r ./mydirectory /home/users/dan&#8221; will move the entire contents and subfolders of my directory to the folder /home/users/dan

7.] Moving files

The command is not &#8220;move&#8221; it&#8217;s &#8220;mv&#8221;. Moving files is way faster than copying them, because all the system has to do is tell the harddrive that the file is located in a different directory, in most cases, nothing really needs to actually be moved around on the hard drive. That&#8217;s why this command is so popular.

Simply type &#8220;mv&#8221; then the name of the file and the destination. For more help on this command simply type &#8220;man mv&#8221;.

8.] Deleting files:

In Linux deleting files is done by using the command &#8220;rm&#8221;. Be careful with this one, because although there are ways of getting your deleted files back, it&#8217;s not as easy as using apple&#8217;s time machine, or even windows Recycling bin. If you are looking to delete an entire directory, you will need to use the &#8220;-r&#8221; command. This stands for recursive, which means, all of the sub directories.

9.] Create a directory:

&#8220;mkdir&#8221; is the command to create a directory. Simply type in &#8220;mkdir&#8221; then the name of the directory you wish to create, and it will be done.

10. Find a file on your system.

I cannot tell you how many times I have forgotten how to do this on Linux. So here it is. If you are looking for a file on the system simply type:

locate &#8220;filename&#8220;

the command is easy to use, and it finds your file for you in a sec. even if you have not written the entire name. it will search the entire drive

++++++++++++++++++++++++
    * The Linux equivalent of MicrosoftWindows' ipconfig command is ifconfig(8).
    *

      The (8) in the above line refers to the manual page for ifconfig in manual section 8, accessible by typing man 8 ifconfig
          o Other man pages can be accessed by typing man command (See man man for the man manual)
          o Man pages are searchable, type man -k keyword to search the man pages containing that keyword. Think of it as a pre google, google search.
    * Global system configuration files are in the /etc directory.
    *

      Under Debian-based distributions (such as Debian Sarge, Ubuntu, etc):
          o Install Deb Packages using dpkg -i filename. See dpkg(8).
          o To search for packages available on your distribution, use aptitude search name
          o To install a package, and any other packages it depends on, use aptitude install name
          o Note that names are case insensitive, and contain no spaces. Try doing a substring search if you can't find it at first. Debian has over 15000 packages, so there is a good chance it already has what you want.
    *

      Under RedHat-based distributions:
          o Install RPM Packages using rpm -Uvh filename. See rpm(8).
          o RedHat based systems now offer better PackageManagementTools? such as AptForRpm or Yum. Use them instead of manually finding .rpms and installing them
    * Use tar xzvf filename to decompress a .tar.gz or .tgz file, otherwise known as a TarBall. See tar(1)
    * Use tar xjvf filename to decompress a .tar.bz2 also known as a TarBall. See tar(1)
    * Don't get involved in emacs(1) vs. vi(1) arguments. Use nano(1), pico(1), joe(1), or jed(1) for your initial editing needs. Once you have gotten a little more comfortable with the system, however, be sure to revisit emacs(1) and vi(1) as they offer tons of power you will never get with the simple minded editors. For the latter, Vim is the suggested clone, which comes with a vimtutor program that should get your over the initial hurdles quickly. Does any equivalent for emacs(1) exist?
    * Before you ask for help online, be sure to read the documentation first. It is sometimes difficult to understand so don't feel bad if you don't get it, just make the attempt. It will either make any explanation you get from someone else clearer, or the explanation will help you understand the documentation. Next time you look at it, the documentation will be less puzzling. If you repeat this a couple times, then you'll soon be cruising along with the docs just fine.
    * If your desktop locks up, Ctrl-Alt-Backspace will kill the graphical environment (the XServer, in technical terms) and drop you to the Shell (or your display manager) without having to reboot the system.
    * You don't have to worry about defragmenting your disks.
    * You don't have to worry about defragmenting your memory.
    * You don't have to worry about mail Worms.
    * Linux will crash on you at some point. It happens, no matter what anybody says. However, it won't happen nearly as much as it does on MicrosoftWindows.
    * You don't have to shut down or restart every day. It's ok to leave a Linux system running for a week or more (some users have their system running for months at a time). You should still conserve electricity, tho.
    * There is no way to undelete a file in Linux. You deleted it, it's gone. See rm(1)
    * sudo(1) will let you execute a command with SuperUser (or any other) privileges; it may need to be configured, in that case, see SudoHowto. If you really need a root shell, you can use su(1): execute su - and type the root password. You should never log in as root (except if you managed to get the system so shot up that you can't log in as a user).
    *

      Installing a program from source is easier than you think. The sequence is usually along the lines of

          tar xvzf filename-version.tar.gz
          cd filename-version
          ./configure && make
          sudo make install

      Note you have to be root for the make install step if you are installing into system wide directories. You can always install to your home directory, of course -- which you need to indicate by saying ./configure --prefix=$HOME on the relevant step. You can also pass many more options, to configure, most of which needn't concern you, except for the (usually few) --enable-foo/--disable-foo and --with-bar/--without-bar which let you hand-pick features to include or omit from the resultant build of the software.
    * Make sure you are working on the correct drive when doing any FileSystem level work -- nuking the wrong partition or disk is annoying to say the least.
    * Learn how to use redirection ("<", ">") and pipes ("|") in the Shell. See bash(1)
    *

      Your initial WindowManager settings are (generally) stored in the .xinitrc or .xsession file in your home.
          o Note that this isn't so relevant any more with GNOME and KDE

Handy Ubuntu Tips
Write a bash script.

Open up your favourite text editor and add this line to the top:

    * #!/bin/bash

Now add your bash commands and at end of each line add a ";" Save you file and make sure you chmod to give execute permissions.
Extract zips that are in multiple parts.

*unzip -d destdir/ \*.zip

REMEMBER : The '\' is the escape character. Without it, our command would look like: unzip -d destdir/ 1.zip, 2.zip, 3.zip which is bad because after the first zip argument, the following stuff is read as list arguments. With \*.zip bash doesn't interpret the * but unzip does.
Extract rars that are in multiple parts (Using Rar Linux) (eg: .rar,.ro1,r02...)

    * unrar name.rar destdir/

Note: We only need to supply the file with the ".rar" extension. Rar is smart and detects the other files.
Cool tools to play around with

    * cal

Typing this command will display a calendar with the date highlighted.

    * date

Will display the date and time in terminal.

    * dmesg

Displays log of messages printed to the screen during the boot process
Where on Earth are the rename and copy commands?

    * We use the "mv" command when renaming instead.

e.g mv dog cat This will rename the file "dog" to "cat".

    * The cp(1) command copies files. The -a switch is for copying directories.

You can copy/move/list multiple things at a time! Just separate files/expressions with a space.

    * ls -l *.txt *.letter
    * cp *.jpg *.bmp ~/pics/

How to Stop listing dir contents when using glob expressions with ls.

Use the -d switch to list just the directories, and not the contents of each matching directory.
Change Password

Simply type "passwd". You will be prompted for the current password and then asked to type in a new password.
Jump quickly between words in terminal

    * Alt-f - Move forward one word.
    * Alt-b - Move backward one word.

Print to screen first/last few lines of a file.

    * head -n 20 test.txt

Will print to the screen the first 20 lines in test.txt

    * tail -n 5 test.txt

Will print to the screen the last 5 lines in test.txt
Print a Message To The Terminal

    * echo Damn you rock Staz

Note : Make sure to type the above exactly as it is written.

    * echo $PATH

Slightly more useful!
Display a long file to screen

    * more test.txt

Will print the first page of test.txt to the screen, and you can use arrow keys to navigate further.

    * less test.txt

A more advanced version of more. (Can do Searches etc).
Search command History

    * Alt-r

Now Start typing part of the command any matches will be displayed as you type and press enter to use them.
What type of file is that??

    * file <filename>

Will return the file type.
Reload fstab file

    * sudo mount -a

This mounts everything in your fstab file.
How much disk space is the contents of this directory using?

1)All Folders/Subfolders

    * du -h

2)The current directory

    * du -sh

3)All folders excluding subfolders.

    * du --max-depth=1 -h

4)All folders beginning with the letter P

    * du -sh P*

Mount Samba Shares

We need to get the smbfs and smbclient packages.

    * sudo aptitude install smbfs
    * sudo aptitude install smbclient

First lets get a list of the available shares on a particular machine.

    * smbclient -L <IP/HOST>

Now create a folder in /media/ that will be the mount point for your samba share. There are two ways of mounting: 1.

    * sudo smbmount //<IP/Hostname>/smbshare /media/mounthere/ -o username=YYYY,password=YYYY,dmask=XXX,fmask=XXX

2.

    * sudo mount -t smbfs //<IP/Hostname>/smbshare /media/mounthere/ -o username=YYYY,password=YYYY,dmask=XXX,fmask=XXX

dmask = directory umask fmask = file umask

Now to unmount:

    * sudo umount/smbumount /media/diryoumountedto/

Add a smb share to fstab that is automatically mounted on boot

    * sudo /etc/fstab

Add this line: //HOST/share/ /mount/point/ smbfs auto,username=xxxxx,password=xxxxx,uid=xxxx This website is really good: [http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)
Mount all smb shares listed in fstab

    * sudo mount -at smbfs

Unmount all smb shares listed in fstab

    * sudo mount -at smbfs

List NTFS Mounted Drives

    * sudo mount -t ntfs

If you want to view mounted fat32 drives simply replace "ntfs" with "vfat"
How much memory is free?

    * free -m

Will tell you how much free memory is available in megabytes.

    * free -s 60

Will tell you how much free memory is available every 10 seconds.
List all your drives

    * sudo fdisk -l

NOTE : Don't forget the "sudo" or else you may not see anything listed. Blocks can be read to mean "Kilobytes"
List Drives/Capacity/Free Space

    * df -B M

The -B switch refers to Block Size. The M means it will be displayed in Megabytes. But if you prefer use K for kilobytes, G for gigabytes etc..

df(1) doesn't require root privileges to work. Also "df -h" will select the right units for you. Many programs that support outputting units will support "-h" for "human readable". The other useful command here is du(1).
Install an app from .rpm

First you need Alien: sudo aptitude install al

---------------------------------------------------------------------------------------------------------------------------
The one page linux manual full of very handy stuff
[http://homepage.powerup.com.au/~squadron/]("http://homepage.powerup.com.au/%7Esquadron/")
---------------------------------------------------------------------------------------------------------------------------
looking for a clock screen saver? Ubuntu does not come with one standard, but follow this and you can have one for nix!
go to Synaptic, search for screensaver.

Install:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra

From a terminal run:

xscreensaver

  click on 'settings'
   select GLText (clock)
    click on setttings
     modify the text to what you want it to be, example:
     My own System%n%n%A%n%d %b

Follow the screensaver instructions in:
[https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu)
to apply permanently.
---------------------------------------------------------------------------------------------------------------------------
if you need a picture viewer similar to ACDSEE then Gwenview is for you
[http://gwenview.sourceforge.net/news](http://gwenview.sourceforge.net/news)
easy to install from command prompt
sudo apt-get install gwenview
---------------------------------------------------------------------------------------------------------------------------
windows alternative project find linux alternatives to windows packages
[http://www.linuxalt.com/](http://www.linuxalt.com/)
---------------------------------------------------------------------------------------------------------------------------
some thought provoking sites as to why change to Linux
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)
[http://www.reichel.net/opensource/linuxtop10.html](http://www.reichel.net/opensource/linuxtop10.html)
[http://www.getgnulinux.org/](http://www.getgnulinux.org/)
---------------------------------------------------------------------------------------------------------------------------
Windows file monger equalivent
[http://www.methylblue.com/filelight/](http://www.methylblue.com/filelight/)
[http://www.jgoodies.com/freeware/jdiskreport/index.html](http://www.jgoodies.com/freeware/jdiskreport/index.html)
---------------------------------------------------------------------------------------------------------------------------
Change default file manager in gnome
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)
---------------------------------------------------------------------------------------------------------------------------
assorted resources for ubuntu
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
---------------------------------------------------------------------------------------------------------------------------
diff and merge tool - meld
[http://meld.sourceforge.net/](http://meld.sourceforge.net/)
---------------------------------------------------------------------------------------------------------------------------
desktop mascot similar to tahni
[http://rosegray.sakura.ne.jp/macopix/index-e.html](http://rosegray.sakura.ne.jp/macopix/index-e.html)
---------------------------------------------------------------------------------------------------------------------------
If you download a CHM file(= Microsoft Compressed HTML Help", witch is a proprietary format), there is a lot of viewers for Linux(as xCHM, gnochm, kchmviewer, kchm), but I dont like how it works(so used to PDF).

The command based program CHMLIB can extract it for you, and very fast.

The program HTMLDOC can convert the extracted files to a PDF for you. HTMLDOC can also download urls as HTML, PS, PDF or Seperated HTML. Is great when you find a guide on the nett that you want to save.
---------------------------------------------------------------------------------------------------------------------------
desktop calendar
[http://www.pycage.de/#gdeskcal](http://www.pycage.de/#gdeskcal)
this is in the repos - sudo apt-get install gdeskcal
---------------------------------------------------------------------------------------------------------------------------
clipboard manager glipper - in repos
[http://glipper.sourceforge.net/about.shtml](http://glipper.sourceforge.net/about.shtml)
---------------------------------------------------------------------------------------------------------------------------
Debian.exe - Aside from having the best domain on the internet ([http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)), it's a fantastic tool which works seamlessly. Differs from Ubuntu's equivalent because it doesn't install Debian in the Windows partition, it's basically the netinstall CD without the need for a CD. Very, very useful for getting Debian on machines with no CD/USB/Floppy.
---------------------------------------------------------------------------------------------------------------------------
FSlint is a utility to find and clean various forms of lint on a filesystem.
One form of lint it finds for example is duplicate files.
It has both GUI and command line modes.
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)
---------------------------------------------------------------------------------------------------------------------------
dvdisaster. It's in the repo's. It will salvage all readable data off a scratched or corrupted dvd/cd and make an iso file so you can put the salvaged data on a good dvd. Also if you use it on a dvd/cd that isn't scratched, it will make a small reference file for that dvd so that if it gets scratched in the future, it can read the readable material, and fix the rest with the reference. Pretty handy.
---------------------------------------------------------------------------------------------------------------------------
xbox iso extractor
[http://gxiso.berlios.de/](http://gxiso.berlios.de/)
---------------------------------------------------------------------------------------------------------------------------
Vector drawing program
[http://www.skencil.org/index.html](http://www.skencil.org/index.html)
---------------------------------------------------------------------------------------------------------------------------
ghost backup type clone
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
---------------------------------------------------------------------------------------------------------------------------
Virtual disc encrypter
[http://www.truecrypt.org/](http://www.truecrypt.org/)
---------------------------------------------------------------------------------------------------------------------------
Nautilis Actions - add extra stuff to your right click menu plus other cool stuff
[http://www.grumz.net/index.php?q=node/289](http://www.grumz.net/index.php?q=node/289)
---------------------------------------------------------------------------------------------------------------------------
CD RIpper - grip
[http://nostatic.org/grip/](http://nostatic.org/grip/)
---------------------------------------------------------------------------------------------------------------------------
video convertor
[http://biggmatt.com/programs/video-converter/winff---free-video-converter.html](http://biggmatt.com/programs/video-converter/winff---free-video-converter.html)
[http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder](http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder)
---------------------------------------------------------------------------------------------------------------------------
QBrew found it in synaptic.

It's a homebrewing recipe guide. Includes the Beer Judge Certification Program (BJCP) style guide so I can build my recipes to fit in the guidelines.
---------------------------------------------------------------------------------------------------------------------------
Lyx document processor
[http://www.lyx.org/](http://www.lyx.org/)
---------------------------------------------------------------------------------------------------------------------------
convert xp cursors to linux
[http://gursormaker.sourceforge.net/](http://gursormaker.sourceforge.net/)
---------------------------------------------------------------------------------------------------------------------------
flight simulator
[http://www.flightgear.org/](http://www.flightgear.org/)
---------------------------------------------------------------------------------------------------------------------------
electric sheep very cool screensaver
[http://www.electricsheep.org/](http://www.electricsheep.org/)
---------------------------------------------------------------------------------------------------------------------------
all sorts of extra googies for ubuntu
[http://www.littleubuntu.com/v2/](http://www.littleubuntu.com/v2/)
---------------------------------------------------------------------------------------------------------------------------
Firefox User agnet switcher. if you have a site that only works with Internet explorer, try this add on it may fix the error
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
if this does not fix the error and you have a web wite that demands you have IE and the above app fails, install IE with this
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
---------------------------------------------------------------------------------------------------------------------------
Program won't stay in Startup Programs menu - permissions fault
[http://ubuntuforums.org/showthread.php?t=359686&highlight=startup+chown+permissions](http://ubuntuforums.org/showthread.php?t=359686&highlight=startup+chown+permissions)
---------------------------------------------------------------------------------------------------------------------------
how to flash bios of a mobo the ubuntu way
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)
---------------------------------------------------------------------------------------------------------------------------
all sorts of tips, tricks, hacks, info, etc
[http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html](http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html)
---------------------------------------------------------------------------------------------------------------------------
Q. How do I backup Thunderbird mail and profile within Ubuntu

A. Thunderbird is simple to use and powerful email client with following features:
=> Safe, fast, and easy email

=> Intelligent spam filters

=> Quick message search

=> Customizable views etc

Mozilla thunderbird stores your email and profile setting in a special directory called ~/.mozilla-thunderbird i.e. /home/you/.mozilla-thunderbird/

All you have to do is backup this directory.
Task: Backup Thunderbird mail and profile

You need to backup thunderbird mail and profile to tape drive, use:
# tar zcvf /dev/st0 /home/you/.mozilla-thunderbird/

You need to backup thunderbird mail and profile to a /backup directory:
# tar zcvf /backup/email-you-22jan2007.tar.gz /home/you/.mozilla-thunderbird/

You can copy /backup/email-you-22jan2007.tar.gz file to a CD/DVD or USB pen.
Task: Restore Thunderbird mail and profile

Make sure Thunderbird is not running. Simply copy backup files from tape, USB pen or CD to your /home/you/.mozilla-thunderbird/ directory:
$ tar &#8211;zxvf /backup/email-you-22jan2007.tar.gz -C /home/you

Or just copy all files from USB pen/CD to ~/.mozilla-thunderbird/ directory.

Where it says "you" make this say your user name
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Handy Thunderbird tips
Look ma, no messages!

Let's take a look at another common problem: You open up your email one day, and all your messages are missing. Isn't that a great way to start your day!

Thunderbird gets just a wee bit confused sometimes about keeping track of its messages. The root of this problem is that it doesn't do well with handling large numbers of mail messages. The program has gotten better, but it still happens often enough that it really ticks me off.

The first thing you should do is close Thunderbird and head to your Profile mail directory and sub-directories. Once there, delete all your ".msf" files. Then, restart Thunderbird. With luck, you'll be back in business.

Be unique

One way to avoid problems is to avoid using Thunderbird's default mail account. The program has an annoying habit of losing track of its "default" mail profile. Don't ask me why -- it's beyond me.

Usually, the first time you run into this is when you start up Thunderbird and -- what's this? -- you see the new account window instead of the application. You can usually get things back to normal, by closing out of the new account dialog and using Profile Manager to make Thunderbird start with the default profile.

Better still, when you first create your Thunderbird account, create your profile with a unique name. I, for example, use sjvn. Thunderbird will not lose track of this unique name. Or, at least, it hasn't yet on any of the machines I've set up with unique user names!

While, you're at it, if you're running Windows, why not do yourself a favor and create a top-level directory under My Documents for your Thunderbird profile with Windows Explorer, Norton Commander, or your file manager of choice. That way, it will be a lot easier to find when something goes wrong.

Then, you can use that folder for your profile when you run the Create Profile Wizard. It will make your life a lot easier.

Compact those folders!

Another must technique for avoiding Thunderbird annoyances is to run the command: File > Compact Folders. You see, when Thunderbird deletes email messages, it doesn't really delete anything. It's just hiding them from you. It's only when you run Compact Folders that the messages actually get wiped.

If you don't run Compact Folders, you accumulate this deleted crud, and Thunderbird will eventually stall out in one annoying way or another -- leaving you wondering what the heck happened.

Every time I look in on the Thunderbird support forums, the number of ways that uncompacted folders can make your life miserable keeps going up. If you don't do anything else with Thunderbird, run Compact Folders at least weekly on your inbox and any other folders you might have where you're frequently deleting or moving files.

Trust me, it's worth the trouble.


---------------------------------------------------------------------------------------------------------------------------
To backup firefox bookmars, get this extension
[http://www.pikey.me.uk/mozilla/#bb](http://www.pikey.me.uk/mozilla/#bb)
---------------------------------------------------------------------------------------------------------------------------
How to install anything in Ubunto for users coming across from Windows
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
---------------------------------------------------------------------------------------------------------------------------
Ubuntu Gamers Arena
[http://gaming.gwos.org](http://gaming.gwos.org)
---------------------------------------------------------------------------------------------------------------------------
Ubuntu Video - Ubuntu Video is a video portal that takes the best Ubuntu-related videos on the Internet, from places like YouTube and Google Video, and centralizes them in one convenient spot. There are many goals - demystifying Linux, providing support to Ubuntu users, crushing Linux myths, even educating people about free and open source software.
[http://ubuntuvideo.com](http://ubuntuvideo.com)
---------------------------------------------------------------------------------------------------------------------------
Register yourself at Ubuntu Counter It aims to catalogue the number of registered machines using the numerous varients of the Ubuntu Linux distribution.
[http://ubuntucounter.geekosophical.net/index.php](http://ubuntucounter.geekosophical.net/index.php)
---------------------------------------------------------------------------------------------------------------------------
Planet Ubuntu Planet Ubuntu is a window into the world, work and lives of Ubuntu developers and contributors.
 [http://planet.ubuntu.com/](http://planet.ubuntu.com/)
---------------------------------------------------------------------------------------------------------------------------
The Ubuntu Fridge The Fridge is an information hub for the Ubuntu community, bringing together news, grassroots marketing, advocacy, team collaboration, and great original content.Just like the family fridge at home, this is where we - the Ubuntu family - can put our best work on display for everyone to see&#8230; along with the requisite jokes, reminders, invitations, news clippings, photos and everything else!
[http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)
---------------------------------------------------------------------------------------------------------------------------
If your monitor is giving you a hard time and not showing the right resolutions this little trick may fix it
sudo nano /etc/X11/xorg.conf
scroll down using the arrow keys till you find this section
Section "Monitor"
at the bottom of this section add these two lines

HorizSync 30-110
VertRefresh 50-70

now quit and save and restart. with a bit of luck, should be all good!
---------------------------------------------------------------------------------------------------------------------------
Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
---------------------------------------------------------------------------------------------------------------------------
Ubuntu user technical support, not for general discussions
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
---------------------------------------------------------------------------------------------------------------------------
HOWTO: all K3B burning: mp3, data, iso, .bin/.cue, avi to dvd, etc.
[http://ubuntuforums.org/showthread.php?p=3093830#post3093830](http://ubuntuforums.org/showthread.php?p=3093830#post3093830)
---------------------------------------------------------------------------------------------------------------------------
Mount and Unmount ISO Images into Ubuntu
[http://ubuntuforums.org/showthread.php?t=463972&highlight=bin+cue](http://ubuntuforums.org/showthread.php?t=463972&highlight=bin+cue)
---------------------------------------------------------------------------------------------------------------------------
Autopackage makes software installation on Linux easy. Software distributed using Autopackage can be installed on multiple Linux distributions and integrate well into the desktop environment.
[www.autopackage.org]("http://www.autopackage.org")
---------------------------------------------------------------------------------------------------------------------------
USB view - see what your usb devices are doing from cli type this
sudo apt-get install usbview
---------------------------------------------------------------------------------------------------------------------------
TUX a magazine for new Linux users
[http://www.tuxmagazine.org/](http://www.tuxmagazine.org/)
---------------------------------------------------------------------------------------------------------------------------
assorted how to clips for Ubuntu
[http://ubuntuclips.org/](http://ubuntuclips.org/)
---------------------------------------------------------------------------------------------------------------------------
Winki the ripper DVD ripper.follow this link to d/l
[http://www.winki-the-ripper.de/openengine/cms/website.php?id=/de/index/download.htm&sid=22734f0d16d1d27b898f601f933efd31#feisty](http://www.winki-the-ripper.de/openengine/cms/website.php?id=/de/index/download.htm&sid=22734f0d16d1d27b898f601f933efd31#feisty)
---------------------------------------------------------------------------------------------------------------------------
Peekko chat - Makes every web page a place where people can congregate. It adds a toolbar to Firefox that shows how many people are in that page's chat room and allows you to instantly connect with them. Addon for firefox
[https://addons.mozilla.org/en-US/firefox/addon/1825](https://addons.mozilla.org/en-US/firefox/addon/1825)
---------------------------------------------------------------------------------------------------------------------------
Top games to play
[http://ubuntuforums.org/showthread.php?t=427205&highlight=pinball](http://ubuntuforums.org/showthread.php?t=427205&highlight=pinball)
---------------------------------------------------------------------------------------------------------------------------
The Dohickey project - he Dohickey client is a python based GUI software tool which allows the user to list the hardware within his or her machine. Each piece of hardware is given its own id, and this id is then looked up online to see if there is any existing information about this hardware in the database. The GUI then allows the user to report to the server how well the hardware works, edit the information attached to that hardware and send in comments and instructions for the installation of the hardware, which will then be added to the online database. From that point on, anyone who browses the database online will be able to see that information. So, you get to find out about your hardware and help other people, all in one stroke.
[http://www.dohickey-project.com](http://www.dohickey-project.com)
---------------------------------------------------------------------------------------------------------------------------
Warsow - Warsow is a free standalone first person shooter game for Windows and Linux. It is based on the Qfusion 3D engine (a modification of the Quake 2 GPL engine), and aimed on the competitive scene, or the e-sports community.
[http://www.warsow.net](http://www.warsow.net)
---------------------------------------------------------------------------------------------------------------------------
[https://help.ubuntu.com/community/DVD::Rip](https://help.ubuntu.com/community/DVD::Rip)
how to rip encrypted dvds
---------------------------------------------------------------------------------------------------------------------------
print a pdf file from any program

PDF creation with Ubuntu is actually very easy.  Since .pdf files are open source Ubuntu has several ways to create and view .pdf files.  As you may or may not know Openoffice.org has a way to create .pdf files via the use of the Export PDF function.  Well what if you want to create a .pdf file from a web page, text editor or some other application that does not support PDF creation.  No fear there is a package in Ubuntu called CUPS PDF.  To install CUPS PDF simply type the following line in a terminal:

sudo apt-get install cups-pdf

This will the CUPS PDF printer driver.  Now we just need to install the printer driver.  To do that follow these steps.

    * Open printer installation under System--->Administration--->Printing
    * In the Printers window right mouse click on New Printer and select Add
    * This will bring up the Add a Printer window
    * In this window there should be a PDF Printer available.  Highlight the PDF Printer and click Forward
    * Drop down the Manufacturer menu and select Generic
    * Select the postscript color printer and hit Forward
    * Type in a Description and Location and click Apply

That is it.  When you go to print something you will select the postscript color printer and then print.  The .pdf file will be saved in your /home/<your_home>/PDF folder.
---------------------------------------------------------------------------------------------------------------------------
You can edit PDF files like a "normal document" using Kword
---------------------------------------------------------------------------------------------------------------------------
Linuxtopia free online books and info on Ubuntu and other Linux distros
[http://www.linuxtopia.org/online_books/index.html](http://www.linuxtopia.org/online_books/index.html)
---------------------------------------------------------------------------------------------------------------------------
 Unofficial Ubuntu 7.04 (Feisty Fawn) Starter Guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#dvdrip](http://ubuntuguide.org/wiki/Ubuntu:Feisty#dvdrip)
---------------------------------------------------------------------------------------------------------------------------
make sure dma and 32bit access is turned on
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)
enable dma  sudo hdparm -d1 /dev/hdc
enable 32bit sudo hdparm -c1 /dev/hdc
---------------------------------------------------------------------------------------------------------------------------
Linux bit torrent tracker
[http://linuxtracker.org/](http://linuxtracker.org/)
---------------------------------------------------------------------------------------------------------------------------
The Alternative to CTRL+ALT+DEL

If you have a program that crashes and you need to exit from it, bring up a desktop like this
CTRL+ALT+F1 
this brings up a command prompt.
log in with your usual username/password
if you know the name of the program you can kill it with the command 
killall "filename"
and where filename is, the name of the program
otherwise you can use tools like "top" (q to exit) or "ps aux" 

with "ps aux" your better off using "ps aux | more" that way you geta chance to read the info before it flys off the screen.

once you have killed the offending app you can return to GUI by pressing CTRL+F7 on keyboard
---------------------------------------------------------------------------------------------------------------------------
Ubuntu Essentials web site - a start point for newbies
[http://www.ubuntuessentials.net/](http://www.ubuntuessentials.net/)
---------------------------------------------------------------------------------------------------------------------------
An Aussie Ubuntu users handy post install tips/tricks for ubuntu
[http://users.bigpond.net.au/hermanzone/p5.htm](http://users.bigpond.net.au/hermanzone/p5.htm)
---------------------------------------------------------------------------------------------------------------------------
for thse swapping from windows to ubuntu
[http://allaboutubuntu.wordpress.com/](http://allaboutubuntu.wordpress.com/)
---------------------------------------------------------------------------------------------------------------------------
Tutorial on how to get XP Pro running in Linux under VMware
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
---------------------------------------------------------------------------------------------------------------------------
how to get that internal hard drive mounted on every boot
for a long time now i have been trying to get my 80 gig NTFS /hdc drive mounted on boot up. i have read thread after thread on how to do CLI (command line interface) commands to make it work.

Nothing has worked.


Till this morning.

Out of sheer frustration and last ditch hope i went to "applications" and scrolled to "add remove"

click on "show all available apps"

now search and find a program called "storage device manager"
now install it.
after it is installed, to find it go to "system -> administration"
find storage device manager and open it.
now pick the hdd you want to be auto mounted on the left side.
on the right side the hdd will probably be unmounted like mine was. click on the button that says "mount" then click on default.

Thats it!

Restart your pc and everytime you restart it is going to be there, no mucking round, no jumping thru hoops, no cli , IT JUST WORKS!

Hope this helps a few others who are in the same boat as me.
---------------------------------------------------------------------------------------------------------------------------
If your looking for an application starter or mac os-x dock style program starter there is one in Gdesklets it is called "Starter Bar".
Fire up the Gdesklets app and go to "toolbars/launchers" and it is in there
---------------------------------------------------------------------------------------------------------------------------
some tips to setup a fresh hard drive
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

after you have partitioned the hard drive make sure you run this command 
 sudo chown -R USERNAME:USERNAME /media/mynewdrive

you must run the chown command or you will not be able to create files/directorys on the drive

---------------------------------------------------------------------------------------------------------------------------
Linux application finder helps you find Linux native apps from Windows to Linux users
[http://linuxappfinder.com/all](http://linuxappfinder.com/all)
---------------------------------------------------------------------------------------------------------------------------
    Turn a CD/DVD into an .iso
    sudo umount /dev/cdrom
    dd if=/dev/cdrom of=file.iso bs=1024

    Turn a folder into an .iso
    mkisofs -r -o file.iso /location_of_folder/
 
   Generate an MD5 checksum file
    md5sum file.iso > file.iso.md5
---------------------------------------------------------------------------------------------------------------------------
Conky on steroids - system monitor that attaches to desktop
[http://www.kde-look.org/content/show.php/Aero-Gr?content=63213](http://www.kde-look.org/content/show.php/Aero-Gr?content=63213)
---------------------------------------------------------------------------------------------------------------------------
Only Ubuntu - some great infomation about Ubuntu and things to add to make it  achieve more
[http://swik.net/Ubuntu/Only+Ubuntu?page=1](http://swik.net/Ubuntu/Only+Ubuntu?page=1)
---------------------------------------------------------------------------------------------------------------------------
High Quality and High resolution desktop wall papers for any O/S

[http://www.qapla.org/wallpaper/?site=index](http://www.qapla.org/wallpaper/?site=index)
[http://interfacelift.com/](http://interfacelift.com/)
---------------------------------------------------------------------------------------------------------------------------
having dramas with slow internet connection, this may help

 Re: Gusty effects + internet
managed to solve the internet problem
by using an old solution

1: sudo gedit /etc/modprobe.d/aliases
2: find the line - alias net-pf-10 ipv6
3: Edit this to alias net-pf-10 off
4:save and reboot
5: IF that does nothing try line 3) with .... off ipv6
6:It should now surf alot faster

it's the dns settings. this happend to me. you have to go to network settings put your dns settings in manually ane then enter "sudo chattr +i /etc/resolv.conf" This will lock the file and keep it from being reset. to unlock it in the future just use the same command but use a - instead of a +
---------------------------------------------------------------------------------------------------------------------------
setup irfan view in Ubuntu so it works like a normal linux app
[http://ubuntuforums.org/showthread.php?p=3700351#post3700351](http://ubuntuforums.org/showthread.php?p=3700351#post3700351)
---------------------------------------------------------------------------------------------------------------------------
need to get beryl running everytime the pc starts up or restarts here is how i did it

system->preferences->session

go to startup programs and click the add button

in there put this

"beryl-manager"
 in the name,command,comment section

then go to the last tab that says "session options"

click on save session

restart. done
---------------------------------------------------------------------------------------------------------------------------
If you have a fat32 partition and you can read only to it, you need to edit the fstab file.this can be done by starting up a terminal session and typing this

gksudo gedit /etc/fstab


you should see somewhere a line similar to this

/dev/hdd1                                  /media/hdd1    vfat  defaults                     0  0 

you need to delete everything after vfat, so delete the word "defaults" and the two number zero as well.

after the vfat word, add this

rw,user,umask=000 0 0

save the file and exit and restart pc.
all going to plan, you should now have read/write access to all data
---------------------------------------------------------------------------------------------------------------------------
to setup CPU temp monitor start up terminal and type this

sudo aptitude install sensors-applet

once it's installed, right-click on an empty space in your top panel (or bottom panel if you prefer), select Add To Panel, and look for Hardware Sensors Monitor
once running, right click on it and configure.

or you can do this

Now, when I want to use a sensor program, I usually use ksensors.
So, if you want to install it, run this command in the terminal:
Code:

sudo apt-get install ksensors

To run the program, once it is installed, type this:
Code:

ksensors

Now you can configure it, and set it up to watch your cpu temperature. 
---------------------------------------------------------------------------------------------------------------------------
DNS ip redirector
Cable / DSL or even dialup users can enjoy this free service to replace their
dynamic IP address with a static hostname.
[http://dyns.net/](http://dyns.net/)
---------------------------------------------------------------------------------------------------------------------------
If you really need interent explorer load in linux, go to this site
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
---------------------------------------------------------------------------------------------------------------------------
convert binary to text or text to binary
[http://nickciske.com/tools/binary.php](http://nickciske.com/tools/binary.php)

convert hex to text or text to hex
[http://nickciske.com/tools/hex.php](http://nickciske.com/tools/hex.php)

convert octal to text or text to octal
[http://nickciske.com/tools/octal.php](http://nickciske.com/tools/octal.php)


or if you have firefox you can install LEET KEY
[https://addons.mozilla.org/en-US/firefox/addon/770](https://addons.mozilla.org/en-US/firefox/addon/770)
---------------------------------------------------------------------------------------------------------------------------
if you install ubuntu server edition, there is no GUI, but you can add one

sudo aptitude install ubuntu-desktop

If you don't need a LAMP server you can use xubuntu and vnc as a file server on an old comp
---------------------------------------------------------------------------------------------------------------------------
how to:fix ubuntu via net
1) Set secure passwords on the Linux box in question. You're going to open these up to the internet, so don't have accounts like "bob" with passwords like "bobspass". I would even put a new, non-standard and temporary password on the primary account (because I'll need that to make the changes). When I'm done I'll let you know, and you can reset the password again.

2) "sudo apt-get install openssh-server" on the machine in question

3) On your router/gateway device, forward TCP port 22 to the internal IP of your Linux box

4) Record your public internet address (you can find it at [http://www.whatismyip.com](http://www.whatismyip.com) ).

When all that's done, fire me a PM with the IP, username and password and I'll sort it out.
(extra reading here [http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)
---------------------------------------------------------------------------------------------------------------------------
 Re: Remote control/desktop type prog for Ubuntu
Quote:
Originally Posted by Thrasonic View Post
Wow, that Xming stuff is confusing to me. I think it's a bit beyond my capabilities right now. Thanks for the idea, but unless someone is going to walk me through getting this working I'll have to take a pass right now.
Step 1: Forward UDP port 177 on the router
Step 2: Configure Remote access options

    System -> Administration -> Remote

    Change any options that you want. Default settings will work fine.

Step 3: Enable XDMCP

    Code:

    gksudo gedit /etc/gdm/gdm.conf

    Scroll down to the section
    Code:

    [xdmcp]

    Change
    Code:

    Enable=false

    to
    Code:

    Enable=true

    (line no 263 on my system)

Step 4: Download and install Xming-6-9-0-23-setup.exe from [http://sourceforge.net/project/showf...roup_id=156984](http://sourceforge.net/project/showf...roup_id=156984)
Step 5: Setup XMing on Windows box

    After installation, start XLaunch (Start -> Programs -> XMing -> XLaunch)

    Screen 1: select One Window or Fullscreen as desired (preferably One Window)

    Screen 2: select "Open session via XDMCP"

    Screen 3: enter the IP address of the linux box with XDMCP enabled

    Screen 4: accept the default settings (Clipboard)

    Screen 5: click Save Configuration and save the file on desktop

    When you click finish, if XMing can communicate with the XDMCP enabled linux box, you should be presented with a login screen.

For subsequent use, you can launch the configuration file you saved from screen 5.
I would suggest you check the XDMCP stuff from a local LAN machine first and then check the forwarding from a machine on the internet.
---------------------------------------------------------------------------------------------------------------------------
to add a software eject for cd/dvd drive to system try this

Open Terminal and type/ cut&paste

Code:
sudo sysctl dev.cdrom.lock=0

now your cd can be ejected by simply clicking on the eject button but if you restart it will no longer be available, to make it permanent,
then type

Code:
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
Now it will be permanent.
---------------------------------------------------------------------------------------------------------------------------
To install KDE on to Ubuntu you have a few choices if your using gnome.
Those options are

kubuntu-desktop -This is the recommended metapackage to install; the full Kubuntu installation, with all the Kubuntu recommended packages. This includes OpenOffice, Kontact, Konversation, amaroK, K3B, and others.

kde -This will install the following KDE packages: kde-amusements, kdeaccessibility, kdeaddons, kdeadmin, kdeartwork, kdegraphics, kdemultimedia, kdenetwork, kdepim, kdesdk, kdeutils, kdewebdev, kdevelop3 and the kde-core metapackage

kde-core -This will install the core &#8212; the bare-minimum required&#8211; of KDE. That is, kdebase, kdelibs, arts and fontconfig.

If you choose to not install kubuntu-desktop, then you can still get all the Kubuntu-specific tweaks by installing the kubuntu-default-settings package.

If you want to install kubuntu-desktop use the following command

sudo apt-get install kubuntu-desktop

If you want to switch back to Gnome, just log out and select Gnome from the session menu.

If you want to install only KDE use the following command

sudo apt-get install kde

If you want to install only kde-core use the following command

sudo apt-get install kde-core
---------------------------------------------------------------------------------------------------------------------------
to install edubuntu on ubuntu etc, fireup shell and copy/paste

sudo apt-get install edubuntu-desktop
---------------------------------------------------------------------------------------------------------------------------
ubuntu guide for everything
[http://ubuntuguide.org](http://ubuntuguide.org)
---------------------------------------------------------------------------------------------------------------------------
if you need to do work with .iso, .daa, .bin , then grab a free copy of poweriso for linux here
[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)

once installed fire up your terminal and go to the directory where you extracted the file and type this
./poweriso -?

it will how you how to drive it. there is a quick tutorial at the ubuntu site
[http://ubuntuforums.org/showthread.php?t=474468](http://ubuntuforums.org/showthread.php?t=474468)
---------------------------------------------------------------------------------------------------------------------------
Remote contoll pc via web browser multiplatform
[http://www.sshtools.com/showSslExplorerCommunity.do](http://www.sshtools.com/showSslExplorerCommunity.do)

get the gui version for linix
[http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980](http://sourceforge.net/project/showfiles.php?group_id=116065&package_id=125980)
---------------------------------------------------------------------------------------------------------------------------
**Ext2 File System Driver for Windows**

                 Ext2Fsd is an open source linux ext2/ext3 file system driver for Windows systems (NT/2K/XP/VISTA, X86/AMD64).
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
---------------------------------------------------------------------------------------------------------------------------
AcetoneISO is the [disk image emulator]("http://en.wikipedia.org/wiki/Disk_image_emulator") that mounts images of DVD and CD media. Both Mac OS X and [Linux]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html") / other [UNIX like]("http://www.cyberciti.biz/faq/howto-mount-sun-solaris-cd-iso-image/") oses can mount and use ISO images using loopback device. It is a [DAEMON Tools]("http://www.daemon-tools.cc/") (Microsoft Windows disk image) clone / emulator program with a lot more features.
 Using this cool open source software means a user does not have to swap discs to run different programs on local or network computer. You can access software distributed (over Internet) as a disk image such as ISO, DAA, BIN or many other formats (no need to burn a CD/DVD to use disk image). Other usage:[LIST]
[*]Prevent scratching, which can cause permanent damage to a disc
[*]Speeds up access times as hard drives are faster than optical drives
[*]Provides a backup copy of a disc, in case the original becomes damaged, lost, or stolen[/LIST]**Features:**[LIST]
[*]Mount and Unmount  ISO, MDF, NRG (if iso-9660 standard)
[*]Convert BIN/CUE, MDF, NRG, CCD/IMG, CDI, XBOX, B5I/BWI, PDI, DAA to ISO
[*]Burn Your ISO, CUE, TOC images directly in K3b
[*]Blank Your CD/DVD ReWritable
[*]Verify md5sum of image files and Generate a Md5sum file from ISO
[*]Ability to create ISO from Folder and CD/DVD
[*]Service-Menu support
[*]Play a DVD-Movie ISO with Kaffeine, Mplayer, VLC, Kmplayer
[*]Split ISOs in smaller files and Merge them
[*]Quick Turbo Mount an ISO file from your Desktop
[*]Compress ISO with p7zip and extract
[*]Encrypt and Decrypt an ISO
[*]Generate a CUE file from a IMG/BIN image
[*]Rip a PSX cd to a bin/toc image[/LIST]AcetoneISO has only one dependencies problem - Kommander. Make sure you have Kommander  installed.
 **Step # 1: Install kommander**

 Use [apt-get command]("http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html") to install [kommander]("http://kde-apps.org/content/show.php?content=12865") ( it consists of an editor and a program executor that produce dialogs that you can execute), which is required by AcetoneISO. You also need p7zip (a file archiver with highest compression ratio) to compress and extract ISO images. Use apt-get command under Debian or Ubuntu Linux as follows:
# apt-get install kommander p7zip
OR
$ sudo apt-get install kommander p7zip
 **Step # 2: Install AcetoneISO**
First you need to download latest AcetoneISO .deb package from here [http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)
ubunu 32 bit bersion here
[http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.1_x86.deb?modtime=1202501447&big_mirror=0](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.1_x86.deb?modtime=1202501447&big_mirror=0)

or fireup terminal and copy/paste this

wget [http://mesh.dl.sourceforge.net/sourceforge/acetoneiso2/acetoneiso2_2.0.1_x86.deb](http://mesh.dl.sourceforge.net/sourceforge/acetoneiso2/acetoneiso2_2.0.1_x86.deb)

Now you should be having acetoneiso2_2.0.1_x86.deb file you need to install this file using the follwoing command
 sudo dpkg -i acetoneiso2_2.0.1_x86.deb
 This will complete the installation
 Now you need to go to  Application > Accessories > AcetoneISO

 or Simply type the command 
$  acetoneiso &
---------------------------------------------------------------------------------------------------------------------------
if your looking for a peer guardian type program for ubuntu, check this out
[http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html](http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html)  
---------------------------------------------------------------------------------------------------------------------------
Size me verison 2 does work in Ubuntu.... with a twist.

grab the software here
[http://lars.werner.no/?page_id=2](http://lars.werner.no/?page_id=2)
install it in wine.

create a spare directory on a hdd somewhere that has enough spare space to save enough data to fill a dvd, say 4.4 gig.
call the directory for example 

sizeme-output

now, fireup sizeme and point it to the directory you need sized up.

when it makes the cd listing in green, click on disc one and then right click on it and select "copy to"
point it to the directory you just created.
it will copy these files to that directory.
now fireup K3b or whatever and tell it to make a new dvd complilation and copy/paste the files from the sizeme-output directory to the K3B layout and burn away.
do this for each disc.
a little time consuming, but it works!!!
---------------------------------------------------------------------------------------------------------------------------

---

### Post by pyros on 2007-07-19
> **stinger30au said:**
> where is the ubuntu wiki??


[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by evets on 2007-12-22
[QUOTE=stinger30au;3048141]where is the ubuntu wiki??

If your like me and moving from Windows XP to Ubuntu this info below is very handy to have


here is a start of extra repos i have been gathering.now i have started to put this together im finding how amazingly easy it is to work with ubuntu
{snip}


Holy electrons, batman! That's a heck of a post! Thank you. It must've taken quite a while to gather all of those resources.

Thanks again.

---

### Post by stinger30au on 2007-12-24
> **evets said:**
> [QUOTE=stinger30au;3048141]where is the ubuntu wiki??

If your like me and moving from Windows XP to Ubuntu this info below is very handy to have


here is a start of extra repos i have been gathering.now i have started to put this together im finding how amazingly easy it is to work with ubuntu
{snip}


Holy electrons, batman! That's a heck of a post! Thank you. It must've taken quite a while to gather all of those resources.

Thanks again.


yeah, its taking some time. i have learnt a lot. if someone could add thse to he wiki that would be awesome

---

### Post by stinger30au on 2007-12-30
games, games, games....
im enjoying a few rounds on Assault cube.
install was easy, get it here

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)


i am using Ultimate edition available here
[http://ubuntusoftware.info/](http://ubuntusoftware.info/)

once installed you can also install its big brother version, cube 2, also known as Sauerbraten. its in the repos.

next game i want to try is Wolfenstein Enemy Territory. i have found these few pages on how to install

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)
[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

---

### Post by Darganot on 2007-12-31
GetDeb is a great source for extra packages ("programs").

Enemy Territory is free but I personally play Quake Wars.  I've bought the full copy and I suggest you do to.  id is nice enough to make a linux client.  Let me dig up some helpful links since you're clearly starting off:

[http://zerowing.idsoftware.com:6969/](http://zerowing.idsoftware.com:6969/)
download clients and demos for W:ET, ET:QW, Doom 3, Quake 4, and more.

[http://ubuntuforums.org/showthread.php?t=547759](http://ubuntuforums.org/showthread.php?t=547759)
Thread with help on installing the Quake Wars demo

[http://ubuntuforums.org/showthread.php?t=489874](http://ubuntuforums.org/showthread.php?t=489874)
Thread with links to a few game install guides.  

[http://www.urbanterror.net/page.php?6](http://www.urbanterror.net/page.php?6)
Also check out Urban Terror 4.1, a free stand alone Quake 3 mod (trust me it's quality)

[http://www.linux-gamers.net/](http://www.linux-gamers.net/)
Another good site for games that aren't in the repos



Hope this helps.  Good luck!  :popcorn:

---

### Post by stinger30au on 2007-12-31
sweet thanks!!!

---

### Post by stinger30au on 2008-01-01
cool. i got enemy territory installed i used this info

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

make sure you allow access to the directory the maps are installed to our it will never d/l a map from the net and you will never join a game.
allow access with this

sudo chmod 777 -R *.*
run this command on this directory

~/.etwolf/


i have also found ubuntu gamers arena with lots of games as well

[http://gaming.gwos.org/doku.php/start](http://gaming.gwos.org/doku.php/start)

---

### Post by stinger30au on 2008-01-02
how to change the desktop background to a random image at a preset interval

[http://ubuntuforums.org/showthread.php?t=329164](http://ubuntuforums.org/showthread.php?t=329164)

---

### Post by vincentvee on 2008-01-14
[http://www.getdeb.net](http://www.getdeb.net)

> **stinger30au said:**
> I wanna download something ot other....

---

### Post by stinger30au on 2008-04-25
[http://ubuntuforums.org/showpost.php?p=4050910&postcount=1](http://ubuntuforums.org/showpost.php?p=4050910&postcount=1)

---

### Post by stinger30au on 2008-04-30
Open office spell check not working, here is the two second fix

**open office Spell Check is not working**                                                                   To fix the problem, you need to go to[B] File > Wizards > Install New Dictionaries 

[/B]when you see the languages and if you double click on them and they dont open up, right click on them and open hyperlink, all set!
----------------------------------------------------------------------------------------------------------------------
if you want a way to print a banner from shell type this
banner -w50 test
it will print test down your screen you can then print it to your printer if you wish
----------------------------------------------------------------------------------------------------------------------
 An A-Z Index of the [COLOR=#339900]Linux BASH[/COLOR] command line  http://www.ss64.com/bash/
[alias]("http://www.ss64.com/bash/alias.html")    Create an alias
apropos  Search Help manual pages (man -k)
[awk]("http://www.ss64.com/bash/gawk.html")      Find and Replace text, database sort/validate/index
[break]("http://www.ss64.com/bash/break.html")    Exit from a loop
[builtin]("http://www.ss64.com/bash/builtin.html")  Run a shell builtin
bzip2    Compress or decompress named file(s)

[cal]("http://www.ss64.com/bash/cal.html")      Display a calendar
[case]("http://www.ss64.com/bash/case.html")     Conditionally perform a command
[cat]("http://www.ss64.com/bash/cat.html")      Display the contents of a file
[cd]("http://www.ss64.com/bash/cd.html")       Change Directory
[cfdisk]("http://www.ss64.com/bash/cfdisk.html")   Partition table manipulator for Linux
[chgrp]("http://www.ss64.com/bash/chgrp.html")    Change group ownership
[chmod]("http://www.ss64.com/bash/chmod.html")    Change access permissions
[chown]("http://www.ss64.com/bash/chown.html")    Change file owner and group
[chroot]("http://www.ss64.com/bash/chroot.html")   Run a command with a different root directory
[cksum]("http://www.ss64.com/bash/cksum.html")    Print CRC checksum and byte counts
clear    Clear terminal screen
[cmp]("http://www.ss64.com/bash/cmp.html")      Compare two files
[comm]("http://www.ss64.com/bash/comm.html")     Compare two sorted files line by line
[command]("http://www.ss64.com/bash/command.html")  Run a command - ignoring shell functions
[continue]("http://www.ss64.com/bash/continue.html") Resume the next iteration of a loop
[cp]("http://www.ss64.com/bash/cp.html")       Copy one or more files to another location
[cron]("http://www.ss64.com/bash/cron.html")     Daemon to execute scheduled commands
[crontab]("http://www.ss64.com/bash/crontab.html")  Schedule a command to run at a later time
[csplit]("http://www.ss64.com/bash/csplit.html")   Split a file into context-determined pieces
[cut]("http://www.ss64.com/bash/cut.html")      Divide a file into several parts

[date]("http://www.ss64.com/bash/date.html")     Display or change the date & time
[dc]("http://www.ss64.com/bash/dc.html")       Desk Calculator
[dd]("http://www.ss64.com/bash/dd.html")       Data Dump - Convert and copy a file
[ddrescue]("http://www.ss64.com/bash/ddrescue.html") Data recovery tool
[declare]("http://www.ss64.com/bash/declare.html")  Declare variables and give them attributes
[df]("http://www.ss64.com/bash/df.html")       Display free disk space
[diff]("http://www.ss64.com/bash/diff.html")     Display the differences between two files
[diff3]("http://www.ss64.com/bash/diff3.html")    Show differences among three files
[dig]("http://www.ss64.com/bash/dig.html")      DNS lookup
[dir]("http://www.ss64.com/bash/dir.html")      Briefly list directory contents
[dircolors]("http://www.ss64.com/bash/dircolours.html") Colour setup for `ls'
[dirname]("http://www.ss64.com/bash/dirname.html")  Convert a full pathname to just a path
[dirs]("http://www.ss64.com/bash/dirs.html")     Display list of remembered directories
[du]("http://www.ss64.com/bash/du.html")       Estimate file space usage

[echo]("http://www.ss64.com/bash/echo.html")     Display message on screen
[egrep]("http://www.ss64.com/bash/egrep.html")    Search file(s) for lines that match an extended expression
eject    Eject removable media
[enable]("http://www.ss64.com/bash/enable.html")   Enable and disable builtin shell commands
[env]("http://www.ss64.com/bash/env.html")      Environment variables
ethtool  Ethernet card settings
[eval]("http://www.ss64.com/bash/eval.html")     Evaluate several commands/arguments
[exec]("http://www.ss64.com/bash/exec.html")     Execute a command
exit     Exit the shell
[expand]("http://www.ss64.com/bash/expand.html")   Convert tabs to spaces
[export]("http://www.ss64.com/bash/export.html")   Set an environment variable
[expr]("http://www.ss64.com/bash/expr.html")     Evaluate expressions

[false]("http://www.ss64.com/bash/false.html")    Do nothing, unsuccessfully
[fdformat]("http://www.ss64.com/bash/fdformat.html") Low-level format a floppy disk
[fdisk]("http://www.ss64.com/bash/fdisk.html")    Partition table manipulator for Linux
[fgrep]("http://www.ss64.com/bash/fgrep.html")    Search file(s) for lines that match a fixed string
file     Determine file type
[find]("http://www.ss64.com/bash/find.html")     Search for files that meet a desired criteria
[fmt]("http://www.ss64.com/bash/fmt.html")      Reformat paragraph text
[fold]("http://www.ss64.com/bash/fold.html")     Wrap text to fit a specified width.
[for]("http://www.ss64.com/bash/for.html")      Expand words, and execute commands
format   Format disks or tapes
free     Display memory usage
[fsck]("http://www.ss64.com/bash/fsck.html")     File system consistency check and repair
ftp      File Transfer Protocol
[function]("http://www.ss64.com/bash/function.html") Define Function Macros

[gawk]("http://www.ss64.com/bash/gawk.html")     Find and Replace text within file(s)
[getopts]("http://www.ss64.com/bash/getopts.html")  Parse positional parameters
[grep]("http://www.ss64.com/bash/grep.html")     Search file(s) for lines that match a given pattern
[groups]("http://www.ss64.com/bash/groups.html")   Print group names a user is in
[gzip]("http://www.ss64.com/bash/gzip.html")     Compress or decompress named file(s)

[hash]("http://www.ss64.com/bash/hash.html")     Remember the full pathname of a name argument
[head]("http://www.ss64.com/bash/head.html")     Output the first part of file(s)
[history]("http://www.ss64.com/bash/history.html")  Command History
[hostname]("http://www.ss64.com/bash/hostname.html") Print or set system name

[id]("http://www.ss64.com/bash/id.html")       Print user and group id's
[if]("http://www.ss64.com/bash/if.html")       Conditionally perform a command
[ifconfig]("http://www.ss64.com/bash/ifconfig.html") Configure a network interface
[import]("http://www.ss64.com/bash/import.html")   Capture an X server screen and save the image to file
[install]("http://www.ss64.com/bash/install.html")  Copy files and set attributes

[join]("http://www.ss64.com/bash/join.html")     Join lines on a common field

[kill]("http://www.ss64.com/bash/kill.html")     Stop a process from running

[less]("http://www.ss64.com/bash/less.html")     Display output one screen at a time
[let]("http://www.ss64.com/bash/let.html")      Perform arithmetic on shell variables
[ln]("http://www.ss64.com/bash/ln.html")       Make links between files
[local]("http://www.ss64.com/bash/local.html")    Create variables
[locate]("http://www.ss64.com/bash/locate.html")   Find files
[logname]("http://www.ss64.com/bash/logname.html")  Print current login name
[logout]("http://www.ss64.com/bash/logout.html")   Exit a login shell
[look]("http://www.ss64.com/bash/look.html")     Display lines beginning with a given string
[lpc]("http://www.ss64.com/bash/lpc.html")      Line printer control program
[lpr]("http://www.ss64.com/bash/lpr.html")      Off line print
lprint   Print a file
lprintd  Abort a print job
lprintq  List the print queue
[lprm]("http://www.ss64.com/bash/lprm.html")     Remove jobs from the print queue
[ls]("http://www.ss64.com/bash/ls.html")       List information about file(s)
lsof     List open files

make     Recompile a group of programs
[man]("http://www.ss64.com/bash/man.html")      Help manual
[mkdir]("http://www.ss64.com/bash/mkdir.html")    Create new folder(s)
[mkfifo]("http://www.ss64.com/bash/mkfifo.html")   Make FIFOs (named pipes)
mkisofs  Create an hybrid ISO9660/JOLIET/HFS filesystem
[mknod]("http://www.ss64.com/bash/mknod.html")    Make block or character special files
[more]("http://www.ss64.com/bash/more.html")     Display output one screen at a time
[mount]("http://www.ss64.com/bash/mount.html")    Mount a file system
[mtools]("http://www.ss64.com/bash/mtools.html")   Manipulate MS-DOS files
[mv]("http://www.ss64.com/bash/mv.html")       Move or rename files or directories

netstat  Networking information
[nice]("http://www.ss64.com/bash/nice.html")     Set the priority of a command or job
[nl]("http://www.ss64.com/bash/nl.html")       Number lines and write files
[nohup]("http://www.ss64.com/bash/nohup.html")    Run a command immune to hangups
[nslookup]("http://www.ss64.com/bash/nslookup.html") Query Internet name servers interactively

[passwd]("http://www.ss64.com/bash/passwd.html")   Modify a user password
[paste]("http://www.ss64.com/bash/paste.html")    Merge lines of files
pathchk  Check file name portability
[ping]("http://www.ss64.com/bash/ping.html")     Test a network connection
[popd]("http://www.ss64.com/bash/popd.html")     Restore the previous value of the current directory
[pr]("http://www.ss64.com/bash/pr.html")       Prepare files for printing
printcap Printer capability database
printenv Print environment variables
[printf]("http://www.ss64.com/bash/printf.html")   Format and print data
[ps]("http://www.ss64.com/bash/ps.html")       Process status
[pushd]("http://www.ss64.com/bash/pushd.html")    Save and then change the current directory
[pwd]("http://www.ss64.com/bash/pwd.html")      Print Working Directory

[quota]("http://www.ss64.com/bash/quota.html")    Display disk usage and limits
[quotacheck]("http://www.ss64.com/bash/quotacheck.html") Scan a file system for disk usage
[quotactl]("http://www.ss64.com/bash/quotactl.html") Set disk quotas

[ram]("http://www.ss64.com/bash/ram.html")      ram disk device
[rcp]("http://www.ss64.com/bash/rcp.html")      Copy files between two machines.
[read]("http://www.ss64.com/bash/read.html")     read a line from standard input
[readonly]("http://www.ss64.com/bash/readonly.html") Mark variables/functions as readonly
remsync  Synchronize remote files via email
[return]("http://www.ss64.com/bash/return.html")   Exit a shell function
[rm]("http://www.ss64.com/bash/rm.html")       Remove files
[rmdir]("http://www.ss64.com/bash/rmdir.html")    Remove folder(s)
[rsync]("http://www.ss64.com/bash/rsync.html")    Remote file copy (Synchronize file trees)

screen   Terminal window manager
scp      Secure copy (remote file copy)
[sdiff]("http://www.ss64.com/bash/sdiff.html")    Merge two files interactively
[sed]("http://www.ss64.com/bash/sed.html")      Stream Editor
[select]("http://www.ss64.com/bash/select.html")   Accept keyboard input
[seq]("http://www.ss64.com/bash/seq.html")      Print numeric sequences
[set]("http://www.ss64.com/bash/set.html")      Manipulate shell variables and functions
sftp     Secure File Transfer Program
[shift]("http://www.ss64.com/bash/shift.html")    Shift positional parameters
[shopt]("http://www.ss64.com/bash/shopt.html")    Shell Options
[shutdown]("http://www.ss64.com/bash/shutdown.html") Shutdown or restart linux
[sleep]("http://www.ss64.com/bash/sleep.html")    Delay for a specified time
[sort]("http://www.ss64.com/bash/sort.html")     Sort text files
[source]("http://www.ss64.com/bash/source.html")   Run commands from a file `.'
[split]("http://www.ss64.com/bash/split.html")    Split a file into fixed-size pieces
[ssh]("http://en.wikipedia.org/wiki/Secure_Shell")      Secure Shell client (remote login program)
strace   Trace system calls and signals
[su]("http://www.ss64.com/bash/su.html")       Substitute user identity
[sum]("http://www.ss64.com/bash/sum.html")      Print a checksum for a file
[symlink]("http://www.ss64.com/bash/symlink.html")  Make a new name for a file
[sync]("http://www.ss64.com/bash/sync.html")     Synchronize data on disk with memory

[tail]("http://www.ss64.com/bash/tail.html")     Output the last part of files
[tar]("http://www.ss64.com/bash/tar.html")      Tape ARchiver
[tee]("http://www.ss64.com/bash/tee.html")      Redirect output to multiple files
[test]("http://www.ss64.com/bash/test.html")     Evaluate a conditional expression
[time]("http://www.ss64.com/bash/time.html")     Measure Program running time
[times]("http://www.ss64.com/bash/times.html")    User and system times
[touch]("http://www.ss64.com/bash/touch.html")    Change file timestamps
[top]("http://www.ss64.com/bash/top.html")      List processes running on the system
[traceroute]("http://www.ss64.com/bash/traceroute.html") Trace Route to Host
trap     Run a command when a signal is set(bourne)
[tr]("http://www.ss64.com/bash/tr.html")       Translate, squeeze, and/or delete characters
[true]("http://www.ss64.com/bash/true.html")     Do nothing, successfully
[tsort]("http://www.ss64.com/bash/tsort.html")    Topological sort
[tty]("http://www.ss64.com/bash/tty.html")      Print filename of terminal on stdin
[type]("http://www.ss64.com/bash/type.html")     Describe a command

[ulimit]("http://www.ss64.com/bash/ulimit.html")   Limit user resources
[umask]("http://www.ss64.com/bash/umask.html")    Users file creation mask
umount   Unmount a device
[unalias]("http://www.ss64.com/bash/alias.html")  Remove an alias
[uname]("http://www.ss64.com/bash/uname.html")    Print system information
[unexpand]("http://www.ss64.com/bash/unexpand.html") Convert spaces to tabs
[uniq]("http://www.ss64.com/bash/uniq.html")     Uniquify files
[units]("http://www.ss64.com/bash/units.html")    Convert units from one scale to another
[unset]("http://www.ss64.com/bash/unset.html")    Remove variable or function names
[unshar]("http://www.ss64.com/bash/unshar.html")   Unpack shell archive scripts
[until]("http://www.ss64.com/bash/until.html")    Execute commands (until error)
[useradd]("http://www.ss64.com/bash/useradd.html")  Create new user account
[usermod]("http://www.ss64.com/bash/usermod.html")  Modify user account
[users]("http://www.ss64.com/bash/users.html")    List users currently logged in
[uuencode]("http://www.ss64.com/bash/uuencode.html") Encode a binary file 
[uudecode]("http://www.ss64.com/bash/uuencode.html") Decode a file created by uuencode

v        Verbosely list directory contents (`ls -l -b')
vdir     Verbosely list directory contents (`ls -l -b')
[vi]("http://www.ss64.com/bash/vi.html")       Text Editor

[watch]("http://www.ss64.com/bash/watch.html")    Execute/display a program periodically
[wc]("http://www.ss64.com/bash/wc.html")       Print byte, word, and line counts
[whereis]("http://www.ss64.com/bash/whereis.html")  Report all known instances of a command    
[which]("http://www.ss64.com/bash/which.html")    Locate a program file in the user's path. 
[while]("http://www.ss64.com/bash/while.html")    Execute commands
[who]("http://www.ss64.com/bash/who.html")      Print all usernames currently logged in
whoami   Print the current user id and name (`id -un')
Wget     Retrieve web pages or files via HTTP, HTTPS or FTP

[xargs]("http://www.ss64.com/bash/xargs.html")    Execute utility, passing constructed argument list(s)
[yes]("http://www.ss64.com/bash/yes.html")      Print a string until interrupted

[.]("http://www.ss64.com/bash/source.html")        Run a command script in the current shell
[###]("http://www.ss64.com/bash/rem.html")      Comment / Remark

---

### Post by stinger30au on 2008-05-07
a great tutorial on how to network ubuntu to xp
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

--------------------------------------------------------------------------------------------------------

did you know that ubuntu has a ram disk or ram disc or ram drive built in to it

it lives here

/dev/shm

its also auto resizing as well!
good thinking ubuntu team!
--------------------------------------------------------------------------------------------------------
mount and unmount iso images via script
[http://ubuntuforums.org/showthread.php?t=590005](http://ubuntuforums.org/showthread.php?t=590005)
--------------------------------------------------------------------------------------------------------
Ubuntu security for those coming from windows
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)
--------------------------------------------------------------------------------------------------------
gnome wall paper changer
to chnage wall paper at either set timed intervals or change at every restart, install program called "wallpaper tray"
this is done via system -> administration -> synaptic package manager
then search on wall paper and scroll down till you see wallpaper tray , insert tick in box next to it and hit the apply button.
once installed you can find it at applications -> graphics -> wallpaper tray
--------------------------------------------------------------------------------------------------------
the change  the screensaver photos i did a quick search of the net and found this

[http://cro.alienpants.com/index.php/2008/01/04/customising-the-pictures-folder-screensaver-in-ubuntu-gutsy/](http://cro.alienpants.com/index.php/2008/01/04/customising-the-pictures-folder-screensaver-in-ubuntu-gutsy/)

i have 8.04 and it works fine

         One of the default screensavers included with Ubuntu 7.10 is one that will display whatever pictures you have saved in your &#8216;Pictures&#8217; folder (/home/<username>/Pictures). The screensaver will randomly display a picture from this and any subfolders. 
 However, there&#8217;s no way of customsing which folder the screensaver reads if you want to use your Pictures folder to store pictures, but manage which of these images is used.
 A workaround is as follows:
 
[LIST]
[*]Create a new folder somewhere (it doesn&#8217;t have to be under the &#8216;Pictures&#8217; folder)
[*]Open a terminal window (select Terminal under Accessories)
[*]enter the following: gksu gedit /usr/share/applications/screensavers/personal-slideshow.desktop  (enter your password if prompted)
[*]Scroll down to the line (near the end) that begins Exec=slideshow
[*]Add the following after this command: --location=<your pictures path>  (You will have to use standard escape sequences if you have spaces in the path.)
[*]Here&#8217;s an example: Exec=slideshow --location=/home/myusername/Pictures/My\ Screensaver
[/LIST]
 And that&#8217;s it. Save the file, and restart your screensaver. It will now only search for pictures in your chosen folder.
     
--------------------------------------------------------------------------------------------------------
while on the subject of screen savers i stumbled across this handy utility at [www.getdeb.net]("http://www.getdeb.net")  it is in the system tools category

[FONT=Verdana,Arial][SIZE=2]xFX Screensaver Settings is a complete replacement for the gnome-screensaver application providing all the features from the Gnome version and additional configuration options. [/SIZE][/FONT]

home page is here
[http://software.xfx.net/utilities/sss/](http://software.xfx.net/utilities/sss/)

it allows to in to the properties of each screen saver that is there by default. you can even change the text on one of the screen savers so rather then it saying linux kernal blah blah blah, you can make it say what ever you like.
you can also point to the directory you have all your photos saved for to be used as a screen saver.
--------------------------------------------------------------------------------------------------------
another thing to do while on the screen saver subject is to create a symbolic lnk to your pictures directory.

click on places - > pictures
now resize the window a little so you may fit another natalus window on the screen and have both viewable at once.

make sure you have compiz fuzion turned off as well or you will just rotate the windows on the next step.

go to the directory with the photos you want to use and highlight the directory then then hold down the **** and control keys.

while holding those down click on the directory and drag it to the pictures directory
in the pictures directory you will now see a link to that directory with a little arrow.
done
--------------------------------------------------------------------------------------------------------
If you need to create an image of a cd or dvd be it an iso file or what ever you can do this very easy a very handy bit of s/w in the repos.

Its called Brasero. install it via add remove programs or synaptic then start the app up.
once started click on disc copy.
then tell it what cd or dvd drive to read from, and then in the lower box tell it the file name and image type to write and tell it where to save it.
when you tell it to create the image it will take about 30 seconds before it decoed to write the info.... dank ask why, i have no idea, but it works anyhow. and when when copying it has a progress meter to tell you how far it has gone as well.
--------------------------------------------------------------------------------------------------------
if you have the need for a server there is a few tools that can be installed from repos

the easiest way for newbies is to just
open a terminal.  

     Code:
     sudo apt-get install ebox ebox-all 
and go from there.   


There is also the gadmin tools 

     Code:
      apt-cache search gadmin 
You can also install webmin.  
[www.webmin.com]("http://www.webmin.com/")
--------------------------------------------------------------------------------------------------------
[http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)
plenty  of nautilus scripts to do very useful things like, right click and open command prompt here, highlight files and send to Thunderbird and other stuff
--------------------------------------------------------------------------------------------------------

---

### Post by stinger30au on 2008-07-07
i bought myself a netgear WPN111 usb wireless dongle today. works fine in xp and followed the directions here to the letter

[http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)

and it also runs fine in 8.04!

Yee-haw!
======================================================================

For a handy native ubuntu scan2pdf program, follow this thread
[http://ubuntuforums.org/showthread.php?t=62636&page=58](http://ubuntuforums.org/showthread.php?t=62636&page=58)

install is easy

sudo gedit /etc/apt/sources.list

Just add the following line to your /etc/apt/sources.list: 	Code:
 	deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) <release> main

deb-src [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) <release> main 
where <release> is the version of Ubuntu you are using. hardy & gutsy

once added then save and exit.
from shell prompt do this[FONT=monospace]

[/FONT]sudo apt-get update

and then this

sudo apt-get install gscan2pdf

If you want to open gscan2pdf go to Applications&#8212;>Graphics&#8212;>gscan2pdf

---

### Post by stinger30au on 2008-07-08
> **stinger30au said:**
> i bought myself a netgear WPN111 usb wireless dongle today. works fine in xp and followed the directions here to the letter

[http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)

and it also runs fine in 8.04!

Yee-haw!
======================================================================

For a handy native ubuntu scan2pdf program, follow this thread
[http://ubuntuforums.org/showthread.php?t=62636&page=58](http://ubuntuforums.org/showthread.php?t=62636&page=58)

install is easy

sudo gedit /etc/apt/sources.list

Just add the following line to your /etc/apt/sources.list:     Code:
     deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) <release> main

deb-src [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) <release> main 
where <release> is the version of Ubuntu you are using. hardy & gutsy

once added then save and exit.
from shell prompt do this[FONT=monospace]

[/FONT]sudo apt-get update

and then this

sudo apt-get install gscan2pdf

If you want to open gscan2pdf go to Applications&#8212;>Graphics&#8212;>gscan2pdf
======================================================================

video editing with ubuntu
[http://ubuntuforums.org/showthread.php?t=850984](http://ubuntuforums.org/showthread.php?t=850984)

and how to instal firewire drivers for video camera
[http://ubuntuforums.org/showthread.php?t=850984](http://ubuntuforums.org/showthread.php?t=850984)


list of cameras compatable with
[http://www.linux1394.org/hcl.php?class_id=3](http://www.linux1394.org/hcl.php?class_id=3)

======================================================================

how to setup audio/video correctly
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
======================================================================

---

