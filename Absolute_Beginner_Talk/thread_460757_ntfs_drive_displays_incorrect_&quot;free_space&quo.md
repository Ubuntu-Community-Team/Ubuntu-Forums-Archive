---
title: "ntfs drive displays incorrect &quot;free space&quot; under properties"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by lazerous on 2007-06-01
This is kinda silly, but I checked google and the forum and didn't find anything.

Since I switched to Feisty from WinXP, I have a couple ntfs drives that I need to keep until I can move content around to format them.  Everything mounts fine and I can read/write to the drives, however when I check the properties and look at the "free space", the amount is incorrect.  My 120 gig drive with 58 gigs used (under contents) shows 5.5 gigs free.

Does anyone know what could cause this?  

[Laz]

---

### Post by Patrick K on 2007-06-01
I wish I did since I have a similar issue with Fat32 partitions. I've posted here and on other forums and have filed a bug report but have never got an answer.  As with anything out of the ordinary, you'll likely never get an answer. Just part of the joy of Linux.

---

### Post by lazerous on 2007-06-01
So can I continue to write to the drive, even if it goes beyond the free space?  I haven't really tested that portion, but it surprises me that more people aren't having this issue.

Thanks for responding, hopefully we'll both find our answer.

[Laz]

---

### Post by Michaelt74 on 2007-06-01
This link may help to see what's taking up the space on your drive
[http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/](http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/)

---

### Post by Patrick K on 2007-06-01
I don't know what will happen when you exceed what the system thinks you have in free space. You might backup that partition and try writing large files to it. It's the only way I can think of to test it out. 

Actually, my problem is just the opposite. I have several FAT32 partition that show way more free space then they really have. One shows 580mb used (and 35GB free) when it actually has well over 20GB used (and about 14GB free). Good luck, I hope you find an answer.

---

### Post by szaka on 2007-06-01
Did you check this out? [http://ntfs-3g.org/support.html#diskspace](http://ntfs-3g.org/support.html#diskspace)

---

### Post by lazerous on 2007-06-01
Thanks.  I'm an idiot.  I don't know which post had it...but when I'm deleting files from those drives, they're not going to the trash (as in gnome trash on my desktop).  They're going to a hidden folder (.trash) on the individual drive.  Once I remove the files from the hidden folder, the free space is updated.

Thanks for all of the help everyone.  God I love having a community.

[Laz]

---

### Post by kaay on 2007-07-23
For those who experience the same but with the "missing" space being truly free (partitioning utils and other OS's see it), try
```
dosfsck -r {partition}
```
(You might need to unmount first).
It should give you
```
Free cluster summary wrong (28382 vs. really 861151)
1) Correct
2) Don't correct
? 1
Perform changes ? (y/n) y
```
This isn't exactly a solution, but a working fix for when the problem manifests itself.

---

