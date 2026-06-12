---
title: "Flatbed scans poor on a PPC, good on an i686 (Xsane, Epson 1260)"
date: 2010-06-08
forum: Apple Hardware Users
---

### Post by heliboy on 2010-06-08
Under Ubunutu 9.10 on a PPC G4, an Epson Perfection 1260 flatbed scanner running via Xsane produces a scan that is of the correct size and orientation but that has a dark, green, uneven hue and many black longitudinal lines.  No amount of fiddling with Xsane image manipulation parameters produces a usable color, grayscale, or line image.  The same scanner, when plugged into an i686 box (AMD Duron, also Ubuntu 9.10 and Xsane) produces nice scans "out of the box".  I have never attempted before today to run Xsane on either of these boxes.  Why does this scanner not work on a PPC, but works fine on an i686?

Plustek.conf is identical on the two machines.  Scanimage -L correctly identifies the scanner on both machines (e.g., "device `plustek:libusb:001:005' is a Epson Perfection 1260/Photo flatbed scanner").  kernel 2.6.31-22 on both machines (-generic and -powerpcc).  Xsane 0.996-2 and sane 1.0.20 on both machines.

---

