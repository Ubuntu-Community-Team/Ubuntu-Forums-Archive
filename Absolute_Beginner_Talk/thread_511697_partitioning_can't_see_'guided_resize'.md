---
title: "partitioning: can't see 'guided resize'"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by grainbarcelona on 2007-07-28
Ubuntu friends,

I am new to Ubuntu, but exited to give it a try. 

I would like to set up a dual boot with Ubuntu & Windows XP. (currently I have only Windows XP occupying some 40 gigs of the 180 gig hard disk

So I run the Live Disk, got myself into the installation process, but at the point of deciding on how to do the partitioning, Ubuntu gives me only two options: 'guided - entire disk' and 'manual'. I understand from various posts on this forum, that there should be a third option called: 'Guided - resize', which would give me the dual boot automatically.

What did I do wrong? Why is the 'guided resize' not one of the options? What should I do? (I already did defragment the disk several times with Windows, as suggested by several on this forum)

Thanks for anyone who can shed some light on this.

---

### Post by jingo811 on 2007-07-28
There's only 2 options
[LIST]
[*]guided - entire disk' 
[*]'manual'.
[/LIST]

You want Dual Boot bub choose manual I did.  Also check out the links in my signature especially the aysiu one to educate and prepare yourself for the ride.


> Why is the 'guided resize' not one of the options? 
Hmm I checked out aysius Dual Boot guide he uses Ubuntu version 6.06 and 6.10 as an example that's why there's such an option.
I use Ubuntu 7.04 Feisty Fawn it only got 2 options and the manual one is good enough for me.

---

### Post by jingo811 on 2007-07-28
Just don't mess with the partitions with filesystem types 
[LIST]
[*]FAT, 
[*]VFAT, 
[*]FAT32, 
[*]NTFS
[/LIST]
and you won't wreck your Windows partition.

The rest of the free disk space you can wreck and experiment all you want.  Just follow my filesystem type advice and you'll be on your way.
By the way [COLOR="Red"]BACKUP ALL YOUR PERSONAL DATA[/COLOR], install Ubuntu with the mindset that you're going to wreck your entire PC.  If the **** hits the fan you'll have your PERSONAL DATA secured on discs.

---

### Post by az on 2007-07-28
There should be the third option.  It was not removed in Ubuntu 7.04.  If it is not shown, it's because the partitioner does not think that it is possible.  If the problem is not lack of room on the current windows partition, it may be due to fragmentation.  Another reason would be that the partition table is not perfect.  Had you ever partitioned your disk before?

You should not have to do manual partitioning to install Ubuntu.

You can try to pick manual partitioning and simply shrink your windows partition down, then click "go back".  You should then get a "use free space" option and let guided partitioning use that.

---

### Post by grainbarcelona on 2007-07-28
Thanks, Jingo,

I'm a bit nervous about this manual partitioning, so I'm going to ask you advise (or anyone else who knows about this). When I click manual partitioning, it gives me the following info:

sda1 fat12, 65 MB, used 33 MB
sda2 nlfs 156 gig, used 43 gig
sda3 fat32, 3 gig, used 2.5 gig

So, where do I put Ubuntu? Add a new partition, or modify one of the abovy? As what? And where do I the space from, by reducing the size of the nlfs partition? But don't I mess up Windows then?

One more question: once I finalize the partition stuff & the rest of the installation process, do I then get autmatically a boot up screen asking me to choose between windows and ubuntu? Or do have have to do something special for that?

Sorry, but I really don't know what to do.  Any help appreciated

---

### Post by grainbarcelona on 2007-07-28
Thanks very much AZ,

I'll try that also. I already wondered why the automatic option was removed from 7.04. Looked strange to me. Thanks so much for all your help.

---

### Post by jingo811 on 2007-07-28
Hmm there's so much to explain when it comes to partitioning and installing for the first time....it took me 12 pages to write such an incomplete tutorial.  Not counting all the important screenshots.  

IF {

I am to instruct you I'd prefer that you can afford to wipe out the entire hard drive and that you also have these 2 installation CD s at home.
[LIST]
[*]Window XP installation CD
[*]Ubuntu Desktop LiveCD (Feisty)
[/LIST]

} ELSE {

I'd advise you to read aysius Dual Boot process instead
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

}

So I can finish coding my tutorial during next week and put it up on my homepage so that I can explain this topic my way better.

---

### Post by gusanto on 2007-07-28
I have Windows XP and Ubuntu Feisty on my desktop.
I followed a note somewhere (I forgot where) to create two partitions: ext3 and linux swap. Then I have 4 primary partitions. I still have unallocated space on my HD and I want to create another partition that both Ubuntu and Windows can have access (I read about partition with FAT32 file system).
When I tried to create an extended partition with GParted, the following message appeared:.
"It is not possible to create more than 4 primary partitions. If you want more partition you should first create an extended partition. Such partition can contain other partitions. Because an an extended partiton is also a primary partition, it might be necessary to remove a primary partition first."
If the only way to create a new partition is by removing one of the available partitions, can I remove a Linux swap partition then create it again later? But if I deleted Linux swap partition, and then create an extended partition, will I be able to create a Linux swap partition again because there are already 3 primary partitions and 1 extended partition (which is also considered as primary partition; as I understood form the GParted message above).
Please give me advise.
Many thanks.

---

### Post by trucker33377 on 2007-07-28
if you dont get the slider then you cant put both on this HD you must see that slider ive seen alot of post where ppl asked what happened to windows. it happened to me i had a 40 gig HD

---

