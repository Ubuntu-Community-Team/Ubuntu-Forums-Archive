---
title: "Dual-Boot Partition Help"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by bmh2005 on 2007-09-11
Hello, I am new to the Ubuntu OS. I was trying to install it from thr Live CD and I go to the point where I select Manual partitioning. After that I looked at the biggest partition (NTFS) and I edited it and went to the size and dropped it down about 10 GB's. Then that created 10Gbs of free space, I then made that into a partition by selesctin the ext3 and then the '/' on the bottom option. (not sure if I selected the right options). I left it on primary and beginning options also. I only made that partition into 8 GB's so I could use the remaining 2 GBs for the Swap partition. Now here is my problem when i see the 2 GB's of free space, it says it is unusable. Can anyone help me through this step? Thanks!

---

### Post by BrendanM on 2007-09-11
Hmm, that is kind of strange. Maybe it's unusable because it hasn't been formatted yet? You'll have to format it as "Linux SWAP".

---

### Post by gn2 on 2007-09-11
> **bmh2005 said:**
>  I left it on primary and beginning options also. I only made that partition into 8 GB's so I could use the remaining 2 GBs for the Swap partition. Now here is my problem when i see the 2 GB's of free space, it says it is unusable. Can anyone help me through this step? Thanks!

The 8gb partition doesn't have to be primary, neither does the swap partition. 
It's unlikely you'll need 2gb for swap, I find 512mb-1gb is usually enough.

Have a good read through the Hermanzone link in my sig for all the info you'll ever need on this subject.

---

### Post by smokey_58au on 2007-09-12
I was having the same problem.  Changed my new partitions to Logical instead of Primary and it worked fine.

---

### Post by indytim on 2007-09-12
Did you specify the remaining 2 G of space as the swap?  Also, when you identify the "/" partition, make sure you "check" the format checkbox.  May have to do the same with the swap - not 100% sure on that one.

IndyTim

---

### Post by oddin85 on 2007-09-12
I don't know if it'll help but i know that you can have 4 primary partitions maximum
all logical partitions are made under 1 primary partition of file type extended, that's how you can have more than 4 partitions on a drive

---

### Post by bmh2005 on 2007-09-13
All I did was change it to logical and it worked. Thanks for the advice everyone!

---

