---
title: "Can I use the same USB drive on both Ubuntu and Windows?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ___ on 2007-04-21
The easy way for me to find out would be to just plug it in and try it on both systems, but I've already hosed up one USB drive, so I figure it wouldn't hurt to ask this time.  And can I use files (like bookmarks and png files) from an Ubuntu system and use them on a Windows machine?  Would there any risk to the files?

---

### Post by M!K3_$ on 2007-04-21
giver er'
from my experience USB drives are pretty much universal.

about the files.
its worth a shot. You definatly will not mess up the files.
i dont kno if they will work tho.
like i said, worth a shot

---

### Post by BoneKracker on 2007-04-21
Yes, you can use the same drive.

However, there are still some issues with using read/write access from Linux on the NTFS filesystem.  So, if you have "formatted" the entire USB drive as NTFS, then you probably should only allow read-only access from within Linux for the time being.

If you want to be able to read/write to the drive from Linux then there are a couple of options.  First, you should copy any files you want to keep off of the disk:

a) If you want to be able to read/write the same filesystem (the same partition, the same files) from both Windows and Linux, then you should make it a vfat filestem, which is the only filesystem they can both read and write to safely.  Then you can put the files back.

b) Alternatively, you could create two partitions: one for Windows to use (NTFS is probably best, or vfat if you want Linux to also be able to use it) and one for Linux to use (ext3 is probably best, or vfat if you want Windows to also be able to use it).

---

### Post by medad on 2007-04-21
I use my USB stick all the time between the XP and Ubuntu systems here at the house when transferring documents, pictures, and music files.  Normally what I am moving around though are files set up for Word, MP3, PDF, pretty much anything related to what Windows can read.  I have taken my stick with me on trips and used it as backup for pictures from my camera that I moved using my in-laws XP and then I moved them over to the Ubuntu computer and copied them to a CD.

Your stick is most likely set for FAT32 which is read easily by both XP and Ubuntu.  I didn't need to reformat mine at all.

---

### Post by ___ on 2007-04-21
Wow.  Lots of good info.  Thanks for your advice.

---

### Post by b4lr0g on 2007-04-21
You can use ntfs-3g for read/write access to NTFS partitions. I don't know how safe it is, but I've been using it for quite a while and I didn't find any problems with it.

---

### Post by BoneKracker on 2007-04-21
Yes, depending on who you ask, they've "pretty much got all the bugs worked out now".  My advice to people generally is that I'd feel safe using it to access a shared partition that contains non-critical data, but I still advise against enabling read/write access to the actual Windows partition.

Depending on how important the stuff on the usb drive is, you might be willing to do it.  In all honesty, I haven't tried it in almost a year.  Maybe it's okay (enough) now.  Call me cautious.

---

### Post by jiminycricket on 2007-04-21
with ntfs-3g you have to be careful to unmount the external drives, like your usb card, before removing it.  Otherwise, anything can happen.

---

### Post by BoneKracker on 2007-04-21
Hmmm... one thing that might help with that issue would be to use the "sync" mount option, but that would slow down the disk access to some degree.

Probably worth looking into, especially for thinks like thumb-drives that people tend to just yank off (if you'll pardon the expression).

---

