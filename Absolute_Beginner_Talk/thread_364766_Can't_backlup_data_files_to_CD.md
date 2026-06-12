---
title: "Can't backlup data files to CD"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Nigel Hewlett on 2007-02-18
I have installed Ubuntu 6.06 using the CD in the book Ubuntu Unleashed (Andrew Hudson and Paul Hudson) and upgraded to Firefox 2 and installed Thunderbird. I am now trying to back up my Mozilla-thunderbird email  fiolder to a CD-ROM.  I have tried Naurtilus and haven.t been able to drag anything or drop anything into the CD/DVD Creator.

Following Ubuntu Unleashed page 212, I tried "sudo cdrecord -scanbus" and got:

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-28-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

I looked in Synaptic Manager and found that the packages cdrao, cdrecord and cdrtools all seem to be installed.

As you will gather, I am new to this and computer-naive.  But I am really enjoying Ubuntu Linux so far and I would really appreciate any help anyone could give me with this.

Nigel Hewlett

---

### Post by pismo on 2007-02-18
Wecome to the forums
Use the package manager, Synaptic Manager and install K3b that will burn files for you after it is installed add it to your desktop or the bar right click on it and type gksu before the command K3b when you run it you will have to type in your password then you can burn your files

---

### Post by Nigel Hewlett on 2007-02-18
It worked!  That is just great.  Many thanks.
Nigel Hewlett

---

