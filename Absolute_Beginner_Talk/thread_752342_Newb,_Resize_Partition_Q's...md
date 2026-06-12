---
title: "Newb, Resize Partition Q's.."
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by latda13 on 2008-04-11
Hi,
 I apologize if this has been asked alot or is in the wrong area.
I did search and read as much as I could before finally turning to you, the pro's who will hopefully get me going in the right direction and 'unfrustrate' me :)

So far I cannot install Ubuntu, version 7.1. I have a verified iso burnt to disk..
I'm running XP & would love to wipe the partition which I want to install Ubuntu- to 
but I'm afraid I'd be stuck w/out internet access then ..

My HDD is 160 GB with a primary partition of 72+ GB which has XP on it and an 80 GB partition (D:/ Storage) used just for storage..

I have **4 GB (3.2 gb) of Ram** and dual 2.8 processors. I know the Ram could be an issue in and of itself...but amyways;

My problem: I start to install Ubuntu, get to the HD partition phase and cannot proceed/figure out what to do from here..
I've tried guided, manual, etc and can't get it to cooperate???

Any help please? I really can't wait to explore Linux in this environment :D
Thanks in advance

Mike

---

### Post by prshah on 2008-04-11
> **latda13 said:**
> 
My HDD is 160 GB with a primary partition of 72+ GB which has XP on it and an 80 GB partition (D:/ Storage) used just for storage..

My problem: I start to install Ubuntu, get to the HD partition phase and cannot proceed/figure out what to do from here..


If yu have about 20Gb free space in your storage, you can easily install ubuntu and enjoy it. You dont NEED 20 Gb but it's more fun if you have it. If you don't move some stuff from the storage partition to your other partition.

Then defrag your d:. Don't bother with c: we won't be touching it.

Boot into the live CD, come to the partitioning part. "Shrink/Resize" your d: partition (it'll probably be sda2 _or_ sda5- DONT fiddle with sda1).

After the shrinking process: 

if you _dont_ already have an sda5, create an "extended" disk partition of size 20Gb (or how much ever free space it shows avail). If you already _have_ an sda5, you can ignore this step.

Then create a new "logical" drive in the free space and give it size 10Gb and in "mount point" enter "/".

Then create ANOTHER "logical drive" in the free (remaining) space and give it a size of 2Gb, type as "swap" and no mount point.

Then create YET ANOTHER "logical drive" in the free space and give it size 8Gb (or total remaining space) and in "mount point" give "/home".

Once you finish everything, take a final check before clicking "Apply"

From this point on, it's smooth sailing!


Then

---

### Post by wolfen69 on 2008-04-11
> I've tried guided, manual, etc and can't get it to cooperate???
what exactly is happening/not happening at this point of the install? what do you mean by not cooperating? can you click the forward button?

---

### Post by Kevanx on 2008-04-11
Hey, are you using gparted?

I'm not an expert - only did this once, myself. Essentially, the hardest part is figuring out how you want to divide the remaning space. gparted is really straightforward, once you know what ext3/fat/ntfs is, and how to label each drive.

There are a ton of partioning tutorials out there (use google rather than these forums).
Bascially, IMO, the best way to do it is to divide your remaining space like such.
1) FAT32 shared drive so that you can share your documents between Linux & Windows, because windows can't read from EXT3 formatted drives, and Linux can read but not run on NTFS (I think).
2) EXT3 Home folder partion (essentially the linux documents and settings folder, so keep it fairly large).
3) A SWAP partion. I've heard varying info around the size.
4) The main bootable EXT3 partition for the OS itself. This should be the largest partition.

In terms of sizes, I would say probably
1) 30% of the space
2) 20-25% of the space
3) 5-10% of the space (probably less, though)
4) 40% of the space

If you google partition linux how-to, you should get some much clearer explanations about sizing, and what each drive is for.
eg: [https://answers.launchpad.net/ubuntu/+question/2910](https://answers.launchpad.net/ubuntu/+question/2910)

---

### Post by Oldsoldier2003 on 2008-04-11
> **latda13 said:**
> Hi,
 I apologize if this has been asked alot or is in the wrong area.
I did search and read as much as I could before finally turning to you, the pro's who will hopefully get me going in the right direction and 'unfrustrate' me :)

So far I cannot install Ubuntu, version 7.1. I have a verified iso burnt to disk..
I'm running XP & would love to wipe the partition which I want to install Ubuntu- to 
but I'm afraid I'd be stuck w/out internet access then ..

My HDD is 160 GB with a primary partition of 72+ GB which has XP on it and an 80 GB partition (D:/ Storage) used just for storage..

I have **4 GB (3.2 gb) of Ram** and dual 2.8 processors. I know the Ram could be an issue in and of itself...but amyways;

My problem: I start to install Ubuntu, get to the HD partition phase and cannot proceed/figure out what to do from here..
I've tried guided, manual, etc and can't get it to cooperate???

Any help please? I really can't wait to explore Linux in this environment :D
Thanks in advance

Mike

Mike, This may seem a little advanced but this is what i would do.
First I would backup all my data :)
then download the [GParted Live CD]("http://gparted-livecd.tuxfamily.org/") and burn it
After you do that go ahead and scandisk and defrag your windows partitions

Next boot from the Gparted Live CD and resize your data partition to make room for a Ubuntu install. leave the unallocated space as unallocated. 30GB should be way more than enough to evaluate Ubuntu safely.

When you install Ubuntu tell it to use the unallocated space. What this will do is give you a dual boot system allowing you to evaluate Ubuntu without removing windows. 

Once you are satisfied that you are ready to go windows free you can always remove the windows partitions and use gparted to grow your linux partitions, or you could re partition and set your system up from scratch.

---

### Post by phidia on 2008-04-11
What errors are you getting? "can't get it to cooperate" doesn't provide the specifics people will need to help you troubleshoot this.
Linux/Ubuntu will require formatted ext3 and a swap partitions so that it will install.
You need to select the "/" mount point for the install partition, but without knowing exactly what messages or responses you are seeing I can't offer much more than that.
There are community install guides [here]("https://help.ubuntu.com/community/Installation"). Hope that helps.

---

### Post by spydon on 2008-04-11
> **Oldsoldier2003 said:**
> 
Next boot from the Gparted Live CD and resize your data partition to make room for a Ubuntu install. leave the unallocated space as unallocated. 30GB should be way more than enough to evaluate Ubuntu safely.
Why not just use the gparted that's already on the Ubuntu live cd??:confused:

---

### Post by latda13 on 2008-04-11
> **spydon said:**
> Why not just use the gparted that's already on the Ubuntu live cd??:confused:

I've tried gparted..

anyway, there isn't a whole lot of info once I can't continue.
There's a red "do not enter" sign and it says it cannot continue (I'm not doing something right obviously at this point"..

Thanks RSRhah! That looks like a very viable solution, I'll give that a try :)
Thanks all to your replies, I'll post an update after I try..
and any further info if I can.. at that point, if needed ;)

---

