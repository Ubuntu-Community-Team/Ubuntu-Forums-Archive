---
title: "Advice on configuring with multiple hard drives"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by dancer on 2008-02-08
First off, I see lots of setups where people are multi-booting between Windows and various Linux's.  If you can virtualize, it seems to me a much better solution to have various virtual machines available.  Am I missing something here?

Assuming I am not, my thought is to do this.

The basic hardware in my box:  Asus M2N-SLI motherboard, Athlon64-5600 CPU, 2 GB RAM, 2 320 GB Barracuda SATA drives, also an external 500 GB USB hard drive.

I've tried using the Nvidia RAID built into the BIOS to stripe, span, mirror the 2 SATA drives, and found that in each case Ubuntu failed to install in a way that allowed me to boot.  Then I found a thread somewhere that indicated Ubuntu doesn't work with these BIOS controlled RAIDs.  So, I've now undone that.

But I think I do want the enhanced performance at least of mirroring.  I'm also interested in LVM, which sounds extremely useful.  And, I want to be able to run a variety of virtual machines, including at least Windows XP and maybe also Vista.

I also want to work with video.

Seems to me this should be possible.

If I'm wrong please let me know.  If not, how would you recommend I proceed to get this set up?

Thanks much in advance!

---

### Post by cuby on 2008-02-08
Hi,
I never used RAID in ubuntu, so I cannot help you there.
In respect to virtualization / bual boot, is more or less like this:

Dual boot provides better performance, so in some cases it cannot be avoided. Virtualization is very flexible, I use VirtualBox (open source edition) and i'm happy with it, but you must be aware that it doesn't have 3D acceleration (no games) and limited I/O (usb, rs232, etc).

---

### Post by dancer on 2008-02-09
> **cuby said:**
> Hi,
I never used RAID in ubuntu, so I cannot help you there.
In respect to virtualization / bual boot, is more or less like this:

Dual boot provides better performance, so in some cases it cannot be avoided. Virtualization is very flexible, I use VirtualBox (open source edition) and i'm happy with it, but you must be aware that it doesn't have 3D acceleration (no games) and limited I/O (usb, rs232, etc).
Thanks.

I understand dual boot gives better performance.  From what I've read mirroring increases performance very significantly.  So, I'd like to hear from someone with first hand experience with this and, if it's feasible, get a detailed walk through of how to set it all up.

---

### Post by badmedic on 2008-02-09
I was looking into doing this at one point with my system. There are lengthy instructions on how to accomplish this with an nvidia software raid on the Ubuntu Wiki here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The instructions were far too lengthy and intimidating for me so I ended up devoting a drive to Win and a drive to Ubuntu. :)

Hope this helps, and good luck!

---

### Post by bodhi.zazen on 2008-02-09
> **dancer said:**
> First off, I see lots of setups where people are multi-booting between Windows and various Linux's.  If you can virtualize, it seems to me a much better solution to have various virtual machines available.  Am I missing something here?

So long as you understand the limitations of the Virtualization platform ... 

> Assuming I am not, my thought is to do this.

The basic hardware in my box:  Asus M2N-SLI motherboard, Athlon64-5600 CPU, 2 GB RAM, 2 320 GB Barracuda SATA drives, also an external 500 GB USB hard drive.

I've tried using the Nvidia RAID built into the BIOS to stripe, span, mirror the 2 SATA drives, and found that in each case Ubuntu failed to install in a way that allowed me to boot.  Then I found a thread somewhere that indicated Ubuntu doesn't work with these BIOS controlled RAIDs.  So, I've now undone that.

But I think I do want the enhanced performance at least of mirroring.  I'm also interested in LVM, which sounds extremely useful.  And, I want to be able to run a variety of virtual machines, including at least Windows XP and maybe also Vista.

I also want to work with video.

Seems to me this should be possible.

If I'm wrong please let me know.  If not, how would you recommend I proceed to get this set up?

Thanks much in advance!

I suggest you break the task at hand into a logical set of steps. If you get stuck on a particular step, start a thread. In general, I suggest one topic / thread. With everything you are considering a single thread is likely to get quite long and as the length increases I doubt people will read the entire thread ....

---

### Post by Zack McCool on 2008-02-09
> **dancer said:**
> Thanks.

