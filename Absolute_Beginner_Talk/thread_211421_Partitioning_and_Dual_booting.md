---
title: "Partitioning and Dual booting"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by sturmdogg on 2006-07-08
Ok, so I have a 40gb hdd. I created a windows partition, and left the rest unpartitioned.

After reading the guides on how to dual boot my computer, it is my understanding that I have to do the following:

1. Create 2 partitions on the unused partition, 1 for the OS and one for the linux swap.
2. Reboot.
3. Install Ubuntu on the second OS partition.

Am I correct? So basically the HDD will have 3 partitions ( WinXP, Ubuntu, Linux-swap)?

Thanks!

---

### Post by atoponce on 2006-07-08
Yeah.  You have it right, however, the disc partitioner will automatically take care of most of it for you.  You just pay attention to what you want installed, and it will take care of the rest.

---

### Post by Spleenie on 2006-07-08
> **sturmdogg said:**
> Ok, so I have a 40gb hdd. I created a windows partition, and left the rest unpartitioned.

After reading the guides on how to dual boot my computer, it is my understanding that I have to do the following:

1. Create 2 partitions on the unused partition, 1 for the OS and one for the linux swap.
2. Reboot.
3. Install Ubuntu on the second OS partition.

Am I correct? So basically the HDD will have 3 partitions ( WinXP, Ubuntu, Linux-swap)?

Thanks!

Have you actually got windows installed on the windows partition yet? If you do then yep just boot up with the ubuntu cd and create two partitions (at least) when you are asked to in the free space. 

Keep in mind you don't have to create the partitions for ubuntu before you  boot into the ubuntu installer. You are given the opportunity to partition within the installer. You can start with X Gig windows and 40 - X Gig free  space on the HDD. Then reboot and play with the available space :)

---

### Post by sturmdogg on 2006-07-08
Ok...thanks guys...managed to install ubuntu...now my laptop's dual  booting...woot!

---

### Post by lightsped on 2006-07-08
I have a 40 gig drive with 1 partition.  The partition formatted with NTFS file system.  There are 28 gigs free.

I can just boot up with the Unbuntu 6.06 CD and it will allow me to repartition the drive to create a Linux OS partition and swap partition?

Thanks in advance for the clarification.  

I'm in the process of downloading the OS right now and can't wait to try it out.

---

### Post by catlett on 2006-07-08
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html) Follow this guide. It will show you the install process. 
You will come to a part where it will offer you to resize your current partition and use free space.

---

