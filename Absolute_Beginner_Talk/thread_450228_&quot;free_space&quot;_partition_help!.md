---
title: "&quot;free space&quot; partition help!"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Travis_D on 2007-05-21
Hello,

I would like to set up a dual boot option with XP and Ubuntu. I partitioned my hard drive and left a little over 20GB for Ubuntu. I would like to use this partition:

[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]

However, when I tried making a partition /home of 14GB (and planning on / of 4+ GB and SWAP of 2GB) I was successful in making the 14 gig ext3 drive but then the rest of my free space then was labeled "unusable." I tried reading as much as I could find but am still confused -- am I doing something wrong here?

Thank you!

---

### Post by mikewhatever on 2007-05-21
Are there more partitions on the HDD already, such as Windows recovery or/and Windows storage? If so, you can not have more then 4 primary partitions and will have to install Ubuntu on and extended one.

---

### Post by heimo on 2007-05-21
> **Travis_D said:**
> 

[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.png[/IMG]



Are those partitions all that you have / plan to have on the disk? What I'm after is: You can only create four primary partitions on a disk. If you want to create more, make three primary partitions and extended partition out of the rest - then create logical partitions to the extended partition.

Of course, if you only have those two partitions already, you should be able to just create 3rd and 4th partitions (for Ubuntu root / and swap) as primary partitions.

---

### Post by viciouslime on 2007-05-21
Also, except in exceptional circumstances, there is no way you need 2gb of swap. I would suggest 512mb, 1gb if you REALLY want it, but that is probably overkill. IT sounds like you're a little short of space if that largest partition is going to be 14gb so this will give you a little bit extra :)

I can't think of any reason for the problem you're having though other than those already mentioned on here...

---

### Post by Travis_D on 2007-05-21
I guess my problem is the fact that there are already partitions for Windows recovery and one other tiny one for something else. I was just using that picture as a model, I'm still keeping 35GB for NTFS. Whatever I'd need to do to consolidate to bring the number of partitions down to four might be too advanced, I'll have to stick to just Windows.

If, instead of partitioning manually, I were to select the option to let Ubuntu install on the largest continuous free space, would I be able to use that and have it formatted in ext3 and use that program available for Windows that allows it to read and write to ext 3?

---

### Post by Nekiruhs on 2007-05-21
> **viciouslime said:**
> Also, except in exceptional circumstances, there is no way you need 2gb of swap. I would suggest 512mb, 1gb if you REALLY want it, but that is probably overkill.
Really? I have like, 6 gigs of swap. ROFLMAO. I had 2gb ram and a 250 GB hd, so i thought why not and went for 3x.

---

### Post by Pisi-Deff on 2007-05-21
And how many percent of those 6GB are maximally in use? 1%? 2%? Maybe 5%?

---

### Post by Nekiruhs on 2007-05-21
> **Pisi-Deff said:**
> And how many percent of those 6GB are maximally in use? 1%? 2%? Maybe 5%?
Well, right now, im listening to music, Beryl is going like crazy, editing a word doc, browsing the web, and using GIMP and its at a record high of 0% in use and my RAM is at like 33%, 22% of which is cache.

---

### Post by comer on 2008-07-09
I google partition manager find some freeware bellow:

paragon  [http://www.paragon-software.com](http://www.paragon-software.com)
I have not used,no comment!

easeus partition manager 
I download from brother soft 
[http://www.brothersoft.com/easeus-partition-manager-51814.html](http://www.brothersoft.com/easeus-partition-manager-51814.html)

It worked OK, but failed when i tried to  merge partition. so i have to allocated the free space to another partition. Partition magic may merge two partitions which will cost you $69.95

cute partition manager
[http://www.giveawayoftheday.com/freeware/partition_download.shtml](http://www.giveawayoftheday.com/freeware/partition_download.shtml)

---

