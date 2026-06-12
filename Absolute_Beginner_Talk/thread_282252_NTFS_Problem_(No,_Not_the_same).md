---
title: "NTFS Problem (No, Not the same)"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by darthcoder on 2006-10-22
Hi All,

First up, let me share my experience with you guys.
Installing Ubuntu was not a choice but a necessity for me (Corrupted WinXP CDs) and now ave come to like it :).

Thanks to this great community here who help each other a lot.
Especially the senior geeks who dont belittle n00bs and are very patient with them :).Ave already configured my Samsung ML1610 through the searching the forum!!

OK, Now to the problem.
I have a secondary HDD (The primary one has Ubuntu installed on it) and the secondary one has nothing, just data on it.

Now, I mounted the secondary HDD after searching the numerous NTFS Mounting help threads and managed to mount the HDD.But, I am able to see only one Partition(the last partition F: and not the other 3 C:,D:,E:) of the HDD at my desktop (Mount point /media/windows) and not the other 3 partitions of 
the HDD.

Now, what do I do to access the other 3 partitions of my HDD??

Would be grateful if someone could help me with this :)
I wanna play CSS!! :D.


Ever grateful,
Darthcoder.

---

### Post by qamelian on 2006-10-22
Can you post the contents of /etc/fstab? You need an entry in this file for each partition.

---

### Post by darthcoder on 2006-10-22
Here are the contents of fstab, the new line that I have added is /dev/sdb5
the /dev/sdb5 showed up in my "My Computer" thingy in ubuntu and therefore I added only that.

Is there any way I can find out the names of other partitions??

Thanks.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1 /windows_ntfs ntfs nls=utf8,umask=0222 0 0
/dev/sdb5 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by qamelian on 2006-10-22
You could install gparted which would allow you to view and identify the partitions on each drive. There may be other ways as well, but I'm not sure. Once you've identified the other NTFS partitions, you just need to add lines to fstab for each partition you want to mount automatically. They would be similar to the one you've already added, but with the appropriate changes for the partition names.

---

### Post by darthcoder on 2006-10-22
How do I get to know the names of the other NTFS Partitions??Any idea??
Cos they dont show up anywhere.If I could just get the names of the other partitions then that would be helpful for me to mount them too.

---

### Post by rccharles on 2006-10-22
> **darthcoder said:**
> How do I get to know the names of the other NTFS Partitions??Any idea??


Have you tried fdisk?

in the terminal, ( applications -> accessories -> terminal )

sudo fdisk -l

# and the -l is the letter l for list 

Robert

---

### Post by darthcoder on 2006-10-22
Hi Charles, this is what I do when I did fdisk.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   42  SFS


I may be able to guess the partition names but how do I mount them in fstab??I guessed the partition names as sdb 2,3,4 (sdb5 is the partition I am able to access) and tried to mount the sdb 2,3,4 by doing this in the fstab

dev/sdb5 /media/windows ntfs nls=utf8,umask=0222 0 0 
/dev/sdb4 /old-drive1 ntfs nls=utf8,umask=0222 0 0
/dev/sdb3 /old-drive2 ntfs nls=utf8,umask=0222 0 0
/dev/sdb2 /old-drive3 ntfs nls=utf8,umask=0222 0 0

Another doubt, for creating mount points , I need to create different directories, right?Where do I create the directories??Only in /media??

Like /media/old-drive1 ??

Hope am not confusing you guys :(.

Thank you :).

Darthcoder.

---

### Post by darthcoder on 2006-10-23
w00T!!
i got it !!
Thanks guys!!

---

### Post by jwbirdsong on 2006-10-23
I'm curious..you answered your own question, Right?? 
> Like /media/old-drive1 ??

In your fstab you didn't have a complete mount point (2nd path in the line)..you just had 
> /dev/sdb4 /old-drive1 ntfs nls=utf8,umask=0222 0 0
/dev/sdb3 /old-drive2 ntfs nls=utf8,umask=0222 0 0
/dev/sdb2 /old-drive3 ntfs nls=utf8,umask=0222 0 0


Did you just see  it after re-reading your post a coupe of times??

How ever you did it Good Job.... People that will "Roll up their sleves" and look/work for their own solutions ROCK!!

---

### Post by darthcoder on 2006-10-23
Hey jwbirdsong :).
Yes, I answered my own question :), but with a lot of help with the community's help in this thread :).

Being the nut-case I am, I shudve written this in /etc/fstab

/dev/sdb4 /media/old-drive1 ntfs nls=utf8,umask=0222 0 0

instead of 

/dev/sdb4 /old-drive1 ntfs nls=utf8,umask=0222 0 0

because I had done mkdir old-drive1,2,3.. in the /media folder and not the "/" path :(.I figured that out and did the changes in fstab and now I can see all my drives on the desktop :) (I guess putting them in /media makes them appear on the desktop).

Anyways, thanks guys!!
Am coming back to bug you guys more though :D.

This community rocks!! :).

Regards,
Darthcoder.

---

