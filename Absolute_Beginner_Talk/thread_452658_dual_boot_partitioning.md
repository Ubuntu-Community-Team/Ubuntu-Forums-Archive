---
title: "dual boot partitioning"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by drravshan on 2007-05-23
hi all,
 am very new to ubuntu. i have both windows XP & ubuntu installed on my desk top having a 80 GB hard disc. when i first set up the partitions, i just did it wihtout having any knowledge about it. now i would like to edit or reset my partitions as there is some space free. 
tried using the Gnome partiton editor but couldnt understand anything. have taken a screenshot of the window. when i tried to utilize the free space, got a msg saying there cannot be more than 4 partitions. kindly help me in partitioning my hard disc without losing any data.
thanks,
ravi

---

### Post by Sparkster185 on 2007-05-23
You cannot have more than four physical partitions, but you can have more logical partitions.  If you're comfortable using the command line, you can try using fdisk.

What's the output if you run ```
sudo fdisk -l
```?

That screenshot link isn't working, BTW.

---

### Post by apunc1 on 2007-05-23
is that the correct screen shot? it's not of your partitions.

if you can post a screen shot of your partitions it might be helpful. are you trying to resize your current partitions?

EDIT: aha I see your partitons in the screen shot now.

---

### Post by Sparkster185 on 2007-05-23
If you click on the /dev/sda3 (your / partition), can you click the "resize" button?

---

### Post by drravshan on 2007-05-23
hi spark,
 sudo fdisc -l gives the following response
Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591    7  HPFS/NTFS
/dev/sda2             974        7399    51616845    f  W95 Ext'd (LBA)
/dev/sda3            7400        8677    10265535   83  Linux
/dev/sda4            8678        8808     1052257+  82  Linux swap / Solaris
/dev/sda5             974        4797    30716248+   7  HPFS/NTFS
/dev/sda6            4798        7399    20900533+   7  HPFS/NTFS
thanks
ravi

---

### Post by drravshan on 2007-05-23
hi spark,
 / partition cannot be resized, its not enabled
ravi

---

### Post by apunc1 on 2007-05-23
/ needs to be unmounted before you can resize it

boot up with the live cd and use the partitioner there to resize your partitions.

---

### Post by Sparkster185 on 2007-05-23
I'm still pretty new to Linux and partitioning can ruin your system if you don't do it right so I don't want to say anything that I'm not 100% sure is correct.

I've never used GParted (I'm a Kubuntu user), but I did have to use fdisk a couple of times.  If you look up how to use fdisk, you should find how to resize an existing partition.  You might need to delete the swap partition, re-size your /dev/sd3 (/ partition) one, and then re-create swap at the very end of the disk.

Once again, I'm no expert so you might want to wait for someone else to answer.

---

### Post by Sparkster185 on 2007-05-23
> **apunc1 said:**
> / needs to be unmounted before you can resize it

boot up with the live cd and use the partitioner there to resize your partitions.

Oh, that makes sense.  When I used fdisk, I was messing around with /home (it's own partition), so that's why I was able to without problems.

Just for my own knowledge, is there a way to use GParted from the LiveCD without going through a full install?  Can you just get to the part about partitions, adjust them and then abort the installation?

---

### Post by Inxsible on 2007-05-23
> **Sparkster185 said:**
> Oh, that makes sense. When I used fdisk, I was messing around with /home (it's own partition), so that's why I was able to without problems.
 
Just for my own knowledge, is there a way to use GParted from the LiveCD without going through a full install? Can you just get to the part about partitions, adjust them and then abort the installation?
 
Yes you can abort in between, but you'd need to partition the drive sometime and using some partitioner. So why not use GParted itself ?
 
I haven't seen a better partitioner around

---

### Post by apunc1 on 2007-05-23
> **Sparkster185 said:**
> Oh, that makes sense.  When I used fdisk, I was messing around with /home (it's own partition), so that's why I was able to without problems.

Just for my own knowledge, is there a way to use GParted from the LiveCD without going through a full install?  Can you just get to the part about partitions, adjust them and then abort the installation?

my mistake. 
i'm guessing the OP will need the official gparted cd for this. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

