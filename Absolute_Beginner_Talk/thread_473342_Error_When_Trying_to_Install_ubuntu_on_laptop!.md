---
title: "Error When Trying to Install ubuntu on laptop!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by moktoman on 2007-06-13
I have a DELL Latitude CP 233XT.
It beyond obsolete, I know.
But I was told I could get a Linux distribution to run on it okay.

I downloaded and burned an iso of ubuntu 7.04 and tried to boot the CD and install within laptop.
I click the install option without adding any parameters and after dsplaying the load screen for awhile it
gives errors like:

[    146.004000] Buffer I/0 error on device fd0, logical block 0
[    390.928000] hdc: error code: 0x70  sense_key:  0x05  asc:  0x64   ascq:   0x00

etc, etc.

I though the issue was related to the hard drive not being formatted correctly, so I ran a Knoppix dist. and formatted the hard drive as FAT32. But still got the same errors after that.

I tried the xubuntu distr. also, but with the same results.

Any idea what is going on, and how I can resolve this?

---

### Post by Trueno22 on 2007-06-13
seems like a floppy error does the lap top have a floppy drive if not go into the bios and make sure its not set to have a floppy when it doesn't

---

### Post by moktoman on 2007-06-25
Well, yes, there is a floppy disk drive, but it is swappable for the CDROM drive, which I am using when trying to install ubuntu.

I checked the BIOS, and the floppy is disabled (as well as non-existent, since it is not plugged in), and the boot order is CD-ROM first, then hard disk drive.
?

---

### Post by moktoman on 2007-06-28
I think the problem is actually with the ubuntu installation CD or the CDROM drive.
The errors I am getting are from trying to read the CD's contents.
But I don't understand why every version of ubuntu and other linux distros I tried to install are all giving me CD read errors...
(even after the initial startup screen appears, and I make the choice to install on my hard drive...)

Any thoughts?
Because I REALLY want to try out Ubuntu!

---

