---
title: "Partitioning Help!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by kiroro on 2008-01-15
I am in the process of installing Ubuntu and having a partition problem. I have a 400G HDD. I installed windows XP on it at the beginning and left 30G unallocated disk space for Ubuntu. But I only created one partition C: for XP. Then I used Patition Magic to resize C: to 2 more partitions. Now in the Ubuntu partition process, I have /dev/sda1, /dev/sda5, /dev/sda6 as NTFS partitions. I want to create 3 partitions using the 30G for Ubuntu. Problem is: after I created two partitions, which are /dev/sda3 and /dev/sda4, the rest of the space is unusable?? I think the dev number is messed up. How can I solve this problem? Thanks a lot!

---

### Post by mikewhatever on 2008-01-16
You must have created 4 primary partitions, which is the max number of that type per disk. Delete one of them, create a big extended partition, and then create a number of logical ones.

---

### Post by kiroro on 2008-01-16
Does the / partitoin have to be primary? I guess I will have to double check my windows partitions using partition magic.

---

### Post by kiroro on 2008-01-16
I just checked my windows partition. I only have 2 primary partitions. I did create a big extended partition and then two logical ones. I just don't understand why I have sda5 and sda6 instead of sda2 or sda3 for my current partitions...

---

### Post by mikewhatever on 2008-01-16
> **kiroro said:**
> I just checked my windows partition. I only have 2 primary partitions. I did create a big extended partition and then two logical ones. I just don't understand why I have sda5 and sda6 instead of sda2 or sda3 for my current partitions...

I don't know, but that does not seems to be a problem. Perhaps sda2,3 are reserve d for more primary partitions. Anyway, I thought the problem was that part of the free space was unusable. Is that so?
It does not matter whether root is primary or logical, can be any.

---

### Post by meindian523 on 2008-01-16
sda 1,2,3,4 are reserved for primary partitions,if you create an extended,it will be allotted one of these numbers and any logical partitions inside will start from sda5,sda6 and so on.

---

### Post by kiroro on 2008-01-16
> **mikewhatever said:**
> I don't know, but that does not seems to be a problem. Perhaps sda2,3 are reserve d for more primary partitions. Anyway, I thought the problem was that part of the free space was unusable. Is that so?
It does not matter whether root is primary or logical, can be any.

Right. I tried some more. 

If I create / as primary partition as I did before, it will appear as /dev/sda3, and when I create /home, it does not give me the choice to set it primary or logical, and automatically appear as /dev/sda4. then the rest would be unusable. If I create swap as next instead of /home, it will still be unusable after swap..

But If I create / as logical, it will appear as /dev/sda7, then /home will be /dev/sda8, and then I could create swap. This seems to work. I thought OS better be on the primary partition? Can you confirm that it does not matter?

---

### Post by kiroro on 2008-01-16
> **meindian523 said:**
> sda 1,2,3,4 are reserved for primary partitions,if you create an extended,it will be allotted one of these numbers and any logical partitions inside will start from sda5,sda6 and so on.

So I should stop messing the primary partition and set / as logical? It would be sda7. What is your suggestion?

---

### Post by bernied on 2008-01-16
> **kiroro said:**
> I thought OS better be on the primary partition? Can you confirm that it does not matter?This is true of some OSes, but not true of modern linux. I run kubuntu from a logical partition, it doesn't care. Same for swap, doesn't matter.

---

### Post by kiroro on 2008-01-16
Thank all of you guys! I think I'll just make all the linux partitions logical.

---

### Post by meindian523 on 2008-01-17
No problem with logical linux partitions,am running Ubuntu on a logical right now.

---

