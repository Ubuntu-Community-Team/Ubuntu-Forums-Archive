---
title: "Physical and logical config of HDDs for server"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Big_Rog on 2006-10-11
Well, it's official, I've taken the plunge into Linux!  A friend has let me tinker with an old Compaq Proliant 3000 (PII 450) server with the hopes of getting it running as a home file server/web server/teamspeak & vent server, etc.

I've managed to get both ubuntu server (in LAMP) and ubuntu desktop to load up without major issues, so I feel confident in moving ahead with a rearranging of the HDD config.  I am waiting for the SmartStart CD to download as we speak, but I was hoping to get some advice before I go mucking it all up on my own.  The drive cage has  seven 4.3G UW-SCSI drives, one of which is a 10K rpm.  The current setup has 5 of them in RAID 0 (5?) or JBOD, with the 10K and one regular drive inactive.  I've read over the article on LinuxPLanet about "Linux Partitions: A Primer" and have a good understanding of why it's important to partition drives for Linux.  I was thinking of making the 10K drive the boot partition, and then merging the other 6 into a RAID 5 array and then assigning partitions inside that logical drive.  Is that a decent idea, or is there another partition that would be better suited to the fast access of a 10K drive without the need for data protection from RAID 5, i.e. /var or /tmp?

On a hardware note, the server appears capable of running PIII 550 CPUs, and they are fairly cheap online.  Is it worthwhile to invest in uprading from the single PII 450 to a pair of PIII 550s?  It currently has 512MB of ram, but can hold a lot more than that.  If I could only afford to do the CPUs or RAM, which would be the better investment for such a low-end server?

Thanks in advance for your help!

---

### Post by Big_Rog on 2006-10-11
I'm glad I read that part about drive naming in that other article.  Seems that anything on a controler is labled "c", not "h" or "s", giving me a list of drives labled c0d0, c0d1, etc.

I've reconfigured the whole setup, and put the 6 7200 rpm drives into a RAID 5 array, and left the 10K rpm drive by itself. I broke the RAID 5 array into 4 4GB partitions and one 8+GB partition with the Compaq Array manager.  The compaq BIOS and utilities are set up on one of the partitions (wish I had known it was gonna do that beforehand) and is only using 40MB of space.  I set the rest of that partition as "swap" in the ubuntu setup.  I'm at the partitioning/mounting screen in the ubuntu setup, and I'm a bit baffled by the staggering ammount of unfamiliar choices.  I recognize FAT16, FAT32, swap, and a few others, but the rest are alien to me.  Before I go any further with the mouting of drive types, should I go back and just keep the RAID 5 array as a single partition since it's gonna be repartitioned when I set up ubuntu?

I'm still waiting for an answer about using separate partitions for the /var /tmp /home etc. directories before comitting to those, unless it's possible to adjust those after the OS is installed...

Thanks again in advance

---

