---
title: "How big does /home need to be with no 'personal' files"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-01-18
I am revising my partitioning strategy to allow multiple OS's to all access my documents, mp3's etc. How big do I need to make a /home partition for ubuntu if I don't put any of my mp3's, documents, videoes, etc in there?

-Andrew

---

### Post by taurus on 2007-01-18
A couple of GB would be plenty if you don't plan to store anything in it.

---

### Post by Atreus12 on 2007-01-18
Ok, I got another question for you ;) 

On my primary drive (hda) I have 4 partitions:
Fat 16   I'm not sure, master boot record I think
NTFS    XP
EXT3    Ubuntu 6.06
Extended - Swap

I know you are only allowed to have 4 primary partitions. Does the extended swap count?

If I wanted to put another OS on, would it be possible? Is is possible to have the OS on a Logical partition?

Thanks for the help

-Andrew

---

### Post by taurus on 2007-01-18
Yes, the extended partition is count as one of the primaries.  So, if you have an extended partitions, you can now only have three primaries.  

Yes, you can install Linux on logical partitions if you want.  Works just as good.

---

### Post by bruenig on 2007-01-18
If home isn't going to host your files, then I wouldn't make a separate partition for it. I would just leave it with the root partition. The whole idea of /home is that if it is holding your files, you won't lost them if you lose your OS. But since they are on another partition, there is no purpose. Unless you are really in love with your . directories or something.

---

### Post by Atreus12 on 2007-01-18
> **taurus said:**
> Yes, the extended partition is count as one of the primaries.  So, if you have an extended partitions, you can now only have three primaries.  

Yes, you can install Linux on logical partitions if you want.  Works just as good.

So if I didn't plan this out right, can I somehow move my current primary partition containing the operating system to a logical partition, or do I have to reinstall?

---

