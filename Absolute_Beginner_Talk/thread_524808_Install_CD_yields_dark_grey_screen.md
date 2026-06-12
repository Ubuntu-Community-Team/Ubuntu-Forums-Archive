---
title: "Install CD yields dark grey screen"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Jon Saxton on 2007-08-13
Installation CD deosn't install.  Computer freezes on boot.

OK, I have tried to search for this problem, and I have also tried the normal and alternate CDs for 7.04 and they exhibit exactly the same problem.

The CDs themselves seem to be OK.  They both seem to work when I boot my laptop from them and each passed its internal consistency check.  So it has to be a computer issue.

The problem shows up on my "desktop" (actually a floor-standing tower model).  The installation CD yields an almost black blank screen and the computer is frozen to the point that Ctrl-Alt-Del does nothing and a hard reset is required.  The very dark grey screen appears immediately on boot.  No image or text is displayed, even briefly.  Only the Ubuntu distribution seems to have this problem.  I've tried Debian and Gentoo and they at least start the installation process.

The computer is an almost modern one that once upon a time was a server running Win2K.  The backplane is a Tyan Thunder 100.  It has twin P3s running at 600 MHz, 1 Gb of RAM, two SCSI hard drives (18 & 147 Gb) and a CD-ROM connected to an Adaptec 79xx controller.  The system boots from the smaller SCSI drive.  It also has a large IDE drive configured as a slave and an IDE DVD reader/writer as well as a (SCSI) magneto-optical drive  The video card is a 3DLabs Oxyten VX1 capable of driving my Dell LCD monitor at 1920x1200.  Of course it also does more standard resolutions such as 1024x768.

I eliminated the Dell monitor as a problem by hooking up an old high-res multisync CRT screen that happily does 1600x1200.

I'm a bit stuck.  I don't even know what question to ask except perhaps "Should I give up on Ubuntu?".

---

### Post by janipewter on 2007-08-13
Does this happen BEFORE of AFTER the machine boots from the install CD?

---

### Post by Jon Saxton on 2007-08-13
It happens as soon as the computer tries to boot from the CD.  The last thing which appears on the screen is the SCSI BIOS telling me that it has recognised a bootable CD in the drive.  Then the computer reaches for the CD and the screen goes a uniform not-quite-black colour.  Nothing else is displayed.

From observing the CD in the laptop, I knew that the alternate (text mode) install CD boots up in a graphics mode and that to get to text mode I have to press Esc and Enter.  That had no effect when the CD is in the tower.  By that time the machine is frozen.

---

### Post by digbyt on 2007-10-23
Identical syptoms here trying to boot the 6.06 LTS install CD on a DELL Precision 410. I am guessing it is a problem with the 3DLabs Oxygen, as that seems to be the thing we have in common that is not so normal in a DELL box.

For what it is worth, 7.10 gets further - but had problems with the SCSI device and seems to ignore the boot option required to work around it :(

---

### Post by alienexplorers on 2007-10-23
I get the grey box with Visual Effects turned on.  With it off everything works fine.

---

