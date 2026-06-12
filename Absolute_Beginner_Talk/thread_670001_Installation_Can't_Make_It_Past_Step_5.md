---
title: "Installation: Can't Make It Past Step 5?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Byakira on 2008-01-17
Hey guys.

I can't make it past step 5! I left it there and went to sleep, and woke up 6 hours later and it's still on step 5. Whats up with this?

I'm using Ubuntu Linux Feisty Fawn, and I was trying to dual boot with XP. I already installed XP.

---

### Post by spiderbatdad on 2008-01-17
could you post your computer specs?

---

### Post by Byakira on 2008-01-17
Sure

Intel Celeron 3.2GHz
1GB DDR2 RAM
Some shitty chipset for a Graphics Card

I cant remember the rest. I only got it yesterday xD

---

### Post by spiderbatdad on 2008-01-17
It would be a good idea to read the installation guide stickied in the forum of the same name. It is important to defrag windows prior to installing. Beyond that...some systems require special parameters to be set before linux will load. such as: noapic nolapic. You can goolge those and read about them if the problem persists. Have you been able to boot up the live cd and try ubuntu without affecting your system?

---

### Post by Byakira on 2008-01-17
> **spiderbatdad said:**
> It would be a good idea to read the installation guide stickied in the forum of the same name. It is important to defrag windows prior to installing. Beyond that...some systems require special parameters to be set before linux will load. such as: noapic nolapic. You can goolge those and read about them if the problem persists. Have you been able to boot up the live cd and try ubuntu without affecting your system?

Yeah, I'm using it now.

I have a 160GB Hard Drive. I split it into:

120GB = WIndows XP
40GB = Unpartitioned Space

My friend said that I'll be able to configure the 40GB into what I need. He also told me to split the 40GB into:

1GB = /Swap
50MB = /Boot
18.95GB = /

---

### Post by spiderbatdad on 2008-01-17
Hmm. I haven't tried that type of partitioning, I'm sure someone else here has...as you can run the live cd, I'd say your close...my gut says your swap is too small. Good Luck.

---

### Post by Byakira on 2008-01-17
> **spiderbatdad said:**
> Hmm. I haven't tried that type of partitioning, I'm sure someone else here has...as you can run the live cd, I'd say your close...**my gut says your swap is too small.** Good Luck.

BUt I havn't even made it yet. It's just unpartitioned space.

---

### Post by spiderbatdad on 2008-01-17
[http://ubuntuforums.org/showthread.php?t=668029&highlight=manual+partitioning](http://ubuntuforums.org/showthread.php?t=668029&highlight=manual+partitioning)

---

### Post by Byakira on 2008-01-17
Thanks for that link. I tried the Partition Editor in the System>Administrator thing, and I went on Refresh but it didn't see any devices. I'm gonna reformat the 40GB and see what happens

---

### Post by Byakira on 2008-01-17
Okay, I went on System > Admin > Disks, but there wasn't any discs there. It said there wasnt any known partitions on the disk.

Should I turn the 40GB into NTFS?

---

### Post by Byakira on 2008-01-17
[ATTACH]56684[/ATTACH]

Thats all I see

---

### Post by spiderbatdad on 2008-01-17
ntfs is your windows partition. you should format the disk you want linux on as ext3, like the instructions said.

---

### Post by stoodleysnow on 2008-01-17
You just need / as ext3, 38GB and swap as swap, 2GB. The boot part will sort itself out, as will /home, /etc...
You could even just tell it to automatically partition free space, rather than faff with manual formatting. Just a thunkt. (stoodleysnowspeak for 'thought':lolflag:)
:)

---

