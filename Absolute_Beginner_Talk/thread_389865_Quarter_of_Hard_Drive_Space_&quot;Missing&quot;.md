---
title: "Quarter of Hard Drive Space &quot;Missing&quot;"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by duncanpc on 2007-03-21
I seem to have lost about 17GB of the drive space in my root partition. Disk Admin utility reports size   
 of partition as 71GB (which is reasonable) and used space is given as 42GB. I thought this looked rather high so I used the graphical file size option in konqueror to look at the root directory and found the total size to be 27.3GB. This is close to what I expected so what is in the missing space?

I have tried fsck but it immediately comes back clean without scanning so I presume it simply reads the partition table. Is there a way of forcing a scan (similar to the one done on every 30th start)?

Not sure if this is significant but fsck tells me I have 144255 files in the partition but konqueror can only see 143108 with hidden files set visible. That's over 1000 phantom files!

I am using Kubuntu 6.06 on a machine with 2 hdds. I have 2 NTFS partitions on the 1st (160gb) drive (they both report correct free space) and ext3 and swap partitions on the 2nd 80gb drive.

I would be very grateful to anyone who can shed some light on this.

---

### Post by bapoumba on 2007-03-21
May be some deleted files that belong to root ?
What does **df -H** returns ?
Check your .Trash in your /home.

---

### Post by Michaelt74 on 2007-03-21
Did you run a backup? If so, the backup will eat a lot of space on your drive.

This link may be of assistance:

[http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/](http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/)

---

### Post by duncanpc on 2007-03-21
Thank you both for replies. Michaelt74 you were spot on with your backup theory. I found I had a 15GB backup file in /var that was invisible to konqueror. Obviously I'll have to learn more about file management from the command line. The backup should have gone to my external HDD so I must have messed up a setting somewhere. Anyway, I've removed the file and I now have 40GB of free space. Thanks again.

---

### Post by Michaelt74 on 2007-03-23
Glad to have helped, all the best.

---

