---
title: "[SOLVED] Scanner Problem"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-14
I am using:
Dell A920 Printer (aka Lexmark Z600) in Ubuntu Gutsy

I downloaded the Z600 driver and have succeeded in getting the printer to work ok.
When I use Xsane to scan images I am told that there are “no devices available”.
Is there something about frontends that I should know about to get the scanner part to work?
Thanks

Bern

---

### Post by ewr2san on 2007-12-14
What does:
the command "sane-find-scanner" show?
also what does "scanimage -L" show?


Try and see if it works with xsane running as root.

If it does you'll need to do a variation on the following:
1. Make sure that scanning users are added to group scanner

The next step is an example of what I added to get a Epson CX8400 to work.  Your file under /etc/sane.d might be different, and the line you add is definatley different.
2. Edit /etc/sane.d/epkowa.conf
add:
usb 0x04b8 0x0839

The purpose of #2 is to tell sane that this device is ok to let users in group scanner have access to it.

---

### Post by bern1939 on 2007-12-14
Thanks your reply:

**_Running sane-find-scanne_**r gives:

“ # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
found USB scanner (vendor=0x413c, product=0x5105, chip=rts8858c) at libusb:003:004
found USB scanner (vendor=0x050d, product=0x705c) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
  # Not checking for parallel port scanners.
  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

**_Running scanimage -L_** gives:

device `v4l:/dev/video0' is a Noname UVC Camera (046d:08cb) virtual device

**_Running Xsane as roo_**t gives:

 “Failed to open device `v4:/dev/video01; invalid argument”

Where to I wonder?

Thanks

Bern

---

### Post by ewr2san on 2007-12-16
Try installing the libsane-extras package..

---

### Post by bern1939 on 2007-12-17
Thanks ...  got it to work fine


Bern

---

