---
title: "Hard Drive Question II"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Loki*PI on 2008-04-16
Let me try again, I asked this before but I didn't phrase the question well.

Originally I installed Ubuntu just to look at it and I like it.  I'm now using it as my main system, but I didn't plan it out this way so I"m running out of room.

I have an 80 Gig hard drive - NTFS.  Ubuntu is installed in a 16 Gig partition.  / and home are on it and it is getting full.  

I can manually mount the rest of the drive as /media/Local Disk.  I can move files onto it etc so that is OK.  There is data in this partition I don't want to loose. 

 I'd like to load some more software with add/remove but I don't see an option or how to control where the software is installed. I like to push the software onto the local disk.

Is there an easy way to deal with this?  Moving home looks dicey.  Suggestions would be appreciated.  

Thanks All.

---

### Post by tzulberti on 2008-04-16
There isn't a way to tell Apt where to install the programs. It's the DEB file which decides where to put the files.

---

### Post by indytim on 2008-04-16
Using GParted LIve or other partition managers, find out how much free space you have on the drive.  If you are just plain running short on a cumulative basis, then you don't have many options left other than adding an additional hard  drive.  If, on the other hand, you have adequate space on the hard drive, then you may need to re-allocate space between your available partitions.  Post your partition size, type and amount of available space here and someone can guide you.

IndyTim

---

