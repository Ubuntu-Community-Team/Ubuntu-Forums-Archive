---
title: "sane (probably) detected my scanner ?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-08
Probably. Whats that supposed to mean did it or did it not?

found USB scanner (vendor=0x043d [Lexmark], product=0x0093 [Lexmark 5200 Series]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

tried to run as root. Same thing happend.Tried the scanimage -L   no luck can any one help with this? Thanks, Whats the backends man page?

---

### Post by linuxwizard on 2007-07-08
no not a supported scanner 

[http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK](http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK)

---

### Post by Sef on 2007-07-08
If you have a Lexmark 5200, it is unsupported.   Check the [Sane-Project]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Lexmark&model=&bus=any&v=&p=").

Note:  Lexmark products often do not work with Linux because it chooses to keep its hardware and software proprietary.

---

### Post by swoll1980 on 2007-07-08
5200 yep thats me guess i'll throw it in the garbage LOL

---

