---
title: "SATA drivers for install???"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by neatokino on 2008-02-03
I just built my first computer from components using a  Gigabyte GA-EP35-DS3P motherboard and an e8400 Wolfdale 3Mhz processor.   It works when I run off the 64bit live CD.

When I try to install (Gutsy 64bit only, no Windows at all),  the installer partitions the drives ok, then during the install process I get the following error message: 

Failed to copy files; faulty CD/DVD or hard disk

[Errno 5] input/output error

(followed by lots of stuff about how my disc, disc drive, or hard drive might be faulty).

The DVD drive and HD are brand new;  I tried replacing them with drives from my old computer, which work fine, and I get the same error message.  I tried installing 32bit Gutsy and also get the same error message.

I notice on my motherboard's installation instructions that I need to install disk drivers when doing a Windows install.   I think my problem might have to do with disk drivers, but I don't know how to install them without going through a Windows installation (I don't even own a Windows install disk).   

I can't get the computer to boot off the 64bit alternate install disk.

Does anyone have any idea what's happening here? As I said, the 64bit live CD works quite well; is there something in the BIOS that I need to set in order to allow Ubuntu to be written to my hard drive?  Is there a driver or drivers that I need to load?
Any ideas????   Please don't tell me I have to go buy and install Windows, as the whole point of this build was to have a machine that only runs Linux!

TIA
Michael

---

### Post by wolfen69 on 2008-02-03
your alternate cd may be corrupted. did you check it for errors? and no, sata drivers are not needed for linux.

---

### Post by neatokino on 2008-02-03
I'm totally humiliated-- yes, it was a bad alt install disk.  I downloaded and burned another, and I'm up and running.

Thanks!!!

---

