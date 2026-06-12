---
title: "RAID, I'm now baffled - hardware or software?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Guy7 on 2007-12-11
Hi, thanks to those of you who helped me here:
[[COLOR="Blue"]_Mount point recommendations please (multi drive PC)_[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=631600&highlight=guy7")
I'm now up and running.

I've even managed to configure my Ati9550 graphics card using documentation found here and abouts.

However, I chickened out from wiping the RAID array by basically accommodating everything else on the other two drives as I like the idea of the link.

I was pleased to see Ubuntu 7.10 mounted the RAIDed drives as the NTFS label (Data) and even more pleased to see I can read *and* write to NTFS partitions these days.

However I'd still like to Ext3 this partition so have been doing some reading and am now somewhat confused by the possible ways forward.

I *had* understood the RAID feature of the mainboard (Asus A7N8x-e) to be hardware RAID (Windows XP SP2 saw the raided drives as just one device in the disk management tool) but I now doubt this from the various Linux RAID documentation I've read.  Especially as when looking at /media I find both of the SATA drives as /media/sda1 and /media/sdb1.  Although changes on one are still reflected on the other - so there does seem to be mirroring going on.

This document describes the RAID hardware on my mainboard:
[[COLOR="Blue"]_http://www.linuxquestions.org/linux/answers/Hardware/Promise_FastTrack_PDC20378_PATA_or_RAID_[/COLOR]]("http://www.linuxquestions.org/linux/answers/Hardware/Promise_FastTrack_PDC20378_PATA_or_RAID")
and phrases such as:
"The "sata_proimse" driver does not understand the "hardware RAID" sets, created by the BIOS and accessed by the Windows RAID driver for the PDC20378. Of course you can use the Linux software RAID, treating the PDC20378 as a "normal" SATA controller."

1.  I'm assuming therefore I need to go the Linux Software RAID route?
2.  What I'm not clear on is whether I should delete the current RAID set (via the BIOS, which is where it was built)

3. But then I find the likes of:
[[COLOR="Blue"]_Raid 1 software or hardware?_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=624191")
and
[[COLOR="Blue"]_Software vs hardware raid 5 question_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=137911") - OK, I want RAID 1 but I presume the issues are the same.

OR, could I just split the array in the BIOS, format sda1 as Ext3 with a mount point of, say, /data, then copy the contents of sdb1 to sda1 and then rebuild the array in the BIOS?  Do I then "ignore" the fact that Linux still sees both devices in /media?

Sorry to harp on, but I feel a bit dizzy!

Cheers folks
Guy

---

