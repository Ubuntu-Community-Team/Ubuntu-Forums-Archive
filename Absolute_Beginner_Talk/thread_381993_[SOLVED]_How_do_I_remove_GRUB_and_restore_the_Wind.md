---
title: "[SOLVED] How do I remove GRUB and restore the Windows bootloader?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2007-03-11
I have moved to another computer and have run the manufacturer's recovery CD on the previous one.  However, I notice that GRUB is still installed.  Even deleting the partition I though GRUB was on (the one with the boot flag, which was the Windows one) didn't make GRUB go away.  I eventually had to wipe off the recovery partition as well and do a full recovery completely from CD to ensure GRUB's demise.  I have no intention at the moment to remove Ubuntu from my current system for Windows, but in case I need to move again, how do I peel GRUB off of the MBR and put the chain-loaded Windows bootloader back in its place, as it appears that recovery CDs seem to use quick formats and not full ones?

---

### Post by sad_iq on 2007-03-11
If the answer is not there than I'l quit using linux :lolflag: 
[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

---

### Post by himikeb on 2008-04-13
sad_iq's link takes some digging, so I'll summarize here..  BTW - It worked like a charm for XPSP2.
First let me start by saying that the machine from which I am removing Ubuntu is not for me :)
I had installed it along-side XP-SP2  on a machine I thought I was getting, but the original owner wanted back.
Obtain a bootable Windows XP CD, and use it to boot.
I waited through all the Bill-messages until I got the first prompt.  Choose R to repair an existing installation.
It searched and prompted me for the Windows installation, showing me:
   1) C:\WINDOWS
I chose 1, and it asked for the Admin password.  Heh, I guess the previous owner never set one, so I just pressed Enter and got my
C:\WINDOWS>
Now, from the sad_iq link:
C:\WINDOWS> CD ..
C:\> FIXBOOT C:
C:\> FIXMBR
C:\> BOOTCFG /rebuild

After the BOOTCFG, it asked me if I wanted to add the Installation it found, and to be safe I answered "Y".
But the original boot.ini was intact, so that was actually not necessary - I had two entries in boot.ini after that, but that's an easy fix after you restart in the crashy-OS.

Good Luck!

---

### Post by rzlorayes on 2008-04-16
Hi. Like a number of others, I'm new to Ubuntu Linux. I read in the Microsoft site that fixmbr only works for X86 processors. Will fixmbr also work with Athlon 64 processors? I'm asking this isnce I want to restore Win XP in its small (40 GB) original drive while I get a larger HDD and reinstall Ubuntu to the larger drive. 

Thanks very much in advance.

---

### Post by muteXe on 2008-04-16
Isn't there an option on the supergrub disk to a similar thing?  I need to do this, but I haven't seen my xp disk in ages.

mute

---

### Post by Saint Angeles on 2008-04-16
yeah, super GRUBdisk has an option to "fix windows boot"

basically it does what you need.

---

### Post by rzlorayes on 2008-04-16
I'll try that with super grub disk. Thanks very much!

---

### Post by CSMatt on 2008-04-18
In the time I posted this I have since found out about the /fixmbr flag for Microsoft's FDISK utility.  I didn't know about the Super GRUB Disk though.

---

### Post by rzlorayes on 2008-04-19
Thanks very much to every:one! :)

---

