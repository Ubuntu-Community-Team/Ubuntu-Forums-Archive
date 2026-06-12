---
title: "I want to switch with an unusual dual-boot setup"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by White_Wolfman on 2007-02-10
I've been using plain old vanilla Debian for about two weeks now, and I want to switch to Ubuntu since it seems to be more user-friendly and a bit more what I'm looking for. However, I'm a musician and a bit of an artist, and Debian and its children so often have issues with some of that that I want to set up my PC with a dual boot so I can boot Ubuntu for typical, everyday stuff and 64Studio for my music and other multimedia... stuff. :)

Can someone please explain how I can do this? Thanks.

---

### Post by pay on 2007-02-10
Just install Ubuntu normally and then edit your grub menu. [Here's ](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2) a good guide.

---

### Post by nickoli_02 on 2007-02-10
Well, hopefully when you install grub it will automatically see 64studio and add that in its boot menu. If it doesn't, you'll have to add it manually. Can't help ya there, sorry. This isn't a problem with linux, it's a problem with the boot loader :)

---

### Post by White_Wolfman on 2007-02-11
Thanks!

Now I have another problem. I wasted three CDs burning necessary ISOs for Partimage, Ubuntu, and 64Studio. (They burned the ISO as a file on the CDs instead of burning the image. :confused: )

I ran cdrecord -scanbus, and it finds the SD card drive in my printer, but it doesn't tell me what the location of my actual CD burning drive is. I tried the typical 0,0,0 location, and this is how it went:

[FONT="Courier New"]71-4:/home/wolfman7/Desktop# cdrecord dev=0,0,0 -v systemrescuecd-x86-0.3.2.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.1.25
cdrecord: No such file or directory. Cannot open '/dev/sg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
71-4:/home/wolfman7/Desktop#
[/FONT]

I feel like a total moron now, because when I switched from Windows to Debian, the ISO burning was quite simple. :-s

---

### Post by White_Wolfman on 2007-02-11
Wait, I just got it to work properly in k3b. Sorry! :lolflag:

---

