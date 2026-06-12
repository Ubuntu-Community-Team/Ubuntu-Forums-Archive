---
title: "recommendations for external hard drive?"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2006-01-13
Hi,

I would like to buy an external usb hard drive, but I heard that there are some possible problems with external hds and Linux. Is there any brand I should be worried about (am looking at a 200gb Matrox right now) or one that will most likely work without any headaches?

Would be glad for any advice, so that after the purchase I don't need to spam the forum with pathetic cries for help. :)

---

### Post by Deaf_Head on 2006-01-13
You shouldn't have a problem, if it ships with NTFS though you'll have to reformat it (which will be real quick and easy) into FAT

---

### Post by signbarn on 2006-01-13
I've heard that it's not good to have FAT partitions over a certain size ~30something Gigs? (i actually don't know) Can anybody shed some light on this?

---

### Post by RaiSuli on 2006-01-13
Thanks for the quick replies. From what I've read a FAT32 partition has no size limits, but there is a limit to the size of a single file. Apparently it can't be bigger than 4 gb. Hope this is correct.

@Deaf Head: the one I'm looking at has been formatted with FAT32, it just worried me that they only list different Windows versions as being compatible. But that is probably just company policy to be on the safe side.

---

### Post by aysiu on 2006-01-13
I have a Lacie 160 GB external hard drive that works perfectly with Ubuntu (it's FAT32, by the way).

---

### Post by Gandalf on 2006-01-13
I always prefered iomega over the others, I have 160Gb Iomega USB drive which i've made ext3, mounted on a server and accessible to everyone via NFS/Samba it works just great :)

---

### Post by blair on 2006-01-13
Any USB device should work fine.

---

### Post by juicybananahead on 2006-01-13
Booting from a LaCie 300GB external USB hard drive myself, no problems whatsoever.

---

### Post by John C on 2006-01-13
[QUOTE=blair]Any USB device should work fine.[/QUOTE]

I use a simple "USB 2.0 IDE Adapter w/power supply", and it works great
with Linux.  I can plug in an old/or new hard drive, CD,or DVD and have 
not had any problems with most flavours of Linux...

The great part is, you can find these priced as low as about $20.
Wouldn't be without this, as I can use anything outside my computer
box -- saves a lot of needless installation.  Of course USB 2.0 is pretty
much necessary for proper speed.

---

### Post by nandasunu on 2006-01-14
I recently got a 250gb Lacie drive (FAT32), very happy with it.

---

### Post by steve.horsley on 2006-01-14
I will add the Maxtor one-touch to the list of working drive makes.

Since I use mine for backup, it mostly contains large tar files. You can't write to NTFS, and vfat is limited to 4Gig files, so I reformatted mine as reiserFS (ext2/ext3 would also be fine, and you can get Windoze drivers for ext2 if you wnat to use windoze too).

---

### Post by RaiSuli on 2006-01-14
Thank you all for the quick and helpful replies! You put my mind to rest. 
:cool:

---

