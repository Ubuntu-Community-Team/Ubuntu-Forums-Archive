---
title: "How many partitions and what sizes?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-12-15
Hi,
Having recently made a mess of my laptop by not allocating enough size to partitions; I have decided that this time I will go with somebody elses, more experieced opinions!

I have been searching everywhere for a concrete answer as to how many partitions I should have, and what sizes.

I have an 80gb hd and 512 ram. 
I think a gig should be enough swop space but could anybody please point me in the direction of a good howto or describe how they would set up their partitions?!

I use my box averagely, browsing and watching media but I mostly store on a 60gb external. Soon I will have a new box with 250 ( I hope) so storage space shouldn't be a huge issue!

Thanks in advance; and sorry I set up a thread I've been searching for ages and haven't found anything useful,
Peter.

---

### Post by an.echte.trilingue on 2006-12-15
The rule of thumb is that swap is twice your amount of RAM.

Assuming that Ubuntu is your only OS, the easiest way is to make two partitions, one for swap and one for "/".

However, that will leave you with some sticky situations with your data if you need to re-install.

So, you can go with hda1 at 7 or 8 gig and mount "/" there, hda2 one gig and make it swap, and hda3 the rest and mount it at "/home".

At least, that is what I do with my 80 gig hd.

Take care
-mat

---

### Post by glotz on 2006-12-15
See [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I've myself only got / (root) and swap partitions on my physical disk 1. I've got 368 RAM and the swap is same size. The rest of the little 6.5 gig disk are allocated to the root partition.

---

### Post by rich.bradshaw on 2006-12-15
I have 512 ram, 512 swap, 6GB / and that's it. Works fine. I hardly ever even get into using the swap, so 512 should be plenty.

---

### Post by peterj on 2006-12-15
> **an.echte.trilingue said:**
> The rule of thumb is that swap is twice your amount of RAM.

Assuming that Ubuntu is your only OS, the easiest way is to make two partitions, one for swap and one for "/".

However, that will leave you with some sticky situations with your data if you need to re-install.

So, you can go with hda1 at 7 or 8 gig and mount "/" there, hda2 one gig and make it swap, and hda3 the rest and mount it at "/home".

At least, that is what I do with my 80 gig hd.

Take care
-mat


Sorry I recently put wind*ws on for one particular thing, it get 2gb's and struggles just the way it deserves..

---

### Post by drito on 2006-12-15
Another excellent [link]("http://www.psychocats.net/ubuntu/separatehome")!

---

### Post by peterj on 2006-12-15
So having read those links I am thinking:

/windows     3gb hda1     (NTFS)
/                 10gb hda2    (ext 3)
/shared       60gb hda3   (fat32)
/home         5gb hda4     (ext 3)
/swap          2gb  hda5    (swap)

But I'm very sceptical! any opinions greatly appreciated!

Edit: I'm sure people will say if I'm that much a noob just have / and /swop but I want to learn so have no interest in taking the easy option!

---

### Post by an.echte.trilingue on 2006-12-15
> **peterj said:**
> Sorry I recently put wind*ws on for one particular thing, it get 2gb's and struggles just the way it deserves..

Personally I hate dual booting with a passion.  I will usually go one way or the other on a box.  However, in this case I would recommend this partition scheme (please bear in mind that this is just my opinion):

hda1:   6gig (at least)   :windows                                 ntfs
hda2:   6gig                 :mounted at "/"                        ext3
hda3:   1gig                 :swap                                      swap
hda4:   the rest            :mounted at "/media/storage"    ext2

Keep all of your files on /media/storage.  Then install the ext2 driver for windows from fs-driver.org and you will be able to share files between the two OSs just fine (but don't mess with your root partition at all under windows with this driver: you can seriously bugger it up).  Also, bear in mind that if you want to do things like install mad amounts of software or compile your own software, your root partition needs to grow accordingly.

Take care,

---

### Post by drito on 2006-12-15
It will do the job. Although you can erase windows partition :)

---

### Post by peterj on 2006-12-15
I hate dual booting too, I loved just having Ubuntu but I literally have no choice for the next couple of months.

Sounds great thank you. Last time I gave root 2gb's and ran out of space. Wan't able to log in, tried editing partition with partition magic, crashed...!
when I download or save to desktop or my home directory that will be in /media storage? I'm sorry again, learning is a slow process!

---

### Post by glotz on 2006-12-15
It saves wherever you choose. Usually you'd probably download to home partition. E.g. /home/<username>/Desktop
I used to dual boot 2 months before getting rid of the windows partition.
If memory serves, the absolute minimum for fully functional Ubuntu root partition is some 3 gigs.

---

### Post by Sef on 2006-12-15
> Sounds great thank you. Last time I gave root 2gb's and ran out of space. 

Ubuntu should be allocated about 8 gb of space.  Swap should be a gb.  

> tried editing partition with partition magic

PM and Linux tend not to get along.  I prefer to download and burn [GParted]("http://gparted.sourceforge.net/livecd.php").  It is on the Live CD too.

---

### Post by bodhi.zazen on 2006-12-15
Partitioning is an art and the is no single right way.

The only potential problems are running out of room on / and /swap.

/swap is not as much an issue these days and 512 Kb - 1 Gb is typically more then enough.

I have used / partitions for Ubuntu as small as 2.5 Gb, but this is not practical.

I typically use 10-15 Gb for / although you can go as small as 5 Gb.

I like a data partition over a /home partition.

You can mount /tmp /var or what have you in their own partitions, but this is not as helpful for desktop installs. If you do not know what these directories are, then you do not need to use a more complex partitioning scheme.

At at end of the analysis I advise:

/ = 10-15 Gb

/swap =  521 Kb or 1 Gb

Rest a ext3 datea partition

HTH

---

### Post by glotz on 2006-12-15
How come ppl always mix up kilos and megas? I guess zeros don't matter...

---

### Post by peterj on 2006-12-15
thanks for some great advice guys.
I finished with:

10 for / (ext 3)
1 for swap (swap)
rest in an ext2.

Thanks again!

---

### Post by igknighted on 2006-12-15
Just a note, this doesn't apply to you now, but perhaps when you get your new disk...  Swap works best when it is the first partition because it's quickest to read/write there.  In this case, windows needs to be on the first partition, but when you get you new disk you could perhaps leave both in and have windows on one (with the ext2 transfer partition) then swap, /, and /home on the other disk (in that order).

---

