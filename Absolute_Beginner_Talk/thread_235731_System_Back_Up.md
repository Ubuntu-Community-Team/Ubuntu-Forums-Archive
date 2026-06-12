---
title: "System Back Up"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Geffers on 2006-08-13
I'm using Ubuntu on a Dual Boot machine with Ubuntu booting from hda3 and currently, owing to a recent power failure my other system ( Win98 ) is not working.

The Win98 system is viewable via ubuntu and my data is on another drive.

My main disk is a little eratic lately so I want to back up my old Win98 folder (only for the files, not necessarly to boot again) and my Ubuntu system.

What is the best procedure to do so, Nautilus for some reason does not copy the entire contents of my Win98 (I am the owner so copy should not be a problem).

I tried gparted but it needs partitions to be unmounted which I can't do for my Ubuntu system.

Any suggestions appreciated.

Geffers

---

### Post by djsroknrol on 2006-08-13
I would make a drive image on the other drive with partimage. I've used it to make images for backup, recover and restore and it has never let me down.

---

### Post by ironfistchamp on 2006-08-13
Hey

I think the copying problem could be down to the partition with win98 on being FAT32 (it is FA32 right). I tried copying to and from a FAT32 partition and it didn't work correctly.

To unmount everything you can boot from a live CD and use gparted from there. That way nothing is mounted from the start and you can edit as much as you want. Are you wanting to copy a partition or something?

Hope this was of some help. I don't really know about backing up at all. I just put anything I want to keep on a seperate partition and hope for the best.

Ironfistchamp

---

### Post by Geffers on 2006-08-14
> **djsroknrol said:**
> I would make a drive image on the other drive with partimage. I've used it to make images for backup, recover and restore and it has never let me down.

My second installed drive is much smaller than the one I have problems with but it may work with an external USB drive I have.

Thanks for info.

Geffers

---

### Post by Geffers on 2006-08-14
> **ironfistchamp said:**
> Hey

I think the copying problem could be down to the partition with win98 on being FAT32 (it is FA32 right). I tried copying to and from a FAT32 partition and it didn't work correctly.


Yes it is FAT32 but to date I've had no problem copying either way but then of course I am having a problem with this copy/backup attempt.

> **ironfistchamp said:**
> 
To unmount everything you can boot from a live CD and use gparted from there. Hope this was of some help. 
Ironfistchamp


Good suggestion :)  I already have a liveCD of gparted so will probably give that a try, thanks.

Geffers

---

### Post by djsroknrol on 2006-08-14
Geffers;

What size drives are they? If your Ubuntu install could fit on the other drive, you could move it with Partimage and bring it back to the original position after you change the drive out, or whatever you need to do. 

[Here]("http://www.raoul.shacknet.nu/2006/01/06/partition-images-with-partimage-and-partimaged/")
is a good link to instructions as to how to use Partimage. Another prominent member of this Forum, aysiu, has a great link for it on his website as well...

---

