---
title: "[SOLVED] Feisty CDROM: &amp;quot;unable to mount media. There is probably no media in drive&amp;quot;"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2008-03-09
Using up to date Feisty, I cannot access data CDs. (I haven't tried a music CD because my sound system is still not functional.) If I go to places > computer, and try to open "CD-ROM", the following message appears:

"unable to mount media. There is probably no media in drive"

I don't know if this is a recent problem or not; I've only recently tried to read a data CD for the first time, in connection with trying to get Wordperfect installed. (99.9% of the time all I'm doing is using Firefox to browse the web.)

I've searched the Ubuntu forums and Googled the web to try to find the answer but it seems like no one understands this problem and there's no definite fix for it. I've looked into fstab and followed all the other tips that have been offered and I'm still dead in the water!

The CD-ROM drive is a Samsung SC-148F, firmware FI18. (eff-eye-eighteen)

fstab has the following

/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

Properties for the CD-ROM at places > computer show a SCSI connection. I'm almost certain that this isn't right, that it's supposed to be an IDE drive. I'm using a clunky old second-hand IBM PC from about 2001 and it's unlikely to have a scsi cd-rom drive in it.

Clearly only a few Feisty users have this problem; otherwise the roof would be fallilng in. But none of the threads discussing it have that lovely "resolved" notation, at least not any that I can find.

Haven't tried tinkering with the BIOS.

**_Problem Resolution_**: smartboyathome hit the nail on the head. I installed a new CD drive (CD-RW, actually) and now it works. And here I was *so* sure it wasn't a hardware problem because Linux could display the manufacturer data. Not so. Stupid me.

---

### Post by smartboyathome on 2008-03-09
Sounds like your CD drive may either be broken or not recognised by Ubuntu. Have you tried a more recent version of Linux?

---

