---
title: "Installation Help: Partitioning..."
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2007-08-22
Hi frenz,
 
       Yestday, i was tryin 2 install Fiesty (kubuntu) frm the "Alternate CD"
Dual-boot with Win XP.

Wen the partitioning screen came up, i chose "Manual partitioning":

The screen read thus:

---------------------------------------------------------------------------
SCSI1(0,0,0) (sda) - 80.0 GB ATA ST38001A
#1 primary  21.0 GB     B       K    fat32      /media/sda1
#5 logical    21.0 GB              K    fat32      /media/sda5
#6 logical    21.0 GB              K    fat32      /media/sda6
#7 logical    17.1 GB              K    fat32      /media/sda7

-------------------------------------------------------------------------

In windows, I used to get 4 drives (in above order) as C:/  ,  D:/   ,    E:/ 
and F:/

I plan to use D:/ drive (#5 logical, see abv tabl) completely for Ubuntu.

I've cleaned-up the D:/ drive , except for 2 GB of immovable windows-application programs.

So, i have some 18 GB left. I need, 16 GB for ubuntu in itself and 2 GB swap...

But i dont know how to proceed from the above screen & do this... help !

---

### Post by kidcharles on 2007-08-22
First off, you might want to make double-plus sure that what Ubuntu sees as partition 5 is really your D: drive. (I think you are right by the way.) The way you can do this is by mounting it during the live cd session and checking the contents.

```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5

```

Then 'cd /media/sda5' and poke around a bit to make sure it isn't one of your other drives.

Actually, before you go further, I think you might be better off putting Ubuntu at the end of the drive (like using that partition 7) instead of in the middle (partition 5). Sometimes you can run into trouble repartitioning in between a bunch of other partitions. If you delete the partition 7 (after moving your data of course) you can easily make two new partitions, one for the Ubuntu installation and one for the swap file.

If you want to give the partition 5 a go, you should start by deleting that partition during the manual partition stage. Then in the free space you should be able to create new partitions, but again, you might run into trouble.

---

