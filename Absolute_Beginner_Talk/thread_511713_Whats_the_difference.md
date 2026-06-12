---
title: "Whats the difference ?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by jnorthr on 2007-07-28
Is the ppa module the same as the ppdev module ? Both appear to be needed for correct parallel port options of iomega zip100 disk drives. Any ideas ?

---

### Post by DBStevens on 2007-07-28
IOMEGA Parallel Port ZIP drive SCSI support (ppa.o).

ppdev: user-space parallel port driver

The standard operation of a parallel port isn't SCSI so something has to sit between the ZIP drive and the standard parallel port system that something is ppa.

There are various device classes that are handled this way.   Frequently on the parallel port you will find scanners that act like they are SCSI devices.

---