I understand dual boot gives better performance.  From what I've read mirroring increases performance very significantly.  So, I'd like to hear from someone with first hand experience with this and, if it's feasible, get a detailed walk through of how to set it all up.

Mirroring does not increase performance in any way, shape or form.  Mirroring simply keeps a second copy of the first disk.

Striping increases performance, but comes at a cost.  If you should have either disk fail, you lose everything on both.  It has no fault tolerance.

The only way Ubuntu will support the raid level you want is if there is a driver for the chipset (and it's raid functionality) for linux.  Perhaps, if you give your specific chipset info, someone may be able to help you.

---

### Post by Forrest Gumpp on 2008-02-09
dancer,

You may be able to get a performance boost short of that of full RAID striping if you are planning to use two (or more) physical HDDs in your computer when running Linux.

You could do a manual installation from the Alternate CD for Ubuntu, and place the Linux swap partition on a separate HDD to that upon which the root partition is installed.

For example, I have modified my old single HDD Dell Optiplex G X 240 such that it has two PATA HDDs mounted in caddies sitting on its lid and connected on the primary IDE channel and running at 133 ATA rating.  The OEM Win 2000 Pro resides on the 20 GB HDD that came with the computer, but I resized this to create a 1.5 GB Linux swap partition in previously unused space on the Windows drive.  This 20 GB HDD, jumpered as cable-select and connected with the master connector on the cable-select ribbon cable, is recognised by the BIOS as HD 0, and by Linux as sda (even though it is not a SATA drive).

My Ubuntu 7.10 is installed upon another HDD (80 GB) mounted in the other caddy in a root partition of 6 GB, this partition being the first logical partition in the extended partition I created immediately following the first primary partition on the disk.  During the manual Ubuntu installation I created a separate /home partition of 13.5 GB.  This /home partition is sdb1 and is a primary partition, and is used as a common /home partition with my installation of Xubuntu 7.04, which I had installed in like manner prior to Ubuntu 7.10.  It all seems to work, although there is not much in the /home partition yet, as the installations were all just done recently as experiments and for confidence-building practise.  /Xubuntu 7.04 is sdb5, and /Ubuntu 7.10 is sdb6.

The GRUB bootloader in each case I installed in accordance with the default installation option that is presented on the install screen to the Windows 2000 Pro master boot record.

The most recently installed *buntu as a consequence becomes the default OS in the GRUB menu.  I haven't got to editing the GRUB menu yet, but Herman's Illustrated Dual Boot Site contains probably most information needed when attempting this.  See:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  and have a good surf around.  (This site is linked to in ubuntu_demon's sticky thread.)

I have previously used this separated installation of the Linux swap partition under Fedora 4, and it seemed to me that my surfing of threads in another forum of interest to me was much quicker than when done under Fedora 5 simply installed to a single physical HDD.  I am not advanced enough to have analysed performance with any benchmarking tools, however.

As soon as I can get my hands on a cable-select ribbon cable with sufficient separation between the drive connectors to permit connection of a HDD mounted in the presently vacant single internal drive bay on the secondary IDE channel with the CD ROM drive, I intend to mount a third large capacity HDD (sdc) exclusively for backups and partition images.  This HDD would only run at 33 ATA rating, pegged back by the CD ROM drive which I have to keep internal, as the BIOS does not appear to support booting from a USB device.  I would commend putting the means of imaging partitions to a physically separate HDD in place right from the start in any migration to Ubuntu.  That way, if you make a mistake or something doesn't work well, you will have, in conjunction with the GParted Partimage LiveCD/Puppy Linux/Super Grub Disk CD described in Herman's Super GRUB Disk page at  [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)   a sort of hardware based cross-platform system restore capability.

BTW, the two caddies sitting on the lid of the Dell with their ribbon cable snaking in through the small gap where the lid closes are separately powered from an old AT power supply manually switched on before booting, so as to avoid overtaxing the internal Dell PSU.  I think this may be the cause of some odd messages at shutdown, but hey, Ubuntu Linux uses a journalling file system, so I just ignore them and switch off anyway and behold, the digital 'physician' appears to heal itself every time.  (Just in case anyone seeks to copy this layout with such ubiquitous second-hand hardware, I don't want to be the cause of their blowing their power supply unit.  You have been warned!)

Hope this is not all telling you how to suck eggs.  You seem a bit more advanced as a computer user than me.

---

