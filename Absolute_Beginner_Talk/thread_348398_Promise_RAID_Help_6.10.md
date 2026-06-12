---
title: "Promise RAID Help 6.10"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-01-28
Hey all,

After a few issues with cd defects, ethernet not installing and graphics card drivers - I finally got Ubuntu running on the server at work using a IDE hard drive for OS. From what I have read about the Promise Fasttrak 4310 RAID card (RAID 5), for most people using 6.10 enables the card to work and view the drives in the RAID as one drive. Now using the device manager in ubuntu I can see the RAID card, and it has 4 SCSI Devices attached to it, and opening out each SCSI drive shows a generic scsi driver and the Western Digital Hard drive. (/dev/sda(b/c/d)).
Now when I go to "computer" I cannot see any of the drives? I tried to type /dev/sda into the address bar and it couldn't find it.

Do I have to setup DMraid or something? I downloaded DMraid, but the instructions that were given to install it did not work. 
I would rather use the onboard RAID controller, and i have it setup and everything(RAID 5 in the cards bios).

---

### Post by kuja on 2007-01-30
If it does involve dmraid, the resulting device would be found in /dev/mapper. Anything there?

---

