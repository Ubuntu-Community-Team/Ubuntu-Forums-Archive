---
title: "I/O error when transferring files to external USB drive"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by jimbo111 on 2007-02-11
Hello everyone,

 I discovered this problem just today after having installed Ubuntu Edgy Eft 6.10 a few weeks ago.
My kernel version is 2.6.17-11-generic
I tried transferring about 1 GB of files to my external USB hard drive and I get an I/O error after transferring the first few files. The OS just hangs for a while and if patient enough, comes up with the I/O error while copying a file accross to the USB hard drive. My hardware is just fine as is the integrity of the files themselves. The proposed solution from another forum was to install a 2.4.x kernel which I find quite silly since a 2.6.x kernel should be far better than an earlier kernel. Is anything being done about this or is there anyone who knows the answer?
Any help is appreciated.

Many thanks

---

### Post by hawksbill on 2007-02-11
How large are the files that you are transfering?

What file system is the file system?

I wonder if it's a PCI latency issue? (curious how many PCI devices you have installed)

Have you tried extracting the data with another computer with same kernel?

Also are you checking md5sums?

Sorry for all the questions but these are things that instantly popped into my mind after I read your post. And yes that sounds like a rather strange work around to "downgrade" your kernel (which would most likely cause many other issues).

---

### Post by jimbo111 on 2007-02-11
Thanks for your reply....

The size of each folder is about 75MB, with 10 folders in all and the average size of each file in each folder is 16MB. 
Basically, I'm trying to transfer MP3's from my laptop to my external hardrive. The laptop filesystem is ext2 and the external hardrive is fat32. 
The data transfers fine when using Fedora 6 and of course Windows XP. I don't have another computer to install Ubuntu and try the transfer as I highly doubt it's my laptop (unless HP nc6000 laptops have serious hardware issues which I've never noticed and highly doubt). 

PCI devices on my laptop are as follows: 

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
 
As for checking md5sums, no, I don't think I need to as the file integrity is just fine (I've listened to all the songs without any problems), I'm just trying to do a trivial file transfer from my laptop to my external hardrive.  If I need to check md5sums, then I think I need to install a different flavour of linux as that would be a bit absurd. 

All in all, this is pretty standard stuff. In another forum, it's been 'realized' that this is a known bug since early last year but I'm wondering if anyone has come across this and found a workaround whilst the people at Ubuntu work on this? What was said was the 2.4.x kernel doesn't have a problem with this but the 2.6.x kernel does.....

Thanks very much

---

### Post by jimbo111 on 2007-02-12
Hello hawksbill.....

Yes, indeed, checking the files with md5sums was necessary. 3 of the files were corrupt, causing the entire transfer to abort. Many thanks for your help on this.....

Cheers

---

