---
title: "Skype installation and dependencies"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Arrgoss on 2007-11-25
Hi,

I'm a total newbie in Linux. I installed Ubuntu 6.06 LTS (I could not install version 7.10) in my old laptop yesterday and has come back to live! I had some problems installing Skype, and would like to learn something about it, Any comment or suggestion is welcome.

I wanted to install Skype, so I downloaded the last (not beta) version: skype-debian_1.4.0.118-1_i386.deb. When I tried to install it by simple double-clicking, I got the following error message: "Error: Dependency is not satisfiable: libasound2". I checked, and reinstalled the package with libasound2, and it is OK, but the message still appears and Skype doesn't get installed.

Then, I tried the command "sudo get-apt install skype", but it could not find the package, am I missing something in this command?

Eventually, I installed it using the repositories from Medibuntu, but it installed an older version. What shall I do if I want the newer version?

Thanks a lot.

---

### Post by jken146 on 2007-11-25
The versions in the official Ubuntu (or Medibuntu) repositories are well tested and (almost) bound to work, so that's why they're not always up to date.  They will be updated eventually though and you'll get the updates automatically.

There is a Skype apt repository however, which will contain the latest stable linux version.  To install this, either go to System > Administration > Software Sources > 3rd Party and add the this line
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
or if you can't do that (not sure if you can on 6.06) then
```
sudo gedit /etc/apt/sources.list
```
then append the deb.... line there at the end.

You can then do ```
sudo apt-get install <package>
```
But I would look in Synaptic to choose the right one if you have more than one repository with packages called skype.

---

### Post by Arrgoss on 2007-11-25
Thanks jken146,
I have added the repository you suggested, and now Synaptics indded tells me there is a newer Skype version than the one installed. When I try to upgrade, however, I get the following "unresolvable dependencies"
> skype:
  Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
 Depends: libqt4-core but it is not going to be installed
 Depends: libqt4-gui but it is not going to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

Maybe I should be happy to have a working version in my second day :)

---

### Post by Pumalite on 2007-11-25
Exactly. A working version beats anything.

---

### Post by of_darkness on 2007-11-25
> **Arrgoss said:**
> Thanks jken146,
I have added the repository you suggested, and now Synaptics indded tells me there is a newer Skype version than the one installed. When I try to upgrade, however, I get the following "unresolvable dependencies"


Maybe I should be happy to have a working version in my second day :)
i have the medibuntu version installed..

My sources.list

