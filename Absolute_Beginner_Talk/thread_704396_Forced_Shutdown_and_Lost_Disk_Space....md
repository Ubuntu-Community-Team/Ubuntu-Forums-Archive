---
title: "Forced Shutdown and Lost Disk Space..."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Simon C. McLeod on 2008-02-22
Used Ubuntu 7.10 LiveCD to resize an NTFS partition from ~30GB down to 23GB, leaving ~7GB of free space after the partition. Tried to shut down, but weird problem with greeter program interrupted shut down and I was forced to press the power button.

Booted into Gutsy, the 7GB have disappeared. According to GNOME Partition Editor, hard disk has shrunk in size from ~120GB to 112GB. Booted into Vista Business, same result from Disk Management. Is there any way to fix this? I imagine it's something to do with the partition table...? (*fdisk -l* reports that the disk is 120GB, though...)

Many thanks in advance. Was going to make a new partition out of those 7GB and study Wine's ability to run games...

(Used LiveCD to resize because Vista refused to shrink the partition down more than a few hundred megabytes, in spite of the fact that the partition had ~20GB of free space...)

---

### Post by Sam Lars on 2008-02-23
So the partition editor and Windows think that the whole hard drive is 112, but fdisk sees it as 120?
Are you sure that the free space is gone and it thinks that the partition is the whole drive?  Could you post a screenshot of the partition editor, etc., and what they see?

---

### Post by Simon C. McLeod on 2008-02-25
Here we go - I've looked at cfdisk as well...

---

