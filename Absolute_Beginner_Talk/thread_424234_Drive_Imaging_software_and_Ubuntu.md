---
title: "Drive Imaging software and Ubuntu"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-04-26
Do programs like Ghost and Drive Image work with Ubuntu's  file system?  

I use Drive Image 2002, which requires that the destination drive be formatted FAT32 (because it works from DOS, the destination partition must be accessible from DOS).  I currently use Win2k and NTFS and am able to image the NTFS partitions onto my FAT32 partition.  I was curious if I could do the same with Ubuntu and its file system.

Thanks,
Tim

---

### Post by Campingman on 2007-04-26
I have used partimage to create and store an image of Ubuntu to a fat32 partition.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
It runs in a terminal and has to be run from a live cd or equivalent as the partition to be copied cannot be mounted at the time.  it does work well as i have done a full restore of an edgy image perfectly.

---

