---
title: "Unable to scan with HP PSC 1210xi"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by twin_57103 on 2007-06-28
I've recently dual-booted my Win XP machine (Dell P4, 4.0 GHz, 1.5 Gb RAM) to Ubuntu 7.04 (default installation).  I am quite familiar with Windows but very new to Ubuntu and Linux. 

I use an 3-in-one printer/scanner/copier, model HP 1210xi.  Printing works well, but I've had little success with scanning.  When I attempt to open Xsane image scanner, I get the following error after a long delay (30 seconds or so)
 "Failure to open device 'hpaio:/usb/psc_1200_series?serial=CNN44FG20YMSH': Error during device IO."

I have tried troubleshooting based on this thread: 
[http://ubuntuforums.org/showthread.php?t=385893]("http://ubuntuforums.org/showthread.php?t=385893")

I have installed the HPLIP driver (version 2.7.6 downloaded from [http://hplip.sourceforge.net/]("http://hplip.sourceforge.net/")) and the sane-utils package.  I have also unplugged and replugged the USB cable.

Here is the output of sudo sane-find-scanner:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2f11 [psc 1200 series]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


The output from scanimage -L:
device `hpaio:/usb/psc_1200_series?serial=CN44FG20YM5H' is a Hewlett-Packard psc_1200_series all-in-one

If anyone has thoughts about how to proceed, I'd welcome them.  If necessary, I can use Windows for scanning (I have successfully enabled NTFS read/write support), but I'd like to get this working.  If there's an another scanning program that might work better, I'm  open to trying it.  Thanks in advance for your time.

---

### Post by linuxwizard on 2007-06-29
Look through the user notes might be something in them that could help you

[http://www.openprinting.org/show_printer.cgi?recnum=HP-PSC_1210](http://www.openprinting.org/show_printer.cgi?recnum=HP-PSC_1210)

---

