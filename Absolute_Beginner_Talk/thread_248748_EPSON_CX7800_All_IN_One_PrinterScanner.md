---
title: "EPSON CX7800 All IN One Printer/Scanner"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by gpw1 on 2006-09-01
I'm trying to install my Epson allinone printer and scanner. I have installed SANE Frontends and Backends and still dosen't work. I had installed Suse 10.1 with no problems both the scanner and the printer worked right out of the box. I need the scanner to complete my conversion from WinXP to Ubuntu Linux. 
Suse had a scanner setup as part of the System Administration menu like "printer" does where you can pick the scanner model and pick and choose the driver (in my case its a 'generic one') Ubuntu lacks that feature.
gpw1

---

### Post by jorn on 2006-09-01
Have you tried a search on google?
Something like: Name_of_your_printer ubuntu

---

### Post by awkward1234 on 2006-09-01
you could try 

[http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=435706](http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=435706)

good luck;)

---

### Post by gpw1 on 2006-09-01
Yes, I have and that's where the problem is. There is generic driver I don't know the name or who wrote it, for JUST the Scanner that I have, with no directions on how to load it. I have been pointed back to the "Backend and the Frontend and to something I know nothing about called a "HotPlug(?)" (this is do to the scanner being a USB, I guess) This is more greek then the wireless networks. YET Suse does it all by itself with no help from me. Sure is frustrating. SUSE also lets you pick a scanner and then load the driver even though I didn't need to, just like Ubuntu lets you pick a printer. This is my last step to solve, then I can turn off my WinXP box for good...

gpw1

---

### Post by wpshooter on 2006-09-01
I hope you are not going to try to hold your breath that long.

Looks like to me that Ubuntu is determined to solve every other problem first before they get printers/scanners working properly.

But good luck anyway.

---

### Post by Fedz on 2006-09-01
I thought the same as you ... as my HP printer worked but, my scanner wouldn't ... :roll: 

If you goto System > Admin > Synaptic Package Manager and highlight all > scroll down to Sane and Sane-utils > mark for install and apply.

Then goto Application > Graphics > Xsane Image Scanner.

Does that work?

---

### Post by gpw1 on 2006-09-01
Good Try... Glad it worked for you. Same message on this end "No Devices Found"  I will keep on looking on the Web got to be something.
Is your scanner a single one or part of an All-in-one? I have only ONE USB cable for both printer and scanner, I think it has something more to do with USB switching then drivers. Something called HOTPLUG? 

gpw1

---

### Post by gpw1 on 2006-09-01
> **awkward1234 said:**
> you could try 

[http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=435706](http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=435706)

good luck;)

That is where I'm really confused the above are Gutenberg(?) And I'm using CUPS.
I think...

---

### Post by monkotronic on 2006-10-27
got mine working by the following:

installed libsane AND libsane-extras AND sane-utils

please note you must have the universe and multiverse repositories enabled to get the extras package.

open a terminal and type sane-find-scanner

my results looked like this:

--------------------------------------------------------------------------
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x081f [USB2.0 MFP(Hi-Speed)]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-------------------------------------------------------------------------

the important information is the vendor and product numbers.  if yours are the same as mine, you can copy the following lines into a file and save it as /etc/sane.d/epkowa.conf

-------------------------------------------------------------------------
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-scsi(5) and sane-usb(5) for details.

# SCSI scanners can be configured simply by listing the path to the
# device.  For example, if your system claims to have a /dev/scanner
# SCSI device, all you have to do is uncomment the following line:
#
#/dev/scanner
#
# In the interest of maintainability, most installations would have
# /dev/scanner sym-linked to the real SCSI scanner device node.
#
# An alternative way that works for many operating systems and is a
# little bit more generic, is to have the backend probe for your SCSI
# scanner with the following configuration command:
#
scsi EPSON

# On systems with libusb, the following line is sufficient to get the
# backend to recognise your USB scanners.  It presumes, however, that
# the scanner---more precisely, it's USB product ID---is known to the
# backend.
# For all USB scanners that are officially supported by this backend,
# this presumption is true.  A list of such scanners can be found in
# sane-epkowa(5).
#
usb

# For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
# 
#   usb <USB vendor ID> <USB product ID>
#
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1) or, on Linux systems, peek
# at the information in /proc/bus/usb/devices.
# A sample configuration for the Perfection 1650 (GT-8200), which has
# a product ID of 0x0110, would look as follows:
#
usb 0x04b8 0x081f

# When not accessing your USB scanner via libusb, you may need to use
# one of the configuration commands below or commands that are almost
# the same.  These commands typically access the scanner via a kernel
# scanner module.
#
#usb /dev/usb/scanner0
#usb /dev/usbscanner0
#usb /dev/uscanner0
#
# Linux had a scanner module until version 2.6.2.  As of version 2.6.3
# libusb is your only option.  Linux' scanner module can be loaded via
# the modprobe(8) command like so:
#
#   modprobe scanner vendor=<USB vendor ID> product=<USB product ID>
#
# If the scanner module already knows the vendor and product IDs, you
# do not have to specify them.  If you want to have this done automa-
# tically every time you boot, you can add the above line, except for
# the modprobe command itself, to your /etc/modules file.

# Although not tested with this backend, parallel port scanners should
# be usable.  You can configure them as shown below, but I do not know
# much about the details.  Information is welcome.
#
#pio 0x278
#pio 0x378
#pio 0x3BC

--------------------------------------------------------------------------
when you have done this, try xsane again.  if you dont get what you want, try the following command to get permissions but replace the 004/002 with what followed the "libusb" word in your sane-find-scanner results:

 sudo chmod 0666 /proc/bus/usb/004/002

anyway, that worked for me.  good luck!

---

### Post by jrok on 2007-12-30
Thanks, monkotronic!

This worked the first time around in Feisty, but it required a reboot after my clean Gutsy install.  I'm guessing it might have worked had I had the All-in-One device powered on at startup the first time.

Anyway, thanks for the guidance!

---

### Post by Xavier Oddmon on 2008-06-28
I might add, while this alone did not fix the problem, I noticed that it added a group (saned). I put myself in the group, and this did the trick.

---

