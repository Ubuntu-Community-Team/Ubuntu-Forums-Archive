---
title: "Partition for Windows, Ubuntu, Swap, and Files"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Perogies on 2006-07-27
I was following the partioning guide found [here]("http://www.psychocats.net/ubuntu/installing.html") and so I now have 4 partitions: Windows, Ubuntu, Swap, and one that I was hoping to use just to store my documents such as pictures and OpenOffice files.  Near the end of the guide the author names one partition "/documents" which I also did.  Later I went looking for this so I could save my files there, and found "/documents" in the File System.  I tried creating a folder here, but it told me access was denied.  

Now to my question.  Should I do something different with this partition, is /documents the /documents partition I made, am I simply doing something wrong?

Earlier I browsed Absoulute Beginners and saw the many threads about partitioning drives.  As far as I know and searched I didn't see anything pretaining to my situation, so forgive me if I overlooked my answer somewhere.

---

### Post by Sef on 2006-07-27
Open a terminal and post the results here of this command below:

Applications > Accessories > Terminal

sudo fdisk -l

to copy in the terminal > hightlight the text then ctrl + shift + C

to past in here > ctrl + V

---

### Post by Perogies on 2006-07-27
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        4864    30876930    5  Extended
/dev/hda5            1021        1085      522049+  82  Linux swap / Solaris
/dev/hda6            1086        1467     3068383+  83  Linux
/dev/hda7            1468        4864    27286371   83  Linux

---

### Post by Sef on 2006-07-27
> /dev/hda2 1021 4864 30876930 5 Extended

That caught my eye, so I did some research and came up with this:

> 05 Extended DOS 3.3+ extended partition

I wonder if your problem is related to this.  It don't look like a FAT32 file for sharing documents.  

(Anyone with more experience please confirm or not, what I said.)

---

### Post by Perogies on 2006-07-27
I don't really plan on sharing files between Windows and Ubuntu, does that matter?  The only reason I'm keeping Windows is so I can have sound when I watch movies.
mine,
I guess I'm mostly confused about where to put the files I made the partition for.

Attached is how I set up the partitions.  This isn't my set up exactly, but the one from the website I linked to in my first post that I followed.

---

### Post by confused57 on 2006-07-27
It's probably just a matter of mounting the partition and assigning permissions:
[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

I'm not sure since you already assigned the mountpoint as "documents"...aysiu wrote the guide, he'll probably be able to give you more specific instructions.

---

