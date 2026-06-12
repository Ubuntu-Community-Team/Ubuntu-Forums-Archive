---
title: "Toshiba laptop won't boot up after format"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by bobpur on 2007-09-30
This is the third time I've tried to post this so here goes the short version.
After formatting the drive in a Toshiba Tecra S2, it stalls out with this message at the end of the BIOS run.

                         Yukon PXE v4.11.1.3 (20050614)
                          (c)Copyright 20003-2005 Marvell (R) All rights reserved.
                          
                          Pre-boot eXecution Environment v2.1
                          (c)Copyright 1997-2000 Intel Corporation
                          PXE-E61: Media test failure, check cable
                          PXE-M0F: Exiting PXE ROM
                          Invalid partition format_

I've never run into this before. It won't even boot the Gparted disk now nor anything else I try to boot from (Knoppix, Ubuntu, Win 2000 & XP). Nothing goes past this screen. 
I've seen nothing in the BIOS referencing this and I'm not one to poke around in there beyond what I know. No use making a bad problem worse.
Can anyone help me fix this? 
After formatting, it still has a 20 gb NTFS partition, a 1 gb SWAP partition and a 19 gb EXT3 partition. 

                                                Thanks.

---

### Post by Pumalite on 2007-09-30
DBan the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then use Gparted.

---

### Post by bobpur on 2007-10-01
Thanks for the response. 
DBan didn't do anything either. I can't get to the drive. My problem is that the screen  pops up at the end of the BIOS run and doesn't let me get past that point. 
If I had an OS installed (which I don't) the screen (or error message) pops up while still going thru the BIOS checks (before GRUB if an OS were installed) 
If I could get to the disk I would have no problem. I think what I have here is a " We support MS. If you removed it, you aren't putting anything else in place of it" type thing in the BIOS.
Maybe I missed something at the Dban site about its functionality. How did you think it would help or did you misunderstand?

                                                  Thanks again

---

### Post by molly_001 on 2007-10-01
Is it a 16-bit machine?

---

### Post by bobpur on 2007-10-01
Is it a 16-bit machine?

It had 32 bit Win XP on it as far as I know.

---

### Post by shae on 2007-10-01
Check the BIOS settings for a place to disable Pre-boot eXecution Environment.

---

