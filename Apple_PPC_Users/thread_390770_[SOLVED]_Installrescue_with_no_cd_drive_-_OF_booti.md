---
title: "[SOLVED] Install/rescue with no cd drive - O/F booting"
date: 2007-03-22
forum: Apple PPC Users
---

### Post by pxwpxw on 2007-03-22
This thread is a work in progeress about ways to get booted into an install or rescue, other than the straight forward cdrom using cd drive.
Such as netboot, net-install, hd-media iso install, usb stick install and any other ways, when the cdrom buy or burn and boot from cd drive wont work for your Apple Mac ppc New or Old World (non-intel on this thread)
The first posts are general references, useful to me. 
Followed by outlines mostly just pointing to existing installation or howto,  often simple but sometimes hard to find or not quite complete or out of date. 
Expect it to be edited as I ad links and get round to trying things.

**Please post questions or comments on this thread for discussion and that will probably help others with similar needs.**

========================================

**General Booting info links**.

Thanks t**onyr**  
special booting, mini installation, hacking.
[http://www.extremetech.com/article2/0,1697,2132837,00.asp]("http://www.extremetech.com/article2/0,1697,2132837,00.asp")

initrd management.
[http://ubuntuforums.org/showthread.php?t=423963]("http://ubuntuforums.org/showthread.php?t=423963")
================


**Some Applemac Info.**

original iMac devel note
Apple iMac Computer
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/original_iMac/iMacDevNote.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/original_iMac/iMacDevNote.pdf)
================

The iMac Family of Computers
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf)
=================


iMac G3 (Original) User Manual
[http://manuals.info.apple.com/en/iMacG3_originalUserManual.PDF](http://manuals.info.apple.com/en/iMacG3_originalUserManual.PDF)
=================
PowerBook G3  Wikipedia
[http://en.wikipedia.org/wiki/PowerBook_G3]("http://en.wikipedia.org/wiki/PowerBook_G3")

pismo pbg3
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerBook/PowerBook.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerBook/PowerBook.pdf)

wall street pbg3
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerBookG3Series.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerBookG3Series.pdf)
===================

OldWorld Power Mac G3 (beige)
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMac_G3/PowerMac_G3.pdf]("http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMac_G3/PowerMac_G3.pdf")

===================
NewWorld Power Mac G3 (blue and white)
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMacintosh_G3/PowerMacintosh_G3.pdf]("http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/PowerMacintosh_G3/PowerMacintosh_G3.pdf")

===================



===================

**Macosx access to/from ubuntu.**

 - ext2fsx - Tiger support.
