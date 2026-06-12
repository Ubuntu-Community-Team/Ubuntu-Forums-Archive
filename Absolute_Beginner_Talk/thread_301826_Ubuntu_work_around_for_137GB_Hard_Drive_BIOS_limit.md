---
title: "Ubuntu work around for 137GB Hard Drive BIOS limitation"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by snik on 2006-11-17
I installed Ubuntu 6.10 on a new and empty Hard Drive, using the Live CD. After installation Ubuntu failed to boot up when I restarted my computer. 

I got the following error: Grub Loading Error 18

I googled and found out that Error 18 occurs when the BIOS cannot handle Hard Drives larger than 137GB. My Hard Drive is 250GB. My BIOS is a Dell-4100 Version A06. I checked the BIOS and sure enough it showed incorrectly that my drive was only 137GB. 

Apparently Windows XP, can overcome this BIOS limitation. Is there a way I can get Ubuntu do the same? 

I did try reinstalling Ubuntu again, except in my second attempt I limited the size &#8220;/dev/hda1&#8221; to 127GB. gparted showed that the rest of the drive 123GB (250GB &#8211; 127GB) would remain &#8220;unused&#8221;. And the installation was successful. 

I want to eventually use the &#8220;unused&#8221; portion and create an another drive. Will it work? I mean is there some reason that the &#8220;unused&#8221; will need to remain &#8220;unused&#8221;?

I apologize if this is a very noobie question. But what is the disadvantage of having two 125GB drives (since my BIOS can't handle 250GB). If I have programs on one drive and media files on the other. Is there any significant loss in efficiency or speed?

---

### Post by bernied on 2006-11-17
Just try it. Use gparted to create another partition in that empty space, create a filesystem in it, and see whether linux can see the space. 

Some things to keep in mind:
- it's generally best not to change the partitions of a disk that is in use. So do the gparted stuff from a livecd, not from your ubuntu install.
- in the linux world, multiple partitions are the norm, and if used well will make your system more robust
- it might be better to leave that space as empty space until you've done some exploring and have a better idea of what you want to do with it

Everyone here was a n00b once, most always will be

---

### Post by snik on 2006-11-17
Thanks for your help. 

I am happy that having multiple drives will make my system robust. Cool. Never dealt with partitioning using Windows XP, so I thought I would be losing out on something. 

I am going to try to create a drive in the unused space. But I was so psyched that I got Linux installed; that I've been playing with it, rather than going back and creating a drive in the unused space, I wasn't sure if it was possible and  I was afraid that it would mess up what was already installed.

---

### Post by bernied on 2006-11-17
Just read the instructions first. You can seriously mess up your system very easily, especially with tools like gparted.

google is your friend (even though they keep a file on you)

---

### Post by nadp on 2006-11-18
if im not mistaken, that is the limit of the FAT filesystem
I had that problem with the XBOX hard drive, it would only detect upto a 137GB.
now im not sure if it was FAT limitation or BIOS

if this was of no help, sorry >.<

---

### Post by CatKiller on 2006-11-18
> **nadp said:**
> if im not mistaken, that is the limit of the FAT filesystem
I had that problem with the XBOX hard drive, it would only detect upto a 137GB.
now im not sure if it was FAT limitation or BIOS

[This]("http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html") is a rather dated explanation, but it will probably suffice (first hit on Google).

There's a 2GiB partition limit on FAT16, and a 4GiB file size limit on FAT32. The reason you probably thought it was a FAT limit was because NTFS doesn't suffer from these two limits, but even if the motherboard supports 48-bit LBA, Windows (2000? XP? Can't remember) didn't without an update.

I believe that most motherboard manufacturers released BIOS updates to enable 48-bit LBA, which should just require a relatively straightforward - but potentially risky - BIOS flash. They didn't necessarily do this for every motherboard **model**, of course, but it's usually worth a check.

---

