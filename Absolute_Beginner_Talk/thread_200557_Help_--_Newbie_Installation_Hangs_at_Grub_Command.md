---
title: "Help -- Newbie Installation Hangs at Grub Command"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by budaman on 2006-06-20
I'm trying to install ubuntu linux on a Celeron 500 MHz system with 384MB of RAM and a 20 Gb hard drive.  By the way, I removed the DOS partition on this machine (using FDISK) so the hard drive is unpartitioned.

I've burned images of both the desktop and server installation *.iso files, but when I boot from CD (using either CD)  I get the following screen:

GRUB Version 0.93 (639K lower/392128K upper memory)

[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.]

grub>


I thought that these images would go through a full install of Ubuntu linux, so what gives?  Do I need to go through some kind of command sequence via Grub to install linux?  Is my unpartitioned hard drive the problem?

I've browsed through the installation docs and searched on the forums, but can't find an answer to this dilemma.  (It's probably way too basic for all you linux gurus to even think about!)

Any help would be most appreciated.

---

### Post by aanderse on 2006-06-20
which version of ubuntu did you download and burn? 6.06 dapper drake or 5.10 breezy badger?  and if it is dapper drake ... did you download the desktop cd or the alternative cd?  if you could post the exact file name of the iso you downloaded it would be helpful.

---

### Post by richbarna on 2006-06-20
[QUOTE=budaman]By the way, I removed the DOS partition on this machine (using FDISK) so the hard drive is unpartitioned.
[/QUOTE]

I have been trying to find some info for you, and I found this :-

> You should not create or delete partitions for operating systems other than Linux with Linux fdisk or cfdisk. That is, don't create or delete MS-DOS partitions with this version of fdisk; use MS-DOS's version of FDISK instead. If you try to create MS-DOS partitions with Linux fdisk, chances are MS-DOS will not recognize the partition and not boot correctly.

Here :-
[http://www.tldp.org/HOWTO/Installation-HOWTO/details.html]("http://www.tldp.org/HOWTO/Installation-HOWTO/details.html")

Also, I remember trying to get Linux to work on an older system and had a similar problem. It would boot a windows cd but not from a linux cd.

---

### Post by Haegin on 2006-06-21
Sorry in advance if this seems obvious - to some people it won't be and maybe it will help them with a similar problem even if it doesn't help you.

1. Double and triple check you are definatly booting from CD in the BIOS.
2. Make sure the iso you downloaded is ok by generating an MD5 sum and comparing it with the md5sum file on the download server. (ask if you need more info on this)

---

### Post by drtvasudevan on 2006-06-21
[QUOTE=Human Prototype]Sorry in advance if this seems obvious - to some people it won't be and maybe it will help them with a similar problem even if it doesn't help you.

1. Double and triple check you are definatly booting from CD in the BIOS.
2. Make sure the iso you downloaded is ok by generating an MD5 sum and comparing it with the md5sum file on the download server. (ask if you need more info on this)[/QUOTE]

also try it on another pc.
this one appearas as though you have tried to install some linux os and now that grub is booting.

tv

---

