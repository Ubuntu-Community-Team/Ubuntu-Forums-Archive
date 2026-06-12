---
title: "Epson Stylus CX4800 Scanner"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Literatka on 2007-02-23
I'm running Drake and I have an Epson Stylus CX4800 that I can get to scan. I've tried XSANE and it doesn't detect my scanner (yes it is plugged in). I've tried uninstalling and reinstalling it but nothing happens. It just says that it can't find my scanning device when it works for printing through my printers.

Any ideas?

---

### Post by Bachstelze on 2007-02-23
Try to run *sane-find-scanner* in a terminal - with *sudo* if needed. Does it detect your scanner ? If "command not found", *apt-get install sane-utils*.

---

### Post by alienexplorers on 2007-02-23
You may need to load the libsane-extras, libsane, sane, sane-utils, xsane, and xsane-common to get your scanner working.  I own a microtek 4800 and needed all these files before mine started working.

---

### Post by Literatka on 2007-02-23
jessica@jessica-laptop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
jessica@jessica-laptop:~$ apt-get install sane-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jessica@jessica-laptop:~$ sudo apt-get install sane-utils
Password:
Reading package lists... Done
Building dependency tree... Done
sane-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jessica@jessica-laptop:~$
=



--- Still can't access it.

---

### Post by Bachstelze on 2007-02-24
what if you run *sudo sane-find-scanner* ?

---

### Post by Literatka on 2007-02-25
> **HymnToLife said:**
> what if you run *sudo sane-find-scanner* ?

jessica@jessica-laptop:~$ sudo sane-find-scanner
Password:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0819 [USB2.0 MFP(Hi-Speed)]) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


So it found my scanner but... I can't figure how how to get to scanimage -L to read the backend's manpage. Whatever that means.

libsane-extras, libsane, sane, sane-utils, xsane, and xsane-common  are all installed.

---

