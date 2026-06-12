---
title: "I want to remove partitions and format my hard disk"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2008-04-03
Hi Ubuntuers:

Before installing Ubuntu, I want to remove all partitions and reformat the hard disk from the live CD.

That disk is such a mess, I think that Ubuntu is having a hard time in its installation... after previous installs, Ubuntu dies!

Can somebody provide step-by-step instructions on how to remove all partitions and reformat the hard disk from the live CD?

Thanks,
Phil Smith
Duluth, GA

---

### Post by TeoBigusGeekus on 2008-04-03
Type 
```
sudo gparted
```
in a terminal to open gnome partition editor.

---

### Post by njparton on 2008-04-03
The partitioner screen during the installation process lets you delete and then add/format partitions.
 
Start the installation process then chose manual partitioning on *about* the 2nd or 3rd screen.

---

### Post by bovus on 2008-04-03
When your running off the Live CD, you can also get to gparted by going into the administrator options.  I belive its called partition editor

---

### Post by njparton on 2008-04-03
You could try that but gparted running off the live CD seems to be very buggy judging by quite a few posts around the forum.
 
Another alternative would be to download the free "super F disk" bootable CD and use that to clean up your hard drive and it's MBR first.

---

### Post by mcdan on 2008-04-03
if you don't like gparted on the ubuntu disk, you can use the gparted stand alone CD, it is easier, loads faster, works faster, and gives you the ability to modify mounted drives, like an external.  i prefer it over the ubuntu live cd

---

### Post by hyper_ch on 2008-04-03
> **bovus said:**
> When your running off the Live CD, you can also get to gparted by going into the administrator options.  I belive its called partition editor

Only problem is the desktio cd will auto-mount recognized ext3 partitions... you you first have to umount those before you can partition them.

---

### Post by vanadium on 2008-04-03
You have different options indeed. The easiest option for you is probably to run gparted from the life session to delete all partitions. If a partition is mounted, you can, in gparted, right-click it to unmount. Then quit gparted and click the install icon to launch te install program. Now  have Ubuntu partition the drive automatically.

If you want custom partitioning, then you can start the instal program right away. Then choose custom partitioning. You will first have to delete the existing partitions, create the new partitions and indicate the mount points. It is more complex, so I advise you to stick wit option 1 unless you are confident enough.

---

### Post by prismpirate on 2008-04-03
To me, the easiest way would be to install. When it comes to the partitioning part, choose manual, delete all partitions :).

Then make a ext3 partition with approx 10gb of space, and the mount point should be /.

Make a swap partition with approx 1024mb of space..

Make another ext3 partition with the remainder, the mount point should be /home

Click next to the end and you've succesfully removed all partitions and installed ubuntu.

---

### Post by vanadium on 2008-04-03
Partitioning and assigning mount points is not the easiest option for beginning users, in my opinion.

---

### Post by MrWES on 2008-04-03
This is exactly how I did my install on an old desktop. I just booted the live CD and choose manual. I put 10gb in /  1gb as a swap (make sure you don't use /swap, but make the file type swap) and then the remainder in /home. Worked like a charm on a 160GB hard drive.

Bill

---

### Post by Old Jimma on 2008-04-03
Hi All:

I got so many great responses to my query... I am very thankful! My machine is running again!  :-)

Special thanks to prismpirate, vanadium, njparton for the useful information they provided!

Sincerely,
Phil Smith
Duluth, GA

---

### Post by ClearyA on 2008-04-03
ya i find your best bet would be a bootable cd of Gparted... it works well as a hard drive cleaner partitioner etc.

---

