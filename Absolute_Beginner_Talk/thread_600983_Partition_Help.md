---
title: "Partition Help"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by cooper892 on 2007-11-02
I've popped in the Gusty Gibbon Live Cd, and everything has been going smoothly until...You guessed it, partitioning. I'm too scared to press anything right now. I want to dual boot with vista and I have about 12 GB of free space on an 80gb hard drive. I've gotten up to the partition window and can only choose manual and I have no clue what to do next, help!

/dev/sda
   /dev/sda1   fat16   /media/sda1   41mb        33mb
   /dev/sda2   fat16   /media/sda2   79979mb   unknown
   free space                                 8mb

---

### Post by overdrank on 2007-11-02
> **cooper892 said:**
> I've popped in the Gusty Gibbon Live Cd, and everything has been going smoothly until...You guessed it, partitioning. I'm too scared to press anything right now. I want to dual boot with vista and I have about 12 GB of free space on an 80gb hard drive. I've gotten up to the partition window and can only choose manual and I have no clue what to do next, help!

/dev/sda
   /dev/sda1   fat16   /media/sda1   41mb        33mb
   /dev/sda2   fat16   /media/sda2   79979mb   unknown
   free space                                 8mb

Hi and you say you have 12gigs free  where is that 12gigs? Is it inside your windows partition?

---

### Post by cooper892 on 2007-11-02
Yes, it's in the windows partition and I don't know how to get it out

---

### Post by overdrank on 2007-11-02
> **cooper892 said:**
> Yes, it's in the windows partition and I don't know how to get it out

Well this is my advice, I would backup my data and remove what I could to a additional source and then resize windows partition.  You stated that will only let you choose the manual partition and not the resize? There have been some users that have to resize vista from with in vista.

---

### Post by louieb on 2007-11-02
IF you only have 12 gig out of 80 left then its time to get another drive. NTFS performance drops starting at about 70% full. Your over that now. I would not try to shrink the partition not without a backup made with something like partimage or norton ghost.

---

### Post by tarchy on 2007-11-02
I also need to know..

How can I make another partition without losing any data? I want to install a dual boot :P

---

