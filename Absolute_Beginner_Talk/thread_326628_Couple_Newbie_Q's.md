---
title: "Couple Newbie Q's"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by nar57981 on 2006-12-27
Alright, i'm ording some new parts for my computer, including a copy of windows, and i'm going to format my HDD. I also wanted to try out linux and put that in a partition a long with it. I just have a clouple questions:

1) Could i make a small partion for windows, one for ubuntu, a swap, and use the rest of my space for files/games?

2) If I can't do this what would be suggested partition sizes for a 80gig HDD?

3) If I can do this i saw that 1 gig should be for swap, 8 gigs for Linux, but how much space should i use for windows?

4) This is a really noobie question, but how do I use the extra space that i partitioned. Do I need to do anything to it after i make the initial partition?

5) Do you have a link that would show me how to make the extra partitioning? The only video/picture tutorial i've seen is with older versions, or it doesn't show making a swap partition.

6) I saw that not every wireless card will work with Ubuntu, would this one work with 6.10/6.06?
[http://www.usr.com/products/networking/wireless-product.asp?sku=USR5421](http://www.usr.com/products/networking/wireless-product.asp?sku=USR5421)

Thanks for the help!

---

### Post by punx45 on 2006-12-27
this is a good guide on jsut about every beginner topic there is:   i used it and so have many others.   it should answer most or all of your q's.

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by nar57981 on 2006-12-27
Alright, I think I understand how to do this.....
During the windows installation I make the partition for windows (NTFS), then make a partition for files (FAT32) and leave about 10gigs left.
Then when I install Ubuntu, I use the first choice, and would that use the 10 gigs that I left for it? Or would it take it off the FAT32?
Also I didn't see how big I should make windows's partition, (10 or 15 gigs?)

The third choice looks a little bit too complicated for me to mess with, but i guess i could scratch my brain to make it work if i had to....><

Also i found out that the wireless works, but I remembered my bluetooth adapter, which is:
[http://www.targus.com/us/product_details.asp?sku=ACB10US](http://www.targus.com/us/product_details.asp?sku=ACB10US)
it uses window's stack, would this still work with Ubuntu?

---

### Post by rccharles on 2006-12-28
> **nar57981 said:**
> Alright, I think I understand how to do this.....
During the windows installation I make the partition for windows (NTFS), then make a partition for files (FAT32) and leave about 10gigs left.
Then when I install Ubuntu, I use the first choice, and would that use the 10 gigs that I left for it? Or would it take it off the FAT32?
Also I didn't see how big I should make windows's partition, (10 or 15 gigs?)

The third choice looks a little bit too complicated for me to mess with, but i guess i could scratch my brain to make it work if i had to....><



I remember early XP notebooks having 10gig harddrives.  The link below suggest 16gig:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).
I'd go for the 16gig.

While you can have upto 4Tbytes FAT32 partitions and Windows XP will read and write to these partitions, Windows XP will only let you define upto 32gig FAT32 partitions.

What you can do is define a NTFS partitions of 16gig and let the rest of the space free.  Use Ubuntu to define the FAT32 partition and the Ubuntu Partition.

Note...
Note: You should install Windows before Ubuntu.

You need to install Windows first, because Windows will overwrite the Master Boot Record.

When you install Ubuntu after Windows, Ubuntu will notice that Windows is around and set up the boot loader Grub.  Grub will ask you which OS should be loaded at boot time.

As for Ubuntu, the default desktop install is about 4gig.

Robert

---

### Post by rccharles on 2006-12-28
> **nar57981 said:**
> 

4) This is a really noobie question, but how do I use the extra space that i partitioned. Do I need to do anything to it after i make the initial partition?

5) Do you have a link that would show me how to make the extra partitioning? The only video/picture tutorial i've seen is with older versions, or it doesn't show making a swap partition.


As for the NTFS partition, Ubuntu will make it read-only and allow only the system administrator to access the partition.

You need to follow the instructions in this link to gain general access to the partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I believe the same goes for Fat32.

...

The Ubuntu installation will give the option to partition the disk.  It not too bad.

You could use a live CD to install.  This will let you use a GUI partitioning tool.



Robert

---

### Post by nar57981 on 2006-12-28
> **rccharles said:**
> While you can have upto 4Tbytes FAT32 partitions and Windows XP will read and write to these partitions, Windows XP will only let you define upto 32gig FAT32 partitions.

What you can do is define a NTFS partitions of 16gig and let the rest of the space free.  Use Ubuntu to define the FAT32 partition and the Ubuntu Partition.

Robert

So when I install windows, would I only make a partition of 16gigs, and then do the 1.5gig swap, about 5 gigs of Ubuntu, and let ubuntu make a FAT32 partition for the rest of the space (about 57gigs).

Or would making a 32gig FAT32 partition, a 1.5gig swap, 5 gig Ubuntu, and use the rest for windows be better/easier? I play a lot of games, and mose of the space will be windows apps. The only thing that will probably be on this space is music and a couple videos clips.

> **rccharles said:**
> You need to follow the instructions in this link to gain general access to the partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I believe the same goes for Fat32.

Robert

So i just follow the instructions, and type in everything he does? (changing partition number for the right drive to mount)

---

### Post by rccharles on 2006-12-29
> **nar57981 said:**
> So when I install windows, would I only make a partition of 16gigs, and then do the 1.5gig swap, about 5 gigs of Ubuntu, and let ubuntu make a FAT32 partition for the rest of the space (about 57gigs).

Or would making a 32gig FAT32 partition, a 1.5gig swap, 5 gig Ubuntu, and use the rest for windows be better/easier? I play a lot of games, and mose of the space will be windows apps. The only thing that will probably be on this space is music and a couple videos clips.


I'd suggest you make a 10gig Ubuntu partition so that you do not run out of space.

You have to decide how much data and programs you will put in each partition.  From what you are saying, I'd increase the size of the Windows partition. 

Robert

---

### Post by rccharles on 2006-12-29
> **nar57981 said:**
> 
So i just follow the instructions, and type in everything he does? (changing partition number for the right drive to mount)

Yes... 

The instructions are often referenced in these forums, so they have survived the test of time.

Robert

---

