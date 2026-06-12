---
title: "Canoscan 650U not scanning"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Eddy Dean on 2007-07-20
Hello everyone,

I recently installed ubuntu on this PC, and the USB scanner doesn't work. XSane finds it, but when I click the "make preview" button it times out. The scanner does nothing while timing out (no lights, nothing moving).

The scanner does get found by sane-find-scanners

```
gezin@links:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2206 [CanoScan], chip=LM9832/3) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
gezin@links:~$ scanimage -L
device `plustek:libusb:001:003' is a Canon N650U/N656U USB flatbed scanner

```

I have no clue what could be wrong, but it does work in Windows XP.

Thanks in advance,
Eddy

---

### Post by freesitebuilder on 2007-07-20
This is the hardware support page for Canon scanners
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)

It isn't listed - but that doesn't always mean that your scanner isn't supported, but that no-one has tried it, or reported that it does work. You could try the SANE project pages [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) to see if they list it.

---

### Post by Eddy Dean on 2007-07-20
My scanner appears to be needing the plustek driver, which is installed on Feisty Fawn by default.
According to SANE the support for my scanner is complete, so it should work properly.

Anyway, it doesn't, and I still have no clue why. XSane tells me the plustek driver is loaded, and it detects all hardware specifications of the scanner.

---

### Post by BirdZerk on 2007-07-20
I have the exact same scanner and I got it to work.  Read this entire thread and the solution is on reply #35

[http://ubuntuforums.org/showthread.php?t=414474&highlight=650U]("http://ubuntuforums.org/showthread.php?t=414474&highlight=650U")

---

### Post by Eddy Dean on 2007-07-22
installing scanbuttond worked, thank you!

---

