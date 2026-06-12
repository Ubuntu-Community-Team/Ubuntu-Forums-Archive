---
title: "Formatting and Labeling USB Drives"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by marianoi on 2007-03-21
Hello everyone,

I have a simple question, actually 2 questions. I liked to re-format a USB pen drive today but I did not find an easy choice to do that. Then I found a post somewhere here in the forums explaining that you have to change the preferences (System-Preferences-Removable Drivers and Media) so the the USB is not automounted. Then you can use GParted to format the partition.

Well, that worked pretty well but now I like to label the pen drive (when mounted it just says "disk"). How could I do that?, I'd like it to say "Mariano" instead...in Win that is pretty easy to do...is there an equivalent here?

Other thing, is there an easier way of formating a disk through a dialog in GNOME? something that will unmount the drive if mounted and then proceed with the formating and then re-mount the formatted drive?

THANKS A LOT FOR HELPING!

Cheers from Columbus, OH

Mariano

---

### Post by sanft on 2007-04-04
Hello, I was searching for this exact information myself.  I've been scouring the net for a solution, but I'm unable to figure this one out either.

Bookmarking this and hope someone will be able to clarify. Will check back soon!

Cheers,
sanft

---

### Post by LaRoza on 2007-04-04
I labelled my disks in Windows, but I thing you right click the icon and go to "Properties" and label it there. I am at school and don't have Ubuntu in front of me so I can't say exactly how. If you label the disk in Windows, it will show up in Ubuntu.

---

### Post by vanadium on 2007-04-07
This thread explains how to add labels to 
[http://ubuntuforums.org/showthread.php?t=322973](http://ubuntuforums.org/showthread.php?t=322973)

Probably it depends on your file system. For my fs3 formatted usb drive, the command 

e2label /dev/sdb1 usd_data

(with the command "df" you can find the name of your usb drive).

For FAT drives (which you obviously can also change in Windows if you own that OS), you seem to need the mtools as also explained in the thread I referred to.

---