> ######################################################################################################################################################
###ubuntu + kubuntu main pakages + apt on cd + live cd
######################################################################################################################################################
# deb cdrom:[APTonCD for ubuntu gutsy - i386 (2007-07-31 14:42) DVD1]/ /
# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ gutsy main restricted
# deb cdrom:[APTonCD for ubuntu gutsy - i386 (2007-07-31 14:42) DVD1]/ /
# deb-src cdrom:[APTonCD for ubuntu gutsy - i386 (2007-06-02 15:48) DVD1]/ /
#------------------------------------------------------------------------------------
# Ubuntu Main
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe restricted main multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe restricted main multiverse
#--------------------------------------------------------------------------------------------
# kubuntu.org packages for the latest KDE version
deb [http://kubuntu.org/packages/kde-latest/](http://kubuntu.org/packages/kde-latest/) feisty main
deb-src [http://kubuntu.org/packages/kde-latest/](http://kubuntu.org/packages/kde-latest/) feisty main
##GPG Key Information
##wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG) | sudo apt-key add
#----------------------------------------------------------------------------------------------------
#kubuntu-packages-jriddell-key.GPG
# kubuntu.org packages for the latest Koffice version
deb [http://kubuntu.org/packages/koffice-latest/](http://kubuntu.org/packages/koffice-latest/) edgy main
deb-src [http://kubuntu.org/packages/koffice-latest/](http://kubuntu.org/packages/koffice-latest/) edgy main
#GPG Key Information
#wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG) | sudo apt-key add
#------------------------------------------------------------------------------------------
# Latest Amarok Packages
deb [http://kubuntu.org/packages/amarok-145/](http://kubuntu.org/packages/amarok-145/) edgy main
deb-src [http://kubuntu.org/packages/amarok-145/](http://kubuntu.org/packages/amarok-145/) edgy main
##GPG Key Information
##wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.GPG) | sudo apt-key add
#--------------------------------------------------------------------------------------------------------

#------------------------------------------------------------------------------------------
# archive.kubuntu.de / archive.czessi.net
deb [http://archive.czessi.net/ubuntu/](http://archive.czessi.net/ubuntu/) gutsy main restricted universe multiverse preview
deb-src [http://archive.czessi.net/ubuntu/](http://archive.czessi.net/ubuntu/) gutsy main restricted universe multiverse preview
#GPG Key Information
#wget [http://archive.czessi.net/ubuntu/kczessi.GPG](http://archive.czessi.net/ubuntu/kczessi.GPG) | sudo apt-key add kczessi.GPG
#-----------------------------------------------------------------------------------------
#---------------------------------------------------------------------
######################################################################################################################################################
###3d party repos
######################################################################################################################################################
# Treviño's Ubuntu gutsy EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...

# deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty eyecandy
#---------------------------------------------------------------------------------------------------------
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) gutsy main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) gutsy main restricted universe multiverse

#--------------------------------------------------------------------------------------------------------------
#-------------------------------------------------------------------
# Canonical Commercial Repository (Opera,Real Player10.. etc)
#----------------------------------------------------------------------------------------
# Seveas' Ubuntu packages

#This repository is created by Dennis Kaarsemaker <dennis@kaarsemaker.net>. If you have problems using these packages contact me via E-mail or IRC(Seveas on Freenode).
#The following distribution releases are available

#dapper-seveas
#    These packages are suitable on Ubuntu Dapper (6.06 LTS). Using them in other versions or other distributions may work, but is not supported.
#edgy-seveas
#    These packages are suitable on Ubuntu Edgy (6.10). Using them in other versions or other distributions may work, but is not supported.
#gutsy-seveas
#    These packages are suitable on Ubuntu Feisty (7.04). Using them in other versions or other distributions may work, but is not supported.

#The following architectures are supported
#i386 · ppc · amd64
#Authenticated packages
#Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is 1135D466. You can enter this key into the APT trusted #keys database with the following command:
#wget [http://seveas.theplayboymansion.net/seveas/1135D466.gpg](http://seveas.theplayboymansion.net/seveas/1135D466.gpg) -o- | sudo apt-key add -
#The following mirrors are available

#    * [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx)
#      Sponsored by Brett Johnson
#    * [http://seveas.imbrandon.com](http://seveas.imbrandon.com)
#      Sponsored by Brandon Holtsclaw
#    * [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/)
#      Sponsored by Niels Roosen
#    * [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas)
#      Sponsored by Henri Cook (orion-hosting.co.uk)
#    * [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/)
#      Sponsored by Peter Lieverdink
#    * [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl)
#      Sponsored by Søren Hansen

# Seveas' Ubuntu packages
#Release info
#Release name:  gutsy-seveas
#Version:       7.04
#These packages are suitable on Ubuntu Feisty (7.04). Using them in other versions or other distributions may work, but is not supported.

#The following components are available:

#all (browse contents)
#    This is the 'all' metacomponent containing all packages in all components.
#backports (browse contents)
#    No description
#custom (browse contents)
#    No description
#extras (browse contents)
#    This section contains several packages I created, or ported to Ubuntu and for some reason are not (yet) suitable for the main archives.
#freenx (browse contents)
#    This section contains freenx and nx packages, havily based on the old kanotix ones but with the new upstream version 2.1.0 (nx) and 0.6.0 (freenx).
#seveas-meta (browse contents)
#    I have created a set of meta-packages to ease installing software suites for specific tasks (like multimedia, or Ubuntu development).
deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) gutsy-seveas all
deb-src [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) gutsy-seveas all
#-----------------------------------------------------------------------------------------
# Bleeding Edge Wine Packages
deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) gutsy main
deb-src [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) gutsy main
#------------------------------------------------
# VoIP Ubuntu packages (Asterisk, ekiga, kphone&#8230;)
deb [http://pkg-voip.buildserver.net/ubuntu/](http://pkg-voip.buildserver.net/ubuntu/) gutsy main
#------------------------------------------------------------------------------------------
# Samba
# deb [http://www.linux2go.dk/ubuntu/](http://www.linux2go.dk/ubuntu/) gutsy main
# deb-src [http://www.linux2go.dk/ubuntu/](http://www.linux2go.dk/ubuntu/) gutsy main
#------------------------------------------------------------------------------------------
#------------------------------------------------------------------------------------------
# Cafuego&#8217;s Edgy Stuff: Broadcom kernel firmwares, google-earth, beagle
deb [http://au.ubuntu.cafuego.net/](http://au.ubuntu.cafuego.net/) gutsy-cafuego all
deb-src [http://au.ubuntu.cafuego.net/](http://au.ubuntu.cafuego.net/) gutsy-cafuego all
#GPG Key Information
#wget [http://au.ubuntu.cafuego.net/969F3F57.GPG](http://au.ubuntu.cafuego.net/969F3F57.GPG) -o- | sudo apt-key add -
#------------------------------------------------------------------------------------------
# Debuntu Ubuntu edgy packages
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
#GPG Key Information
# wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) | sudo apt-key add GPG-Key-chantra.txt
#------------------------------------------------------------------------------------------
# BMPx Edgy Repository
deb [http://files.beep-media-player.org/packages/ubuntu/](http://files.beep-media-player.org/packages/ubuntu/) edgy main
deb-src [http://files.beep-media-player.org/packages/ubuntu/](http://files.beep-media-player.org/packages/ubuntu/) edgy main
#GPG Key Information
#sudo apt-key add bmp-packages.pubkey
#or
#sudo apt-key add [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
#------------------------------------------------------------------------------------------
# Morgoth Repository (Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacity&#8230;)
deb [http://morgoth.free.fr/ubuntu/](http://morgoth.free.fr/ubuntu/) gutsy-backports main
deb-src [http://morgoth.free.fr/ubuntu/](http://morgoth.free.fr/ubuntu/) gutsy-backports main
#GPG Key Information
#sudo apt-key add [http://morgoth.free.fr/ubports/dlsignkey.php](http://morgoth.free.fr/ubports/dlsignkey.php)
#------------------------------------------------------------------------------------------
# ATi & nVidia drivers Ubuntu packages
# deb [http://www.albertomilone.com/drivers/edgy/latest/32bit/](http://www.albertomilone.com/drivers/edgy/latest/32bit/) binary/
#For 32 bit
#For 64 bit
#GPG Key Information
#wget [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)
#GPG &#8211;import tseliot.asc
#GPG &#8211;export &#8211;armor [email]albertomilone@alice.it[/email] | sudo apt-key add -
#------------------------------------------------------------------------------------------
#Automatix
##deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) feisty main
#GPG Key Information
#wget [http://www.getautomatix.com/apt/key.GPG.asc](http://www.getautomatix.com/apt/key.GPG.asc)
 #GPG --import key.GPG.asc
 #GPG --export --armor 521A9C7C | sudo apt-key add -
#------------------------------------------------------------------------------------------
# SoS: SeerOfSouls
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
#GPG Key Information
#wget [http://seerofsouls.com/keys/hawkwind.asc](http://seerofsouls.com/keys/hawkwind.asc) | sudo apt-key add hawkwind.asc
#------------------------------------------------------------------------------------------
# Treviño&#8217;s Ubuntu Dapper Repository
# Many &#8220;random&#8221; software: aMule, amsn, gnash, google-earth, stellarium, moto4lin
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty 3v1n0
#GPG Key Information
#wget [http://3v1n0.tuxfamily.org/EDD1E155.GPG](http://3v1n0.tuxfamily.org/EDD1E155.GPG) -o- | sudo apt-key add -
#------------------------------------------------------------------------------------------
deb [http://easyubuntu.cafuego.net/](http://easyubuntu.cafuego.net/) main easyubuntu
#-----------------------------------------------------------------------------------------------
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main
deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) gutsy main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main
deb-src [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) gutsy main
#------------------------------------------------------------------------------------------
#AUTOMATIX BLEEDER REPOS START
## deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main
#AUTOMATIX BLEEDER REPOS END
#------------------------------------------------------------------------------------------
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#------------------------------------------------------------------------------------------
#------------------------------------------------------------------------------------------
deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) edgy main
#------------------------------------------------------------------------------------------
deb [http://asher256-repository.tuxfamily.org/](http://asher256-repository.tuxfamily.org/) edgy main dupdate french
deb [http://asher256-repository.tuxfamily.org/](http://asher256-repository.tuxfamily.org/) ubuntu main dupdate french
#----------------------------------------------------------------------
#------------------------------------------------------------------------------------------------
# qBittorrent : a C++ / Qt4 Bittorrent Client

deb [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./
#------------------------------------------------------------------------------------------------------------------
#------------------------------------------------------------------------------------------------------------------------
# Avant-Window-Navigator repository:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

#gpgkey:
#wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
#sudo apt-key add 8434D43A.gpg
#rm 8434D43A.gpg
#---------------------------------------------------------------------------------------------------------------------
#kiosysinfo repository

deb [http://download.tuxfamily.org/kiosysinfo/apt/](http://download.tuxfamily.org/kiosysinfo/apt/) binary/
#--------------------------------------------------------------------
#--------------------------------------------------------------------
#Miro The only video application that does it all. repo.
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
#------------------------------------------------------------------------------

##################################################################################################################
##Debian repos
##################################################################################################################
# Upstream Opera
#This repository contains Opera packages for the i386, sparc, and powerpc architectures.

#/opera/
#/opera-beta/

### Example apt source configuration (uncomment the version you want)

# Opera Browser - Production release
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) potato non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) woody non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sarge non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free

# Opera Browser - Beta release
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) potato non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) woody non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) sarge non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) etch non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-free
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) sid non-free
#------------------------------------------------------------------------------------------
# Skype for linux
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
#------------------------------------------------------------------------------------------
#Iuculano's debian packages v7.04
#Thunderbird 2 feisty backport
#wget [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg) -o- | sudo apt-key add -

deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird


#Iuculano's debian packages v7.04
#all
#is is the 'all' metacomponent containing all packages in all components.
#
# deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty all
# deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty all


#Iuculano's debian packages v7.04
#Amsn latest development version (SVN Snapshot)
#
# deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn
# deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty amsn


#Iuculano's debian packages v7.04
#ck-kernel
#Ubuntu kernel optimized for Pentium4 (686-ck) and Core2 (core2-ck) (good also for all core2 notebook). This #kernel has CK patch ([http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)) These are patches designed to improve #system responsiveness with specific emphasis on the desktop, but suitable to any workload.
#
# deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy ck-kernel
# deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy ck-kernel
# deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main --
#------------------------------------------------------------------------------------------
# deb [http://moblock-deb.sourceforge.net/debian/](http://moblock-deb.sourceforge.net/debian/) unstable main
# deb-src [http://moblock-deb.sourceforge.net/debian/](http://moblock-deb.sourceforge.net/debian/) unstable main
#----------------------------------------------------------------
deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) unstable main
#----------------------------------------------------------------------------------------------
#Opensync and additionally needed Debian Unstable Backports for Ubuntu Feisty Fawn:


#Howto add my gpg key for this repro

#gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
#gpg --export CB210090B029CB84 | sudo apt-key add -
#------------------------------------------------------------------------------------------
# GCompris, Televidilo, Kdocker, etc
##deb [http://thomas.pub.enix.org/debian/](http://thomas.pub.enix.org/debian/) edgy main
#------------------------------------------------------------------------------------------
# GiFT P2P Network
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
#GPG Key Information
#GPG --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
 #GPG --armor --export F00175CA | sudo apt-key add -
#------------------------------------------------------------------------------------------
# Easycam packages
deb [http://blognux.free.fr/debian/](http://blognux.free.fr/debian/) unstable main
#------------------------------------------------------------------------------------------
#------------------------------------------------------------------------------------------
deb-src [http://moblock-deb.sourceforge.net/debian/](http://moblock-deb.sourceforge.net/debian/) unstable main
#------------------------------------------------------------------------------------------
# Google picasa
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# GPG Key Information
# wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | apt-key add -
#-------------------------------------------------------------------------------
#------------------------------------------------------------------------------------------

########################################################################################################################
#######################################################################################################################
######################################################################################################################
####################################     gpg keys        ############################################################
#####################################################################################################################
#######################################################################################################################
#########################################################################################################################

# [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) -
#
# wget [http://www.michaelbiebl.de/biebl.asc](http://www.michaelbiebl.de/biebl.asc)
# sudo apt-key add biebl.asc
#''''''''''''''''
# Seveas' Ubuntu packages
# [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl)
#
# GPG Key Information
# wget [http://seveas.theplayboymansion.net/seveas/11#](http://seveas.theplayboymansion.net/seveas/11#) 5D466.gpg -o- | sudo apt-key add
#''''''''''''''''''''''''''''''''''''
# [http://deb.opera.com/](http://deb.opera.com/)
#
# GPG Key Information
# The archive gpg fingerprint
#
# pub   1024D/6A423791 2006-09-26 [expires: 2009-09-25]
#      Key fingerprint = CD5A 9776 9F6E F4D9 EBCD  8F92 0334 3153 6A42 3791
#      uid                  Opera Software Archive Automatic Signing Key
# sub   2048g/BEAEDCB7 2006-09-26 [expires: 2009-09-25]
#
#
#
# sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# sudo gpg --fingerprint 6A423791
# sudo gpg --armor --export  6A423791| sudo apt-key add -
#
#''''''''''''''''''''
# Iuculano's debian packages
# [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it)
#
# GPG Key Information
# wget [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg) -o- | sudo apt-key add -
#''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# [http://thomas.pub.enix.org](http://thomas.pub.enix.org)
#
# GPG Key Information
# gpg --keyserver pgpkeys.mit.edu --recv-key 98D3F7A7
# gpg -a --export 98D3F7A7 | sudo apt-key add -
#''''''''''''''''''''''''''''''''''''''''''''''''''
# [http://www.in.fh-merseburg.de](http://www.in.fh-merseburg.de)
# OpenSync Debian and Ubuntu 0.2x (0.22) packages
#
# GPG Key Information
# gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
# gpg --export CB210090B029CB84 | sudo apt-key add -
#
#''''''''''''''''''''''''''''''''''''''''
# [http://download.tuxfamily.org](http://download.tuxfamily.org)
# Lägga till Compiz-git förråd
# Treviño har öppnat ett förråd för Compiz (git) och Compiz-Fusion (git)
#
# GPG Key Information
# wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -o- | sudo apt-key add -
#'''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# Google software repository
# [http://dl.google.com](http://dl.google.com)
#
# GPG Key Information
# wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | apt-key add -
#''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot # be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc)
#
# GPG Key Information
# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o- | sudo apt-key add - && sudo apt-get update
#'''''''''''''''''''''''''''''''''''''''''''
# archive.kubuntu.de / archive.czessi.net
# [http://archive.czessi.net](http://archive.czessi.net)
#
# GPG Key Information
#
# wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg) | sudo apt-key add kczessi.gpg
#
#'''''''''''''''''''''''''''''''''''''''''''''''''''''
# GiFT P2P Network
# GPG Key Information
#
# gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
# gpg --armor --export F00175CA | sudo apt-key add -
#''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# VoIP Ubuntu packages (Asterisk, ekiga, kphone&#8230;)
# [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net)
#
# GPG Key Information
# wget [http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/Release.gpg](http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/Release.gpg)  | sudo apt-key add Release.gpg
#
#''''''''''''''''''''''''''''''
# Cafuego&#8217;s Edgy Stuff: Broadcom kernel firmwares, google-earth, beagle
#
# GPG Key Information
#
# wget [http://au.ubuntu.cafuego.net/969F3F57.gpg](http://au.ubuntu.cafuego.net/969F3F57.gpg) -o- | sudo apt-key add -
# ''''''''''''''''''''''''''''''''''''''''''''''
# Debuntu Ubuntu edgy packages
#
# GPG Key Information
#
# wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) | sudo apt-key add GPG-Key-chantra.txt
# ''''''''''''''''''''''''''''''''''
# Morgoth Repository (Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacity&#8230;)
#
# GPG Key Information
#
# sudo apt-key add [http://morgoth.free.fr/ubports/dlsignkey.php](http://morgoth.free.fr/ubports/dlsignkey.php)
# ''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# eikiga repository
# [http://snapshots.voxgratia.org](http://snapshots.voxgratia.org)
# GPG Key Information
#
# wget http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg|apt-key add -
# ''''''''''''''''''''''''''''''''''''''''''''''''''''''
# SoS: SeerOfSouls
#
# GPG Key Information
#
# wget [http://seerofsouls.com/keys/hawkwind.asc](http://seerofsouls.com/keys/hawkwind.asc) | sudo apt-key add hawkwind.asc
# '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# EasyUbuntu Packages
#
# GPG Key Information
# wget [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg) -o- | sudo apt-key add -
# '''''''''''''''''''''''''''''''''''''''
#
# '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# MythTV Repository for Ubuntu Linux
#
# GPG Key Information
#
# ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
# nycklarna listade för snabb instalation
# ******************************************************************************
# *****************************************************************************
# wget [http://home.eng.iastate.edu/~superm1/80DF6D58.gpg](http://home.eng.iastate.edu/~superm1/80DF6D58.gpg) -o- | sudo apt-key add -
# wget [http://seveas.theplayboymansion.net/seveas/1135D466.gpg](http://seveas.theplayboymansion.net/seveas/1135D466.gpg) -o- | sudo apt-key add
# wget [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg) -o- | sudo apt-key add -
# wget [http://seerofsouls.com/keys/hawkwind.asc](http://seerofsouls.com/keys/hawkwind.asc) -o- | sudo apt-key add hawkwind.asc
# wget [http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg](http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg) -o-| sudo apt-key add -
# wget -O - [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc) | sudo apt-key add -
# wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) -o- | sudo apt-key add GPG-Key-chantra.txt
# wget [http://au.ubuntu.cafuego.net/969F3F57.gpg](http://au.ubuntu.cafuego.net/969F3F57.gpg) -o- | sudo apt-key add -
# wget [http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/Release.gpg](http://pkg-voip.buildserver.net/ubuntu/dists/gutsy/Release.gpg)  | sudo apt-key add Release.gpg
# wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg) -o- | sudo apt-key add kczessi.gpg
# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o- | sudo apt-key add -
# wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | apt-key add -
# wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -o- | sudo apt-key add -
# wget [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg) -o- | sudo apt-key add -
# wget [http://seveas.theplayboymansion.net/seveas/1135D466.gpg](http://seveas.theplayboymansion.net/seveas/1135D466.gpg) -o- | sudo apt-key add
# wget [http://www.michaelbiebl.de/biebl.asc](http://www.michaelbiebl.de/biebl.asc) -o- | sudo apt-key add biebl.asc
# wget [http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg](http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg) -o-|sudo apt-key add -
# '''''''''''''''''''''''''''''
# obs kör rad för rad
# **********************************
# sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# sudo gpg --fingerprint 6A423791
# sudo gpg --armor --export  6A423791| sudo apt-key add -
# ''''''''''''''''''''
# sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
# sudo gpg --export CB210090B029CB84 | sudo apt-key add -
# sudo gpg --keyserver pgpkeys.mit.edu --recv-key 98D3F7A7
# sudo gpg -a --export 98D3F7A7 | sudo apt-key add -
# ''''''''''''''''''''''''''''''''''''''''''
# sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# sudo gpg --fingerprint 6A423791
# sudo gpg --armor --export  6A423791| sudo apt-key add -
# ''''''''''''''''''''''''''''''''''''''''''''''''''''''
# sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
# sudo gpg --armor --export F00175CA | sudo apt-key add -
# ''''''''''''''''''''''''''''''''''''''''''# Extras Repository (GPG key: 22130E65)
# deb [http://debs.vorian.org/](http://debs.vorian.org/) gutsy extras
# deb-src [http://debs.vorian.org/](http://debs.vorian.org/) gutsy extras'''''''''
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
###################################################################################################################################
deb [http://ppa.launchpad.net/tsimpson/ubuntu](http://ppa.launchpad.net/tsimpson/ubuntu) gutsy main



------------------Disclamer-----------
Note that some of gpg keys are outdated and not updated in the list.. And use of the 3party repos should not be taken lightly, only use them if you know what you are doing and trusting the packger.. but whit that said the uncommnted repos works fine but trouble can come by using 3party repos but is most often solvable by downgrading packges 2 official ubuntu versions.

---

