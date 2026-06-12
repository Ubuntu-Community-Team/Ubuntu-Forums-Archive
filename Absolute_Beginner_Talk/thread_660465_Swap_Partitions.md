---
title: "Swap Partitions"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Truck449 on 2008-01-06
Hey guys i was curious about swap partitions i already have linux installed on my laptop without a swap partition. Why are they so important and is there a way to add one after having partitioned for the install without starting over?

---

### Post by eapache on 2008-01-06
A swap partition is the linux equivalent of a Windows page-file. When you run out of ram because you're running a lot of programs (or are running really big ones like video editors), some of what is normally in ram gets shifted to swap. Swap is on the disk, so is much slower, which is why it is used only as a last resort.

Whether you need a swap partition depends on the amount of ram you have. Ubuntu won't let you install without a swap partition though, so that's peculiar.

---

### Post by Blutack on 2008-01-06
For performance reasons linux uses a seperate swap partition rather than a swap file.  They are important because if your system runs out of memory and needs to swap out and can't, everything can end in tears.  Having said that I accidentally ran my laptop for 6 months (1gb of ram) with no swap and never ran out of memory...
You can boot from an ubuntu live cd and use the Partition Editor in admin menu to resize your ext3 drive down a bit and create a swap partition (normally around 1gb) in the space you freed up.  You will then need to add it to your /etc/fstab...you should be able to google that easily enough.

---

### Post by Toxicity999 on 2008-01-06
They're important for any modern desktop. What swap actually is is "Virtual Memory" Essentially spillover for your ram. The OS uses its best judgement to determine what Memory data you will use the least, and puts it on the slower-than-ram swap partition. In doing this we ensure that your Memory does not fill to the brim with thing s that you may very well rarely access.

As for creating one you *really* should look in to things *before* you decide to turn them off. You still can use a disk partitioner, create a Swap partition, read up on /etc/fstab, and mount it properly, swap it on, and there you go. It would have been much easier leaving it as is from the installer though.

---

### Post by Truck449 on 2008-01-06
great info, thanks for all the help and advice guys it is greatly appreciated

---

