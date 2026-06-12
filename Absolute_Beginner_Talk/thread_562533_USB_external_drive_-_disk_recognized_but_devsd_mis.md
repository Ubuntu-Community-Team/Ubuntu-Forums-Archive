---
title: "USB external drive - disk recognized but /dev/sd* missing?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by gubarro on 2007-09-28
Oops sorry for the chopped off post earlier... Pressed the wrong key :(

I'm using Ubuntu 7.04 on my rig, and I've got a FAT32-formatted USB external drive (80GB Seagate) I wish to copy some files from. 

When I plug the usb drive in, it doesn't automount. I tried to mount it manually, but there are no /dev/sd? device files. 
"sudo fdisk -l" doesn't show the device as well. 

However, in /var/log/messages, there are messages indicating that the device has been detected (it scrolls off a few lines about a USB high-speed device detected every now and then; goes off if I switch off the disk).

I've done a lsmod, and the necessary usb modules are loaded, except usb-storage. I did a "modprobe usb-storage" and then checked with lsmod again - this time usb-storage was listed, but I still can't find the /dev/sd? files. 

I can access the drive without issues on another rig running Windows XP, so I think it isn't a h/w problem. Any clues on what I need to install / check next would be appreciated! Thanks, and sorry for the faulty first post.

---

### Post by Pumalite on 2007-09-28
Hi fo???

---

### Post by gubarro on 2007-09-28
Sorry, edited my initial post. I messed up the first post and fired it off before I was ready. :(

---

### Post by Pumalite on 2007-09-28
Post:
lshw

---

### Post by conehead77 on 2007-09-29
with gparted you can see all your partitions. my external hd is /dev/sdc there.

---

### Post by gubarro on 2007-09-29
BTW, just double-checked that USB2.0 HDD support is enabled in BIOS.

I read somewhere about disabling the ehci_hcd module (modprobe -r ehci_hcd). I gave that a try, and it worked better, but still I couldn't see the /dev/sd? device files... Here's the output from lsusb and lshw, both with and without ehci_hcd module. 

lsmod | grep -i usb
> usb_storage            72256  0 
libusual               17936  1 usb_storage
usbhid                 26592  0 
hid                    27392  1 usbhid
scsi_mod              142348  3 sg,usb_storage,libata
usbcore               134280  6 usb_storage,libusual,usbhid,ehci_hcd,ohci

lsusb output with ehci_hcd module: 
> Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 031: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000 

lsusb output WITHOUT ehci_hcd module: 
> Bus 002 Device 003: ID 0402:5637 ALi Corp. M5637 IDE Controller
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 031: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000 

The lshw output are in the attached text files with the appropriate names below. You will notice that without the ehci_hcd module, lshw actually picks up the USB hard disk: NT68320 USB Storage (but still. no /dev/sd? though)....

Here's the output from dmesg WITHOUT ehci_hcd (since I seem to be getting further without this module...):
> [ 1842.411579] usb 1-3: new full speed USB device using ohci_hcd and address 87
[ 1842.595425] usb 1-3: device descriptor read/64, error -62
[ 1842.883185] usb 1-3: device descriptor read/64, error -62
[ 1843.162940] usb 1-3: new full speed USB device using ohci_hcd and address 88
[ 1843.570604] usb 1-3: device not accepting address 88, error -62
[ 1843.746467] usb 1-3: new full speed USB device using ohci_hcd and address 89
[ 1844.154134] usb 1-3: device not accepting address 89, error -62
[ 1844.154191] usb 2-1: USB disconnect, address 21

Thanks for any help/advice.

---

### Post by gubarro on 2007-09-29
> **conehead77 said:**
> with gparted you can see all your partitions. my external hd is /dev/sdc there.

Nope, just tried that. gparted won't see the disk as well.

---

