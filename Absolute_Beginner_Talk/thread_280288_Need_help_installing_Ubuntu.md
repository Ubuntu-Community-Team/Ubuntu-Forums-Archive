---
title: "Need help installing Ubuntu"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Skidmark on 2006-10-19
Hello world!

I just recently decided to dump my windows in favor of linux, and found my way to Ubuntu which i've gotten quite happy with.

I've installed it on two older PC's without any problem what-so-ever. But on my 'new' PC it's a bit of a fiddle.

I keep getting a message saying:

"hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)"

So i've searched high and low for a solution, but no-one seems to know exactly what's wrong and i just can't seem to find an answer. The closest i've come, is that there's some sort of a problem with ATAPI DVD drives in the newer versions?

Does anyone know of this problem? Is there an easy solution? Or just an explanation of what causes it, and what i can try to figure out what's wrong, would be appretiated.

A bit info about my system:

P4 Northwood 3.06 Ghz
1 GB Ram
Asus P4P800 E-Deluxe
Plextor DVD drive
ATI Radeon 9800 Pro
Western Digital Raptor (76 GB)
Very shiny!

I'm not as dumb with computers as i might sound, so don't be afraid to post long-winded solutions ;)

Thanks in advance

---

### Post by darrenm on 2006-10-19
Is your HDD SATA or SCSI? Just wondering why you have your DVD drive as a primary master?

Never seen this problem or heard of it before so just taking wild guesses but I would look at firmware issues with the DVD drive e.g have you flashed it a non-std firmware? Do you have your 80-conductor IDE cable with the master on the middle connector? Can you try defaulting your BIOS, clearing the CMOS etc. Turn DMA off on the drive through the BIOS, try it a secondary master and change the SATA BIOS config to using the SATA drives as IDE drives. That kind of thing?

---

### Post by Skidmark on 2006-10-19
The HDD runs on SATA. And i haven't touched the firmware for the drive and .. eh.  uh.. pass. I'll have to try those things asap, thanks for the quick reply mate :)

---

### Post by xp_newbie on 2006-11-20
You may want to read the following threads (or at least a few last messages in each) - they contain the solution for your problem:

[ What does Linux have against ASUS (or vice versa)?]("http://www.linuxquestions.org/questions/showthread.php?t=499811")

[Is it possible at all to install Ubuntu on an ASUS P4P800-E Deluxe?]("http://www.ubuntuforums.org/showthread.php?t=289523&page=2")

HTH,
Alex

---

