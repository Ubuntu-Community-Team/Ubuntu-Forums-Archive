---
title: "Swap Question"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by AmbigFish on 2007-05-25
Ok guys. I have Ubuntu installed with a dual boot of XP Pro and Ubuntu 7.04. I have my primary partition limit maxed (4). They are, 1 for XP, 1 For Ubuntu, 1 For Swap, and 1 for XP Recovery (it's a laptop). Well, I want to create another one, so I have to nix one of the primary partitions. I was thinking about making my swap partition an extended partition. I was wondering if this is possible. I have 2 gigs of RAM, so I made my swap a 1 gig partition. Can I reformat it as an extended partition and still be fine?

---

### Post by apunc1 on 2007-05-25
i don't think so. can you afford to resize an existing ext3 or nfts partition and use the freed space for an extended partition to allow for more logical partitions inside it? that's how you can have more than four partitions. what do you plan to do with this new partition?

---

### Post by starcraft.man on 2007-05-25
> **AmbigFish said:**
> Ok guys. I have Ubuntu installed with a dual boot of XP Pro and Ubuntu 7.04. I have my primary partition limit maxed (4). They are, 1 for XP, 1 For Ubuntu, 1 For Swap, and 1 for XP Recovery (it's a laptop). Well, I want to create another one, so I have to nix one of the primary partitions. I was thinking about making my swap partition an extended partition. I was wondering if this is possible. I have 2 gigs of RAM, so I made my swap a 1 gig partition. Can I reformat it as an extended partition and still be fine?

Yup, you can easily make the swap partition an extended logical partition. It doesn't need to be bootable at all its just like page file in windows, extra space for run off from ram. I even think the Ubuntu partition can be extended but not certain, someone was saying that in last thread I posted about partitions a while ago.

[Use GParted live cd.]("http://gparted.sourceforge.net/livecd.php") Will let you edit partitions and resize/move them around. Please read the documentation, should just be able to delete it and make a new one in extended. I don't think it needs mounting, ubuntu just finds it at boot I think >.>.

Edit: Why not apunc?

---

### Post by apunc1 on 2007-05-25
> **starcraft.man said:**
> 

Edit: Why not apunc?

i re-read the post and i guess i misunderstood. i just wondered why the op picked swap and not another? i guess to avoid resizing?

---

### Post by starcraft.man on 2007-05-25
> **apunc1 said:**
> i re-read the post and i guess i misunderstood. i just wondered why the op picked swap and not another? i guess to avoid resizing?

I dunno, maybe he has extra space left on the drive and just has maxed the primary partitions out? Do remember OP that if you only put 1 GB into the extended partition you will have to resize later if you want to make another partition and shunt more space into the extended one with gparted again, keep it handy :).

---

### Post by apunc1 on 2007-05-25
swap can be in the extended partition. sorry for my error. 
[http://www.mepis.org/node/9188](http://www.mepis.org/node/9188)

---

### Post by AmbigFish on 2007-05-25
Thanks. That is great news.

I plan on putting another OS on the computer (it's a Windows based OS). So I needed another Primary partition.

---

### Post by apunc1 on 2007-05-25
> **AmbigFish said:**
> Thanks. That is great news.

I plan on putting another OS on the computer (it's a Windows based OS). So I needed another Primary partition.

ah. ok that makes sense. good luck.
you need two versions of windows? not a technical question...i'm just being nosey:p

---

### Post by AmbigFish on 2007-05-25
I'm loading Longhorn Reloaded.;)

---

### Post by AmbigFish on 2007-05-25
It's not letting me do more then 4 partitions at all. If I format the swap as an extended partition, and then split my Linux partition up, I right click on it and go to new, and I get an error message. How do I do this? It's not allowing me to do anything. I've tried restarting, and nothing.

---

### Post by drowner on 2007-05-25
Do you have any spare space?

You may need to resize one of the partitions first.

---

### Post by AmbigFish on 2007-05-25
Right now I split my Linux partition and got rid of my Swap (for now). I'm going to try it once more.

When I right click on the unallocated space and click new, I can either create it as a Primary Partition or an Extended partition.

So, I select extended (this is for my swap) and hit add. I still have a gig of unallocated space underneith the extended partition. So, I select new, and all I can do is select logical partition. So I set it up as a swap and hit add.

I then select the rest of the unallocated space and select new, and I get the error message.

Does creating an extended partition take up one of my Primary partition slots?

If so, do you think I can get by without a swap? I never have used over 512 megs of my RAM (I have 2 gigs). It usually hovers below 256 (with Beryl running) and firefox. I only use it for word processing and internet.

---

### Post by AmbigFish on 2007-05-25
Apparently setting up an extended partition takes up 1 Primary partiton slot. Is there a way I can put my Ubuntu partition under the extended partition without reformatting?

---

### Post by AmbigFish on 2007-05-25
I've read about creating a swap file. What do you guys think about this? Will it allow me to nix my swap partition? Please, help.

---

### Post by apunc1 on 2007-05-26
> **AmbigFish said:**
> I've read about creating a swap file. What do you guys think about this? Will it allow me to nix my swap partition? Please, help.

from wikipedia
> Swapping in the Linux and BSD operating systems

In the Linux and BSD operating systems, it is common to use a whole partition of a hard disk for swapping. Though it is still possible to use a swap file instead, it is recommended to use a separate partition because this excludes chances of file system fragmentation which would reduce performance. Also, by using a separate swap partition, it can be guaranteed that the swap region is located at the fastest location of the disk which is generally the center cylinders between the inner and outer edges of the disk (except for disks with fixed heads). However with the 2.6 Linux kernel, swap files are just as fast as swap partitions. As such, this recommendation doesn't apply much to current Linux systems and the flexibility of swap files can outweigh those of partitions, and since modern high capacity hard drives can remap physical sectors, there is no guarantee that a partition will be contiguous, and even if it were, having the swap data near the rest of the data will reduce seek times when swapping was needed, so the aforementioned performance claims probably do not apply to modern Linux systems.

---

### Post by apunc1 on 2007-05-26
you can give the swap file a try, though i have no idea who to create one. you're going to have to do some research on swap files.

i still think you should be able to make some some for your extended partition by resizing a partiton and making some free space, but since you'll need that extra partition for longhorn, i'm not sure how to do it since it may need to go on its own primary partition. you'll need to move a lot of things around, and i'm not sure how to do that with your current setup. maybe someone else with more partitioning experience can help. 

good luck.

---

