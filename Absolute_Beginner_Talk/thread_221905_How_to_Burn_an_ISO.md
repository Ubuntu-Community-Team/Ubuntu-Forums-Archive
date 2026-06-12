---
title: "How to Burn an ISO"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-07-24
I need help burning an iso.  I have gnomebaker installed.  When it is finished it says this:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: Device or resource busy. Cannot open '/dev/hdb'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .




Any Help?

---

### Post by richbarna on 2006-07-24
> **cac007 said:**
> I need help burning an iso.  I have gnomebaker installed.  When it is finished it says this:
Any Help?

I got a similar message while trying to use mono to do system backup.

I went to the terminal and entered "su" to switch to "root" and the problem went away.

You could also try (from terminal) gksudo gnomebaker.

Also try right clicking on the iso and selecting open with "other application"

---

### Post by cac007 on 2006-07-24
Now it says:


cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/cdrw'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by richbarna on 2006-07-24
Did you try everything I said in post #2 ?

---

### Post by wpshooter on 2006-07-24
My suggestion would be to switch to the **K3b** CD burning application.  I could never get the GnomeBaker program to work correctly.

You should find the K3b program in the Add/Remove programs menu.

Good luck.

---

### Post by richbarna on 2006-07-24
> **wpshooter said:**
> My suggestion would be to switch to the **K3b** CD burning application.  I could never get the GnomeBaker program to work correctly.

You should find the K3b program in the Add/Remove programs menu.

Good luck.

Good Advice, I use k3b as well.

---

### Post by cac007 on 2006-07-24
thanks for the advice guys. what i was trying to do was burn an iso of dapper, but i gave up.  Instead i'm installing it from update manager.  I wasn't aware i could do this beforehand.

---

