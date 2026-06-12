---
title: "Questions: Laptop &amp; Ubuntu"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Atari26003 on 2007-10-13
I own an Acer Aspire 5012WLMI laptop
Acer has already partitioned my drive and it is supposed to running a full copy of
Windows Media Centre 2005 ( which it is) 
But i want to dual boot it to Ubuntu. My worry is it will override data on either of the partitions, or i cannot use the acerDATA partition, i have attempted previously to contact acer and they were the most horrible people ive dealt with.:lolflag:
Anyways I would like to attempt a DUAL BOOT
I have an ACERDATA partition ( which is ment for me to save all my files to ) so I said well i want to put UBUNTU on that partition, Am I able to do this without messing it up? and also
When im installing ubuntu is it gona automatically select the C:/ or can i select the partition for it to install to?

Thank you very much!
Matt Zigman

---

### Post by dkruidhof on 2007-10-13
You should be able to dual boot by installing Ubuntu to the ACERDATA partition without too much of a problem. The install will not automatically choose where to install, so you can tell it to use that partition. However, it will need to reformat it to a different file format, so all data on that partition will be lost.

---

### Post by Pumalite on 2007-10-13
Use the Alternate CD. It gives you more control. You can direct it to the right partition better.

---

### Post by diatribe on 2007-10-13
if your acer is like mine there is actually a third hidden partition at the beginning that contains restore data.  as long as you dont change this partition you can edit the hdd to your hearts content

---

### Post by silkstone on 2007-10-13
As diatribe says, there is a third partition used by the Acer backup routine.

On my Acer 5612 I left the ACERDATA partition alone - it's already FAT32 so can be used by both Windows and Linux. I used the live CD and created the Ubuntu and Swap partitions within the original ACER partition. Everything worked fine except that I've always had a non-fatal error message on startup - just after selecting from Grub - saying that it is unable to allocate a particular memory resource. It carries on and loads anyway, and I've assumed that it may have something to do with the extra keys on the right hand side which Ubuntu cannot or does not use.

---

### Post by Tteddo on 2007-10-13
I have dual boot on both of my Acer laptops exactly how you describe and it works great (I have a 5100 and a 5050). On both Acer had 3 partitions, 1 was the recovery, 2 was a 60 gig Windows partition, and 3 was 60 gigs blank, which is where I installed Ubuntu. Everything works except the Orbicam, the winmodem, and the little card reader on the LH side all of which I don't care about.

---

### Post by Atari26003 on 2007-10-15
Ok im going to try this when i head home today!
thank you very much! :)
Im going to just put my music onto my C: instead of acerdata
:D

I dont use the modem seeing as i run a T1 
I dont' use orbicam much but I can figure a way to get either it to work or just get another USB webcam,

Thank you so much for your information guys!

---

