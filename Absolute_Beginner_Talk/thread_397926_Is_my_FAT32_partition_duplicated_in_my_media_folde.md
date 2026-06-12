---
title: "Is my FAT32 partition duplicated in my media folder?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by pollywog on 2007-03-31
Hello, I have a question about mounting fat32 partitions on an edgy system. I have a 50g fat32 partition on my hard drive which I use as a safe haven for my data. I have used the procedure shown in :

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29)

to automatically mount the partition. Sure enough, an icon appeared representing this as "hdb3". I noticed that when I tried to make a tarball of my system that my "media" directory contains all the data on this remote partition. I tried to exclude this directory on a subsequent attempt to back up. I then tried to copy the tarball (over 10G's) from" /" to "hdb3" and found that the copying abruptly stopped less than halfway thru the process giving me only about a 4G backup on hdb3. when I used the  graphical disk map to examine my filesystem I found that the whole 10G+ was sitting there in my "media" directory, along with everything else on my fat32 partition. I had just assumed that media was just a portal thru which I was seeing hdb3, but this discrepancy would seem to suggest that everything that I put on my fat32 partition is actually being copied -imperfectly at that- over to "media". Is this just an illusion, or is all that data actually being copied? That just doesn't seem right.- P.W.

---

### Post by eljalill on 2007-03-31
As far as I know, it's the other way around: 
The partition is really mounted to /media . On the desktop there is just some kind of link, the file system really is in /media. So if you copy the /media to your partition, you are copying itself. But since reflexive copying is a (pretty philosophical) problem, it seems likely, that it didn't work.... :) Or just copied, what was not already on the partition, which would explain the difference in size.

---

### Post by pollywog on 2007-03-31
Yea, that would explain the discrepancy- Thanks

---

### Post by perspectoff on 2007-03-31
No, the data is not being copied. Ubuntu by default lists all drives as being "mounted" in /media.

(You can, if you choose, actually "mount" any hard drive or hard drive partition, or CD-ROM drive or other media for that matter, to any folder you choose, through the "Disks" menu item.)

As discussed in other replies, it is only a "symbolic link" ("Shortcut" in windows parlance) to your hard drive partition that appears in /media. Note that the fact that the data on the partition appears to be "imperfectly copied" is not a function of the data, but is probably a function of your settings in the Nautilus File Browser. You may not have it set to show all files (such as hidden files, etc.) 

> **pollywog said:**
> Hello, I have a question about mounting fat32 partitions on an edgy system. I have a 50g fat32 partition on my hard drive which I use as a safe haven for my data. I have used the procedure shown in :

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29)

to automatically mount the partition. Sure enough, an icon appeared representing this as "hdb3". I noticed that when I tried to make a tarball of my system that my "media" directory contains all the data on this remote partition. I tried to exclude this directory on a subsequent attempt to back up. I then tried to copy the tarball (over 10G's) from" /" to "hdb3" and found that the copying abruptly stopped less than halfway thru the process giving me only about a 4G backup on hdb3. when I used the  graphical disk map to examine my filesystem I found that the whole 10G+ was sitting there in my "media" directory, along with everything else on my fat32 partition. I had just assumed that media was just a portal thru which I was seeing hdb3, but this discrepancy would seem to suggest that everything that I put on my fat32 partition is actually being copied -imperfectly at that- over to "media". Is this just an illusion, or is all that data actually being copied? That just doesn't seem right.- P.W.

---

### Post by Patrick K on 2007-03-31
Don't forget the FAT32 has a max file size limit of 4gb.

---

