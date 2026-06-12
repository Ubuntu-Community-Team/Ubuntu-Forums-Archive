---
title: "Can Ubunty read files in Windows format?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by resander on 2007-07-16
Have Ubunty 7.04 on a dual-boot PC with Windows XP. The PC has a Conexant winmodem that is not supported by Ubuntu. It is possible to download a modem driver from linuxant, but of course I cannot do that from Ubuntu since the modem is not working. So, I was thinking of using Windows XP for the download and then copy the driver to a CD or to a normal file in a Windows XP directory.

Many years ago I had a dual-boot MSDOS and Unix PC. It was possible to read Unix files from MSDOS and vice versa. If I remember correctly I had to mount the MSDOS file system as a 'foreign' system in order to read MSDOS files from Unix.

Is it possible to do something similar on a dual boot Ubuntu and Windows XP PC? or are there other ways?

---

### Post by Tomshaq on 2007-07-16
Yes, you should be able to read from your existing partition/drive already in ubuntu. If you would like to edit/manipulate the drive you will need ntfs-config.

---

### Post by randytuggle on 2007-07-16
If you can only download a windows driver for the modem , you will have to install ndiswrapper in order to use the windows-based driver to get your Ubuntu to work the modem. This is probably a stupid tip you already know, but I thought I might add the note to help.

---

### Post by Nythain on 2007-07-16
ndiswrapper will be your friend... its a great package for installing windows drivers for things (primarily used for those pesky broadcom drivers)

you could head to [http://packages.ubuntu.com](http://packages.ubuntu.com)
to get teh package and all its dependencies since you dont have a net connection with your ubuntu install.

since you are dual booting you could also consider downloading the driver to either a fat32 partition, or to an ntfs partition and mount it correctily in fstab (ubuntu will default be able to read ntfs, but it cant write to ntfs without installing the ntfs-3g package wich you cant install since you have no net connection)

just set up your fstab to mount the ntfs partion (you can search these forums or google how to mount ntfs partitions with fstab) and install from there (if its a deb package driver you downloaded)

---

### Post by snkiz on 2007-07-16
I've seen the ndswrapper mentioned in a few posts to fix win driver issues. I have a dumb question can you use the wrapper for any win driver?? say like a webcam driver?

---

### Post by resander on 2007-07-17
I have googled on ndiswrapper and found that:

"With ndiswrapper, most miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network cards work in Linux with x86 or x86-64. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., ethernet cards, USB to serial port device, home phone network device etc."

so I don't think it would work for a webcam.

Will it work for a Conexant winmodem? A win modem is a complex piece of software that emulates what an expensive hardware modems does, so I doubt it will work with ndiswrapper, but I will ask the forum using post title 'Will NDISWrapper wrap native winmodem drivers?"

The modem driver I referred to is for linux and is available from linuxant.cm . It is free for speeds up to 14.4kbs. To get 56K speed you have to fork out $20.

---

### Post by splintercellguy on 2007-07-17
I think there are some winmodem drivers in Restricted Driver Manager and/or the Linmodems site.

---

### Post by wolfen69 on 2007-07-17
ubunty?

---

### Post by resander on 2007-07-17
Oops - the fingers control my brain.

Long live Ubyntu!

---

