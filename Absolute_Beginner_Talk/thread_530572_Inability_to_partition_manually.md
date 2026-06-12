---
title: "Inability to partition manually"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by doktarr on 2007-08-20
Hi all,

I've had some bizarre issues trying to partition my hard drive on a fresh install.

I have a 750GB WD hard drive.  My goal was to divide this hard drive into ext3/swap/xfs, as described in this guide:
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop) 
My plan was 100 GB ext3, 12.5 GB swap, and the rest xfs.  The first two parts of that went off without a hitch.

However, any time I tried to make a partition greater than 200 GB, I received an error message and was told I was placing the end before the beginning.  Also, once I cracked roughly 500 GB total, the remaining space (250 GB or so) went from "free space" to "unusable".

Eventually I threw up my hands and went with a guided partition, which had no problems creating a 730 GB ext3 partition.  This is acceptable but not ideal.  I would gladly re-install and repartition the drive if somebody thinks they know the solution to my problem.

---

### Post by Hobo Joe on 2007-08-20
> **doktarr said:**
> Hi all,

I've had some bizarre issues trying to partition my hard drive on a fresh install.

I have a 750GB WD hard drive.  My goal was to divide this hard drive into ext3/swap/xfs, as described in this guide:
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop) 
My plan was 100 GB ext3, 12.5 GB swap, and the rest xfs.  The first two parts of that went off without a hitch.

However, any time I tried to make a partition greater than 200 GB, I received an error message and was told I was placing the end before the beginning.  Also, once I cracked roughly 500 GB total, the remaining space (250 GB or so) went from "free space" to "unusable".

Eventually I threw up my hands and went with a guided partition, which had no problems creating a 730 GB ext3 partition.  This is acceptable but not ideal.  I would gladly re-install and repartition the drive if somebody thinks they know the solution to my problem.

I know this is not an answer to your problem, but you do NOT need a swap that big. 2GB is all you need at the biggest. 1 GB is more than enough.

---

### Post by doktarr on 2007-08-20
> **Hobo Joe said:**
> I know this is not an answer to your problem, but you do NOT need a swap that big. 2GB is all you need at the biggest. 1 GB is more than enough.Is that true even if I have 4GB of memory?

Thanks for the quick response to my other question BTW.  That makes perfect sense.

---

### Post by Hobo Joe on 2007-08-20
> **doktarr said:**
> Is that true even if I have 4GB of memory?

Thanks for the quick response to my other question BTW.  That makes perfect sense.

Yes, they say it should be twice the size of your memory, but the only reason they say that is so that you don't run out.(swap is what takes over if your RAM if full), even if you only have 2GB of memory you don't need more than 1GB swap, unless for some reason you happen to have more than 3GB of stuff that needs to be stored on ram, or, in your case, **16.5GB** of stuff. :P

---

### Post by jdfreshwater on 2007-08-20
I think the problem is trying to do more then 2 partitions.  I ran into this problem when installing feisty.  I believe I solved it by using gparted by itself and committing to a 2 partion disc, and then repartitioning again.  You may be able to resize your partition at this point using something like gparted to resize and reformat your existing partitions.

---

### Post by schorsch on 2007-08-20
o.k. you will need a swap partition that is a little bit larger as your memory when you want to hibernate on a laptop ..... but as I do not know a laptop with a 750GB HD I would guess you are on a desktop system, right? Then you will be alright with a 2 GB swap partition unless you want run a SAP system on your computer .. :-)

---

### Post by doktarr on 2007-08-20
schorsch, yes, this is supposed to be a HTPC running MythTV.
> **jdfreshwater said:**
> I think the problem is trying to do more then 2 partitions.  I ran into this problem when installing feisty.  
I could test this theory by seeing if I can create a 100 GB ext3 partition and a 650 GB swap (and you guys thought 12.5 GB was too big! ;))
> **jdfreshwater said:**
> I believe I solved it by using gparted by itself and committing to a 2 partion disc, and then repartitioning again.  You may be able to resize your partition at this point using something like gparted to resize and reformat your existing partitions.
Thanks for the link; I will give gparted a try.  I'm a bit confused by your explanation though - do you mean that you set up a 2 partition disc using ubuntu's graphical installer, and then repartitioned after that using gparted?

---

### Post by doktarr on 2007-08-27
Just to follow up - gparted successfully set up the partitions the way I wanted them.  I then reinstalled ubuntu, including reformatting the drives, just to be safe.  The ubuntu installer had no problem working with the partitions that had already been set up by gparted.

Thanks for the help.

---

