---
title: "Changing Size of Ubuntu Partition on Mac OS X/Ubuntu Dual Boot"
date: 2013-10-14
forum: Apple Hardware Users
---

### Post by pvasudev on 2013-10-14
I currently have a MacBook Pro and on it is a 20 GB partition with Ubuntu.  I want to make this partition larger, and in doing so, I am perfectly prepared to delete my current Ubuntu partition.  I see four partitions on my HD using the Mac's Disk Utility:

10.7.4b - Mac OS Extended (Journaled) (478 GB)
disk0s3 - Linux Swap (1 GB)
DISKOS4 - MS DOS FAT (20.61 GB)
disk0s5 - Mac OS Standard (2.1 MB)

Here are my questions:

1) Could gparted from an Ubuntu boot disk be used to edit the partitions?  Disk Utility will not let me.

2) Assuming the response from (1) to be positive, would I erase disk0s3 and DISKOS4 and then use the Mac's Disk Utility to adjust the Ubuntu partition size as described in the Dual Boot Tutorial? ([https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation))

3) I'm confused why the 20 GB partitions is showing up as MS DOS, when Linux uses another file system (which I can't remember the name right now.)  Can someone tell me why this is?

Thank-you very much!

Pranai

---

### Post by pvasudev on 2014-01-24
Can anyone help me with this?

Thank-you!

---

### Post by Mark Phelps on 2014-01-24
> Can anyone help me with this?

You do realize this is a Linux forum, not an Apple forum, right? You should pose your questions about the Mac's utility on an Apple forum.

---

### Post by coffeecat on 2014-01-24
I'm sure there are people on this forum who dual-boot MacOS and Ubuntu On Apple hardware and who can help the OP with their goal of making the Ubuntu partition larger, however this can be done.

@pvasudev, I've moved your thread to the Apple sub-forum where it is more likely to be seen by people who have the right experience to help you.

---

### Post by Balamku on 2014-01-25
I'm not a Mac pro, but this worked for me:

With Maverik 10.9 you can resize your partition if you want. To use this method, start Disk Utility, (Applications > Utilities) . Move to Partition in the submenu (you have to be on the top level on the right, in my case its 1TB xxx Media and below Macintosh HD and Macintosh HD2). In the graphic layout click on the partition you want to resize. Once its activated you will see Name, Format and Size on the right side. Type in the size you want and click Partition in the pop-up.
Hope this helps!

---

