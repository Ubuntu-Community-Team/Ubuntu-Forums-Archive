---
title: "Filesystem Only Writes to One Drive"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by novus721 on 2007-04-30
Hi all,

I have two WD drives hooked up right now and both are recognized together in the file system under Disk Usage Analyzer, however, whenever I try to import the song from my ipod to Banshee it tells me that the drive is full (referring to my primary drive) and aborts - how can I write to my second drive?

It was an old NTFS file system with xp but it seems that feisty has taken over it (I am assuming since it is in my file system, and is fine because I have no need for windows), but only root has access to the drive and I cannot write to it apparently whenever I try to drag files right into the drive. Is there a format that I need to do or something? Properties for the drive state it is read-only. 

Is there some sort of format cmd line I can utilize to be able to write to my slave? I am less than a month into Linux so sorry if this is a real simple problem haha. Thank you all so much, any help is greatly appreciated!

---

### Post by psusi on 2007-04-30
Yes, you need to format it with a unix filesystem instead of windows to be able to make full use of it.  I suggest that you fire up gparted from the livecd and format it as ext3, then update your /etc/fstab to show that it is ext3 instead of ntfs.

---

