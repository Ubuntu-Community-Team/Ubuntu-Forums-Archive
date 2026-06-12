---
title: "Scanner &quot;light-off&quot; command?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-11-13
I know in Windows there was a little app I could run which would turn off the light on my scanner (HP ScanJet 4200c).  Since I've gone all Ubuntu, I have rarely used my scanner, but when I have I noticed the light never goes out.  So....does any have a little app that will do that, or perhaps the USB commands the scanner recognizes and I'll write my own with libusb?

Thanks in advance!:)

---

### Post by PointyWombat on 2007-11-13
You may want to read the scanimage(1) man page, specifically for the -n option which can be used to turn off the lamp.

PointyWombat

---

### Post by anewguy on 2007-11-13
Thanks - I'll give that a try later!:)

---

### Post by anewguy on 2007-12-25
Well, it's taken me long enough to get back here, but I tried scanimage -n  - it reported no errors,etc. but it didn't turn the scanner light off.  Any ideas?:)

---

