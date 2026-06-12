---
title: "Installing Ubuntu - Prepare Partitions"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by seblep on 2007-11-22
Ok, im in the middle of my installation for a dual boot Vista and Ubuntu and when i get to 
Prepare Partitions, i create my SWAP of 800mb and then when i try to make the other partition of 10GB that changes from Free Space to Unusable, i don't know what to do! Can someone help please?!

Thank You

---

### Post by overdrank on 2007-11-22
> **seblep said:**
> Ok, im in the middle of my installation for a dual boot Vista and Ubuntu and when i get to 
Prepare Partitions, i create my SWAP of 800mb and then when i try to make the other partition of 10GB that changes from Free Space to Unusable, i don't know what to do! Can someone help please?!

Thank You

Ok you have resized vista's partition and you have free space. Could you explain a little more about what you mean unusable space?

---

### Post by seblep on 2007-11-22
Ok so i have my "Prepare Partitions" screen and i do the first step on the Free Space which in total is 11GB so once i do my Swap Partition of about 1GB i am left with 10GB but it shows up as unusable space instead of free space, so i cant click on it to creat my ext partition.

I tried doing my swap first and i also tried doing my ext first none of these work the remain space after doing on or the other appears as unusable space.

---

### Post by backflip on 2007-11-22
I had the same problem and it was caused by having a tick in the primary partition option when I created the swap file partition. Just make sure that it isn't ticked. That MAY be the cause of your problem.

---

### Post by seblep on 2007-11-22
Alright so we do not set is as primary right, because yes it was ticked so if it has to be not ticked ( which means not primary) then i have my solution, ill try and get back to you! THANK YOU AGAIN FOR THE QUICKNESSS!!!

---

### Post by meindian523 on 2007-11-23
Looking at the responses,I would say you had that problem because you reached your primary partition limit of 4.........you could create an extended partition of 11 GB and THEN make your swap and ext3 partition within it......Linux doesn't require to have a primary partition to be bootable,just make sure that your / partition is within the space which can be accessed by your BIOS......

---

