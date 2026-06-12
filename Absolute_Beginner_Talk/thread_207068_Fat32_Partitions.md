---
title: "Fat32 Partitions"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-07-01
Okay, this is a minor issue, but it irritates me.  I have a Fat32 partition mounted sometimes, and it is always shown in capital letters.  Is there any way to get it shown in lowercase, like NTFS partitions and other such partitions?

Thanks.

---

### Post by bohboh on 2006-07-01
Where do you mean? Where is it being shown in capitals?

---

### Post by Apple 101 on 2006-07-01
On the Desktop, the drive icon is normal, but the text label is in capital letters, not in writing like *Ubuntu*.  How can I change this?

---

### Post by macdo on 2006-07-01
Find out where the mount point is, (in your case, it's probably something like '/media/HDA2') and create a new folder in that place: ```
sudo mkdir /media/fat32
``` (You can replace fat32 by anything you like...). Open the Disk manager in the administration menu, choose the correct partition and change the mount point to be the new folder. Then OK.

If that's not clear, say so...

---

### Post by Apple 101 on 2006-07-01
I did that, and clicked the Enable button as well.  The disk is still shown in capitals though.  Here is a screenshot of it.

---

### Post by Apple 101 on 2006-07-02
Does anyone else see that?

---

### Post by someusernoob on 2006-07-02
Yes, i got this on my other PC, and it has a fat32 disk. The dir in which the disk is mounted is /media/Documenten but the desktop icon shows DOCUMENTEN. Didnt bother me tho, so i have no solution.

---

### Post by coffeecat on 2006-07-02
I think the problem is the actual partition label - that's in the partition table somewhere. When I set up this quad boot in my laptop I designated partition labels for each of the partitions I set up with Gparted. See my screenshot. VAIO is the Windows C partition and 'Shared_Data' is my fat32 partition - see, lower-case. SuSE_101 and Fedora5 are obvious, and if I was in one of them instead I would see 'Ubuntu' for the partition I'm in at the moment.

Having said that, I know of a utility for relabelling an ext3 partition without destroying the data, but I haven't come across one for fat partitions. I suppose you could backup all your data and reformat your fat32 partition and relabel it while you are doing that, but that's rather drastic. Try googling for relabel fat32 partition.

---

