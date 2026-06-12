---
title: "HOWTO: No-CD FreeBSD/NetBSD Installation From Windows or Linux"
date: 2008-01-31
forum: BSD
---

### Post by tuxcantfly on 2008-01-31
[Main Site](http://lubi.sourceforge.net/unetbootin.html)

This guide is for anyone who wants to install FreeBSD or NetBSD without using any external media, such as a CD, Floppy, USB-Drive, or the like. It uses [UNetbootin](http://lubi.sourceforge.net/unetbootin.html) to chainload off the host OS's bootloader (via GRUB4DOS on Windows, and GRUB on Linux), and load the installer for FreeBSD/NetBSD, so that installation can continue via the standard FTP-install approach, or through predownloaded packages on a partition.

Supported *BSDs to be installed: FreeBSD 7.0, FreeBSD 6.3, NetBSD 4.0
Supported OS's to be installed from: Windows, Linux

**Download Locations**

1. Navigate [here](http://lubi.sourceforge.net/unetbootin.html) and pick the appropriate OS to install. Direct links are here: [FreeBSD 7.0](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=265552) [FreeBSD 6.3](https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=260629) [NetBSD 4.0](https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=260607)

**Instructions for Windows**

If using Windows, download the .exe version for whatever OS you want to install, and reboot when prompted. Select the UNetbootin boot option on the next reboot, and it'll launch the FreeBSD/NetBSD installer. After that, just follow the standard installation instructions.

**Instructions for Linux**

3. If using an rpm-based Linux distro (Fedora, openSUSE), download the .rpm version, install it, reboot, and select the UNetbootin option upon rebooting. Same instructions for a deb-based distros (Ubuntu, Debian), only use the .deb version. If using a distro with no rpm or deb support (Gentoo, Slackware), download the .sh version, make it executable (_chmod +x ./file_), and run (as root; use _su_ or _sudo_): _./unetbootin-something.sh installmode=tohost_

**Alternative Instructions: If you have no host OS, but have a USB drive, and have access to Linux on another computer**

UNetbootin can also be used to create a bootable USB drive which will load the FreeBSD/NetBSD installer, from which you can boot on your other computer. If you have access to a Linux install, this should work (substitue usb drive partition for /dev/sdb1): _./unetbootin-something.sh installmode=nohost targetpartition=/dev/sdb1 formatpartition=yes bootloader=syslinux_ Alternatively, this command may also be used to use GRUB instead of syslinux: [i]./unetbootin-something.sh installmode=usbdrive targetpartition=/dev/sdb1 formatpartition=yes[/u]

**Alternative Instructions: If you have no host OS, but can boot a Linux LiveCD**

Similar to instructions above, only instead of specifying the USB drive device, specify the hard drive partition. For syslinux, use:  _./unetbootin-something.sh installmode=nohost targetpartition=/dev/sdb1 formatpartition=yes bootloader=syslinux_ or for GRUB, use:  _./unetbootin-something.sh installmode=nohost targetpartition=/dev/sdb1 formatpartition=yes bootloader=grub_ or for LILO, use:  _./unetbootin-something.sh installmode=nohost targetpartition=/dev/sdb1 formatpartition=yes bootloader=syslinux_

---

### Post by tuxcantfly on 2008-03-03
I've added builds supporting the newly released FreeBSD 7.0. They can be downloaded from [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=265552](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=265552)

---

