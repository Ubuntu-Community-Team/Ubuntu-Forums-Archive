---
title: "USB based drives (Hard and flash) won't mount???"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by JimmyI on 2008-01-16
Hi

I'm trying to get my usb zte mf622 3g modem to work with ubuntu. So far I have found the following script that stops ubuntu mounting the modems built in drive, with the windows drivers, so that the modem can be activated. But now any usb based drive won't mount, ie my WD ibook and my sandisk cruzer. Is there any way around this???

Script;


ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"

---

### Post by jeffus_il on 2008-01-16
> **JimmyI said:**
> Hi

I'm trying to get my usb zte mf622 3g modem to work with ubuntu. So far I have found the following script that stops ubuntu mounting the modems built in drive, with the windows drivers, so that the modem can be activated. But now any usb based drive won't mount, ie my WD ibook and my sandisk cruzer. Is there any way around this???

Script;


ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"
You are removing the kernel module which accesses usb   storage with the command:
rmmod usb_storage

if you want the storage to work again, you have to do:
modprobe usb_storage

---

### Post by JimmyI on 2008-01-20
Hi,

I type sudo modprobe usb_storage at the terminal, Nothing gets written after I press enter but my drive will now keep its light on as if it's connected, however, I still don't get the drive appearing? So how do I access the drive?

Jim

---

### Post by ozzy666 on 2008-03-03
Hi,

Firstly i need to thank all in this thread for helping me finally get my ZTE MF622 working on Ubuntu Gutsy.

What i would suggest Jim, as i have found, is that the modem needs to be unplugged and then replugged, in order to get access to the flash drive section.

Has anybody come across information relating to the issue, while the modem is in use, not being able to use other USB devices?

I would be very thankful to anyone who could point me along the right path.

Oz

---

### Post by nowhere@cox.net on 2008-03-12
Check out my other post and see if it helps. You may need your vendor and product code included when the usbserial driver is loaded.

[http://ubuntuforums.org/showthread.php?t=722618]("http://ubuntuforums.org/showthread.php?t=722618")

Eric

---

