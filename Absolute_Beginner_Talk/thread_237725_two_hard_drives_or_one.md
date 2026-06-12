---
title: "two hard drives or one?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-08-16
When I had windows xp installed on this computer (an Acer 5004WLMi Aspire) I had two hard drives ('c' and 'd') each about 40 gigs each. When I deleted Windows xp and installed ubuntu, I just have one 80 gig drive. My question is: Is there anyway to divide this one drive into two separate ones? Also, did I never have two hard drives in the first place? Did I just have one drive that had been partitioned to create two separate ares? Is it better to divide my hard drive into two separate partitions/folders???

---

### Post by ComplexNumber on 2006-08-16
> When I had windows xp installed on this computer (an Acer 5004WLMi Aspire) I had two hard drives ('c' and 'd') each about 40 gigs each. they're virtual drives....not physical drives.
> 

Also, did I never have two hard drives in the first place? thats correct.

> 
Is it better to divide my hard drive into two separate partitions/folders???
it depends what you want to do.

---

### Post by daou on 2006-08-16
You can install a program called GParted in Ubuntu. That will let you partition the drive into sections if this is what you want to do. When you installed Ubuntu, you probably let it partition the hard drive by itself. Most likely it has already split the drive into two parts (Ubuntu system and the swap-partition which is small).

It would be very smart to partition the drive especially if you have important files like pics, documents, music, etc. These you want to place in the new partition so if you ever need to reinstall Ubuntu, you won't lose the files during formatting.

---

### Post by ComplexNumber on 2006-08-16
further to what daou has already said, i'm going to assume that you don't already have ubuntu installed. 
if you are intending to have ubuntu and windows to be installed, then i imagine that the whole of the 80GB is either fat32 or ntfs. this partition will need to be resized to allow ubuntu to fit on because windows and linux use 2 different filesystems.  resize windows down to (say) 40GB using the ubuntu live cd, then partition ubuntu as follows:

-root partition (mount point = '/') = about 20GB (this will be more than enough)
-home partiton (mount point = '/home') = about 5-20GB
-swap partition = (duaually) double the amount of RAM you have. if you have more than 256MB of RAM, just make the size of the swap partition to equal the size of the amount of RAM you have.


its important that you have a home partition because this allows you to keep you settings and files etc, and it acts as a sort of permanant storage location inbetween installs.

also, use the ext3 filesystem for both your root and your home partiton.

---

