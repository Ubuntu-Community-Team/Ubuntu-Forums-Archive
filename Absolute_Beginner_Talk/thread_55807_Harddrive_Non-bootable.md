---
title: "Harddrive Non-bootable? :\"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by jak-_- on 2005-08-10
I'm new to the whole linux stuff, (obviously) and stumbled upon a major problem last time I used it.


Heres the background: I had a 120GB NTFS Windows partition, and installed Linux (and grub) on an 80GB clean harddrive. For my needs, I needed to have both Windows and Linux on the 80GB, with the 120GB becoming a shared FAT32 partition.

I formatted the 80GB into 40GB WinXP (NTFS), and left the rest unpartitioned for when I came to install linux. So anyway, I became lazy and was just using windows, hadn't even bothered turning the 120 into FAT32... Anyway, I needed to boot onto my 120GB, but GRUB didnt seem to let me. It just flashed up 'Error: 17' (I think it was 17).  Note, this was only after I formatted the 80GB and hence removed Ubuntu from it. Googling/searching hasnt actually told me what would fix said error.

I left that behind now, since I could still read the drive I backed up all the data and just formatted to use elsewhere. Thing is, I now have one 250GB SATA harddrive, with 40GB WinXP, 170GB Data, 40GB unpartitioned for linux. Thing is, if I install grub while installing linux, then I have to format the linux partition for any reason and Grub starts doing the same error, how will I fix it... It's important that I can boot from this drive.



Also, it will work ok like the said setup right? IE, All on one drive like this...?



Cheers,
 - jak.

---

### Post by tonysathre on 2005-08-10
[QUOTE=jak-_-]I'm new to the whole linux stuff, (obviously) and stumbled upon a major problem last time I used it.


Heres the background: I had a 120GB NTFS Windows partition, and installed Linux (and grub) on an 80GB clean harddrive. For my needs, I needed to have both Windows and Linux on the 80GB, with the 120GB becoming a shared FAT32 partition.

I formatted the 80GB into 40GB WinXP (NTFS), and left the rest unpartitioned for when I came to install linux. So anyway, I became lazy and was just using windows, hadn't even bothered turning the 120 into FAT32... Anyway, I needed to boot onto my 120GB, but GRUB didnt seem to let me. It just flashed up 'Error: 17' (I think it was 17).  Note, this was only after I formatted the 80GB and hence removed Ubuntu from it. Googling/searching hasnt actually told me what would fix said error.

I left that behind now, since I could still read the drive I backed up all the data and just formatted to use elsewhere. Thing is, I now have one 250GB SATA harddrive, with 40GB WinXP, 170GB Data, 40GB unpartitioned for linux. Thing is, if I install grub while installing linux, then I have to format the linux partition for any reason and Grub starts doing the same error, how will I fix it... It's important that I can boot from this drive.



Also, it will work ok like the said setup right? IE, All on one drive like this...?



Cheers,
 - jak.[/QUOTE]
 where did u install the bootloader

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=jak-_-]I'm new to the whole linux stuff, (obviously) and stumbled upon a major problem last time I used it.


Heres the background: I had a 120GB NTFS Windows partition, and installed Linux (and grub) on an 80GB clean harddrive. For my needs, I needed to have both Windows and Linux on the 80GB, with the 120GB becoming a shared FAT32 partition.

I formatted the 80GB into 40GB WinXP (NTFS), and left the rest unpartitioned for when I came to install linux. So anyway, I became lazy and was just using windows, hadn't even bothered turning the 120 into FAT32... Anyway, I needed to boot onto my 120GB, but GRUB didnt seem to let me. It just flashed up 'Error: 17' (I think it was 17).  Note, this was only after I formatted the 80GB and hence removed Ubuntu from it. Googling/searching hasnt actually told me what would fix said error.

I left that behind now, since I could still read the drive I backed up all the data and just formatted to use elsewhere. Thing is, I now have one 250GB SATA harddrive, with 40GB WinXP, 170GB Data, 40GB unpartitioned for linux. Thing is, if I install grub while installing linux, then I have to format the linux partition for any reason and Grub starts doing the same error, how will I fix it... It's important that I can boot from this drive.
[/QUOTE]

I had a problem similar to that. My ways usually aren't what people like to hear, but a solution is a solution.

So I had problems getting Ubuntu to install the grub on my serial ATA drive what a pain. So what I did was get a cheap, normal IDE 20 gig drive (any computer parts place has them for cheap....even a 1 gig one would work for this purpose) installed it as the Master IDE device on the primary channel, and told Ubuntu to isntall grub to that! Worked like a charm ever since. I ended up putting Windows on that drive so my wonderful Ubuntu didn't have to share space with it.

Soo....a cheap IDE drive could save you a lot of trouble. I just looked on ebay and one could be had for less than ten bucks. Linux (nor Windows if you don't want) won't run on there so if won't sacrifice any performance. Its a good solution I think...

---

### Post by jak-_- on 2005-08-15
[QUOTE=poofyhairguy]I had a problem similar to that. My ways usually aren't what people like to hear, but a solution is a solution.

So I had problems getting Ubuntu to install the grub on my serial ATA drive what a pain. So what I did was get a cheap, normal IDE 20 gig drive (any computer parts place has them for cheap....even a 1 gig one would work for this purpose) installed it as the Master IDE device on the primary channel, and told Ubuntu to isntall grub to that! Worked like a charm ever since. I ended up putting Windows on that drive so my wonderful Ubuntu didn't have to share space with it.

Soo....a cheap IDE drive could save you a lot of trouble. I just looked on ebay and one could be had for less than ten bucks. Linux (nor Windows if you don't want) won't run on there so if won't sacrifice any performance. Its a good solution I think...[/QUOTE]


Thanks for the tip, (and sorry for the late reply :)). I will have to remember that, but for now that isn't plausible... I'm talking about 'fixing' the boot watcha-ma-call-it (oo technical terms) when GRUB has been on there but Ubuntu removed...

I remember a some System Tools program in the Wiki, and mentioned on the forum... Does this have such a feature (ie, Remove GRUB and load into windows?)

---

