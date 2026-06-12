---
title: "Spankin' New &amp; DOA!"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Bert_NEPA on 2007-12-29
I have an old Gateway Pentium II system that used to run WinNT4.0 and thought it would make a dandy platform for me to learn Ubuntu.
     The old Win OS got corrupted, stopped working and wouldn't even reboot; I gave up trying to recover the NT software configuration and let the hardware collect dust.  The original WinNT CD and setup floppies were of no use because the motehrboard firmware doesn't recognize the Floppy Drive and trys to only boot from the CD Drive.
     Yesterday, I downloaded and built the Ubuntu alternate CD software on my existing WinXP desktop, loaded it into my old Gateway today and tried to boot up (via the CD).  It didn't work.
     Is it possible to create a bootable Linux  CD, format my hard drive and load Ubuntu?
     Any advice is greatly appreciated.

---

### Post by PmDematagoda on 2007-12-29
What error did you get when you tried to boot the laptop using the Alternate CD?

---

### Post by Tyke91 on 2007-12-29
it should be able to, make sure you burn the alternate CD at the slowest speed possible (x4 if you can). 

watch these video clips on how to download, burn, and install Ubuntu. They worked for me on the first try.
[http://ubuntuclips.org/collections/3](http://ubuntuclips.org/collections/3)

---

### Post by p_quarles on 2007-12-29
My hunch is that this PII just doesn't have enough RAM to deal with a relatively heavy Linux distro like Ubuntu. How much does it have?

---

### Post by cmnorton on 2007-12-29
How much memory is in this old system? You might want xubuntu if your memory is below 512.

---

### Post by eternicode on 2007-12-29
The Ubuntu LiveCD didn't boot?  Did you check the checksums before burning it?

Sounds like you want to use GParted to re-partition you drive.  A couple CDs that can do this are [SysRescCD]("http://www.sysresccd.org/") and [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/").

Once you have GParted up, simply delete all partitions (UNLESS you want to try to save the Windows OS) and create a new linux partition (default is ext3).  To set it up for a new install beforehand, also create a small swap partition.

Edit: Oh, alternate CD.... :D
Still strange that it wouldn't even boot, though

---

### Post by Tyke91 on 2007-12-29
or even fluxbuntu 

EDIT: don't use the live CD, it sounds like your system just wont be able to handle it. Go for the xubuntu or fluxbuntu alternate cds

---

### Post by eternicode on 2007-12-29
> **Tyke91 said:**
> don't use the live CD, it sounds like your system just wont be able to handle it. Go for the xubuntu or fluxbuntu alternate cds

The Ubuntu LiveCD maybe, but I have a 129MB system (yes, 129...dunno why, maybe 128MiB?) which runs the SysRescCD just fine.  There are some issues with the desktop resolution after startx, but all the progs run fine.

---

### Post by Bert_NEPA on 2007-12-29
I used the 4X speed and checksum works OK; I'll try the xubuntu or fluxbuntu alternate CD method.

---

### Post by Bert_NEPA on 2007-12-29
I got no error message; the monitor remains a blank screen.  FYI: a few days ago I used the monitor, keyboard and mouse from my Gateway to work with my nephew's desktop; I'm confident the hardware is OK.

---

### Post by Bert_NEPA on 2007-12-29
I believe it has 512MB; I'm planning to try the xubuntu or fluxbuntu alternate CDs.

---

### Post by eternicode on 2007-12-29
> **Bert_NEPA said:**
> I got no error message; the monitor remains a blank screen.  FYI: a few days ago I used the monitor, keyboard and mouse from my Gateway to work with my nephew's desktop; I'm confident the hardware is OK.

Hm...do you get a BIOS POST screen (usually the vendor's logo before the boot sequence)?  Also, are you sure the BIOS boot settings allow it to boot from CD before HDD?  If this is a notebook system, you might also check to be sure the CD drive is firmly installed.

Let us know how the Xubuntu or fluxbuntu try goes.

Also, according to [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) , your system should be fine to run Ubuntu (Feisty anyway)

---

### Post by Bert_NEPA on 2007-12-29
I'm not even getting any BIOS display on my screen. I'm beginning to wonder if my motherboard is DOA!

---

### Post by Bert_NEPA on 2007-12-29
Thanks foer the suggestions.

---

### Post by eternicode on 2007-12-29
That could be.

Are you sure it's powering up? (Gotta check the basics ;) )  If it is, try tapping the Delete, F12, F2, or F10 keys (most common keys for getting into BIOS setup) and see if anything happens.  If nothing happens after about 5-10 seconds, the motherboard could be dead.

At this point I'm not quite sure how much more help this forum can offer :) unless the BIOS pops up.

---

### Post by tgalati4 on 2007-12-29
Check the voltage of the on-board battery.  It should be 3.3V in most cases.  A dead motherboard battery can cause problems.  Try shorting the BIOS jumper pins to clear the current BIOS and reload it from the eeprom.  Even better, search the interweb and find a BIOS update and reflash it.

---