[http://sourceforge.net/projects/ext2fsx/p:/]("http://sourceforge.net/projects/ext2fsx/p:/")
================

**Resizing MacosX partitions for ubuntu.** 
 iParted from Coriolis Systems ($ware)
[http://www.coriolis-systems.com/iPartition.php]("http://www.coriolis-systems.com/iPartition.php")

==========

---

### Post by pxwpxw on 2007-03-31
Installi/rescue/booting AppleMacs - my ref links. This post is just a collection of some links i use.
See following posts for application.

**Booting OldWorld** 

BootX - the original
[http://penguinppc.org/historical/benh/]("http://penguinppc.org/historical/benh/")
[http://penguinppc.org/bootloaders/bootx/]("http://penguinppc.org/bootloaders/bootx/")

Bootloaders BootX quik yaboot
[http://penguinppc.org/bootloaders/]("http://penguinppc.org/bootloaders/")


[B]Some links for booting installation from hard drive, to do network or hd-media/iso install/rescue.
[/B]
help

User Documentation
 [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Documentation for Ubuntu 7.04
 [https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

Advanced Topics
 [https://help.ubuntu.com/7.04/advanced-topics/C/index.html](https://help.ubuntu.com/7.04/advanced-topics/C/index.html)

Installing Ubuntu via the alternate CD (choose your architecture)
 [https://help.ubuntu.com/7.04/installation-guide/](https://help.ubuntu.com/7.04/installation-guide/)


Ubuntu Installation Guide-ppc
 [https://help.ubuntu.com/7.04/installation-guide/powerpc/](https://help.ubuntu.com/7.04/installation-guide/powerpc/)

4. Obtaining System Installation Media
 [https://help.ubuntu.com/7.04/installation-guide/powerpc/install-methods.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/install-methods.html)

 4 - Preparing Files for Hard Disk Booting
 [https://help.ubuntu.com/7.04/installation-guide/powerpc/boot-drive-files.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/boot-drive-files.html)

5. Booting the Installation System
 [https://help.ubuntu.com/7.04/installation-guide/powerpc/boot-installer.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/boot-installer.html)

 5- Booting the Installer on PowerPC
 [https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html)
    - Booting from Hard Disk
     [https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#install-drive](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#install-drive)
     
	- Booting NewWorld Macs from OpenFirmware

======================
Packages - ubuntu, debian
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

**ubuntuguide.org/wiki/Ubuntu:Feisty**
[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

Documentation for Ubuntu 6.10 (Edgy Eft)
 [https://help.ubuntu.com/6.10/](https://help.ubuntu.com/6.10/)

Installation Guide (for alternate CD, not for desktop CD) - powerpc.
 [https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html)

Ubuntu Installation Guide610
 [https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html)


Preparing Files for Hard Disk Booting-610
 [https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html)

=====================
Partitions: pdisk for partition maps in macos8, 9, not X
[http://www.cfcl.com/eryk/linux/pdisk/dist/index.html]("http://www.cfcl.com/eryk/linux/pdisk/dist/index.html")

=====================

---

### Post by pxwpxw on 2007-05-30
**Old World install with no cd**.

Outline.

Using installer images on a macos9 partition, and the BootX application/extension, it is possible to boot the linux installer images for a hd-media install from downloaded ubuntu install cd iso, or to boot netinstall images for an network installation from ubuntu  mirrors.

Requires preliminarty macos partioning of hard disk for separate macos and linux partitions,
macos browser or ftp capability for network connection and download of images and the Bootx application. Similar to procedure for OldWorld installation from CD.

Refs:

Installation/OldWorldMacs
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

PowerPCFAQ
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Installer images hd-media, netboot/netinstall.
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/)

Ubuntu Installation Guide
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html)

Debian GNU/Linux Installation Guide (more helpfull for OldWorld macs)
[http://www.debian.org/releases/stable/powerpc/](http://www.debian.org/releases/stable/powerpc/)

BootX
[//http://penguinppc.org/historical/benh/]("//http://penguinppc.org/historical/benh/")

to be continued.

---

### Post by pxwpxw on 2007-06-21
**NewWorld Macs**

Assumes you have macosx installed with free space availabe for ubuntu on your drive. 
==============================

**Network install (feisty704)**

Download the 4 installer boot files: vmlinux, initrd.gz, yaboot, yaboot.conf from
[[COLOR="Red"]current images[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/netboot/")

Then folowing the 
 [[COLOR="Red"]Ubuntu Installation Guide[/COLOR]]("https://help.ubuntu.com/7.04/installation-guide/powerpc/")

 Put the 4 boot files on the macosx partition root. Disregard comments about problems with booting from HFS+ systems, current installer kernels can boot from any macosx system including macosx extended journalled.  

See [[COLOR="Red"]Preparing Files for Hard Disk Booting[/COLOR]]("https://help.ubuntu.com/7.04/installation-guide/powerpc/boot-drive-files.html")
 (Hard Disk Installer Booting for NewWorld Macs)

 Boot yaboot from open firmware.
[[COLOR="Red"]Booting NewWorld Macs from OpenFirmware[/COLOR]]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html#boot-newworld")

At the yaboot "boot:" prompt, hit <tab> for options. If available, server or cli will do a quick console install with no desktop (easily installed later). Read yaboot.conf in macosx to see what are the options, before booting.
==============================

**ISO install. (no burning)**

For 32bit powerpc the hd-media set of vmlinux, initrd.gz, yaboot, yaboot.conf
is good for installing from an Alternate or Server cd .iso on the hard drive.
[[COLOR="Red"]hd-media set[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/hd-media/") **vmlinux initrd.gz** and **yaboot.conf**. Plus  **yaboot**  from the Network Install - current images above.

For 64bit powerpc64
It is also possible to install from a downloaded AlternateCD.iso  using the netboot images, but requires expert option selection of installer iso-scan and load-iso modules.

Note: edgy610 installer had a iso /dev/loop bug 
See [[COLOR="Red"][COLOR="Blue"]john_spiral's i386 howto[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=316093")
mkdir -p /dev/loop && ln /dev/loop0 /dev/loop/0

---

### Post by pxwpxw on 2007-07-26
To do:
**Netboot**

Boot via ethernet from openfirmware for network install.

to be continued

=====.

---

### Post by pxwpxw on 2007-07-26
To do:

USB **Boot from USB flash stick **

to be continued.

====

---

### Post by pxwpxw on 2007-07-26
There have been a few threads recently needing help with install when the cd drive is unusable.
There is an outline of network install or hd-media method above, and some general info links.
If you need/want more explanation, post here, it may help other people.

---

### Post by gvigorus on 2007-07-26
> **pxwpxw said:**
> There have been a few threads recently needing help with install when the cd drive is unusable.
There is an outline of network install or hd-media method above, and some general info links.
If you need/want more explanation, post here, it may help other people.

Are the [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/netboot/) current images okay for HD booting Xubuntu too or these are only for Ubuntu? I want to HDD boot Xubuntu on Powerbook G3 Lomabrd 400Mhz 512RAM 6GB HDD OS 10.2
Thanks

---

### Post by pxwpxw on 2007-07-27
> **gvigorus said:**
> Are the [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current//images/powerpc/netboot/) current images okay for HD booting Xubuntu too or these are only for Ubuntu? I want to HDD boot Xubuntu on Powerbook G3 Lomabrd 400Mhz 512RAM 6GB HDD OS 10.2
Thanks

1. Those images are correct if you want to install everything from the network, but they install ubuntu-desktop by default, however that is easily  avoided, see 2. I would suggest network install if you have high speed network access.

 If you want to download an iso of an install CD to a partition on your hard drive first and then install packages from that, you need the hd-media images and the CD iso.    [https://wiki.ubuntu.com/PowerPCDownloads]("https://wiki.ubuntu.com/PowerPCDownloads")
But see below about the hd-media - probably not feasible with 6GB drive, unless you can first create a separate small partition for the iso, or have an external drive.

2. Either way, the yaboot.conf startup menu for the installer has options including "server". (sometimes "cli" in previous versios). That installs a command line console version initially about 300MB, then you can install your choice of xubuntu-desktop, ubuntu-desktop or kubuntu-desktop. But there is no choice of desktop in the yaboot.conf menu.
If you just do the default install you will get the full ubunut-desktop.

3. The macos partition may get demolished by the ubuntu istaller, so you need to get the install to a usable state first time, because there will be no macos partition to do it again, unless you can reinstall macos. Also this might make the hd-media method unsuitable if the 600MB iso file is also demolished before it can be used. 

 So it is a good idea to do a dummy install to find any problems (abort before any partitioning changes are written to disk). A trial run network install might use around 30 MB. 

Once you have ubuntu running, with network access you can look at other backup options including external drives or usb flash stick and network boot from another computer.

---

