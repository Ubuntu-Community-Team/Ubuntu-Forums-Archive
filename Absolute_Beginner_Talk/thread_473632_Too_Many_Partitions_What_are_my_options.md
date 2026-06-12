---
title: "Too Many Partitions? What are my options?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-14
Ok- 

I have 3 partitions currently. Two are Dell Backup Partitions (in case something happens to my xp partition) and 1 is an XP partition. 

I also have 1, empty, 30 some gigabyte blank NTFS partition. 

I want to dual boot, which I know how, but I don't know what to do about the partitions. 

Is there a way to make more, and do I really need a linux swap partition? 


-TS51

---

### Post by LaRoza on 2007-06-14
>I have 3 partitions currently. Two are Dell Backup Partitions (in case something happens to my xp partition) and 1 is an XP partition. 

Do you need two? Could you make backup disks instead?

>I also have 1, empty, 30 some gigabyte blank NTFS partition. 

If you do not need this, this will be good for the second OS

>I want to dual boot, which I know how, but I don't know what to do about the partitions. 

Use the empty NTFS partition, it is big enough

>Is there a way to make more, and do I really need a linux swap partition? 

You can make more, but you can only have 4 primary partitions on a single drive, the rest must be extended.

Swap is not strictly necessary, but you should have one.

---

### Post by domat00 on 2007-06-14
If you've got the space, then you needn't worry about how many partitions - it's space that's the concern.  And a swap works like virtual memory (as in space on your hard disc that can be allocated for use as RAM if your physical memory is overloaded), so it would be a good idea to at least have *some*.

But, I ask, why have 2 XP backup partitions?  I understand 1, but why waste twice as much space on Windows?  Escapes me...  Anyways, just go through the install, and when you get to the partitioning section, click Manual, hit Forward, and create a new partition in the free space, click the drop down menu labeled File System and choose swap.  Enter the size of the swap partition in MB's, then click OK or Forward or whatever the continue button is.  Then, create yet another partition in your free space, allocate all or part or whatever size you need to it in MB's, choose ext3 from the drop down menu, type a / in the Mount To box or similar, and you're home free.

---

### Post by ts51 on 2007-06-14
Ok, because as you can see above, I have 3 partitions on one drive (they all belong to xp) and 1 empty partition that I plan on using for ubuntu. I don't have any other drives, so I guess I'll install it without a swap. Also, it tells me that 36 gig is too big for xp to like it.... Does this mean xp is restricting the size of my partitions?

---

### Post by ts51 on 2007-06-14
> **domat00 said:**
> If you've got the space, then you needn't worry about how many partitions - it's space that's the concern.  And a swap works like virtual memory (as in space on your hard disc that can be allocated for use as RAM if your physical memory is overloaded), so it would be a good idea to at least have *some*.

But, I ask, why have 2 XP backup partitions?  I understand 1, but why waste twice as much space on Windows?  Escapes me...  Anyways, just go through the install, and when you get to the partitioning section, click Manual, hit Forward, and create a new partition in the free space, click the drop down menu labeled File System and choose swap.  Enter the size of the swap partition in MB's, then click OK or Forward or whatever the continue button is.  Then, create yet another partition in your free space, allocate all or part or whatever size you need to it in MB's, choose ext3 from the drop down menu, type a / in the Mount To box or similar, and you're home free.

OK-- the two backups are a result of Dell. The put them on, and they are important, because I've already used them, once or twice probably. And, I'll probably have to use them again. 

I have 512 MB of RAM... so i don't think it will get too overloaded.

---

### Post by domat00 on 2007-06-14
2 back-up partitions?  On a Dell?  No wonder.  Dell always up to funky stuff.

How big is your disc?  XP should have no bearing on partition size, especially if it's only 36 gigs.

And, like is recommended, put at least 256MB for swap.  Assign swap as Logical instead of Primary and see if that works.

---

### Post by ts51 on 2007-06-14
> **domat00 said:**
> How big is your disc?  XP should have no bearing on partition size, especially if it's only 36 gigs.

Somewhere around 160 gigs....

---

### Post by domat00 on 2007-06-14
There should be no problem, but with XP + Dell you never know...  (never had to worry about using Windows plus an OEM, so I wouldn't know about those problems...)

---

### Post by ts51 on 2007-06-14
I'll try it, and if it doesn't work, I guess I'll just ditch the swap.

---

### Post by domat00 on 2007-06-14
Try is all you can do.  Like you said, if it doesn't work, try it without the swap.  And if that doesn't work, someone else here will surely be able to help.  :)

---

### Post by buuntuu! on 2007-06-14
a quick reminder:
you can have 4 primary partitions on each hard disc, no more!
you can bypass this by creating 3 primary and 1 extended partitions
the extended partition can then be split up into multiple logical partitions (@ ts51:you will NOT have to do without swap)
windows wants to live on a primary partition, but ubuntu is happy with a logical partition too.
partitioning with gparted (the partition tool on your live/alternate-cd) is intuitive, you will know what to dpo.
for further reading follow [this]("http://www.psychocats.net/ubuntu/index.php") 
have fun

---

### Post by mrpeenut24 on 2007-06-14
So as I understand this you have [XP - Backup1 - Backup2 - extra partition for Ubuntu?]  What you can do is delete the last partition.  And create an extended partition.  Inside that extended partition create two logical paritions.  One for Ubuntu and one for swap.  I would make it at least as large as your memory.  That way if you hibernate, you will definitely have enough space.

---

### Post by bigken on 2007-06-14
like buuntuu! says create an extended partition with the 30gig and away you go ;)

the way I would partition the extended partition 

10 gig / system
swap twice your ram ie 512mb = 1 gig
the rest /home

---

### Post by bigken on 2007-06-14
by the way the 2 dell partitions one is a restore the other the dell diagnostic tools

---

### Post by antoz on 2007-06-14
If you have run out of primary partitions you need to create an extented partition first and then you can put as many logical partitions inside it as neded. I would still have a swap partition though usually it is recommended to be about 1.5 times your RAM.

---

### Post by ts51 on 2007-06-14
I made an extended drive and then put 2 logical drives in there... I'll use those for Ubuntu.


...Should work

---

### Post by ts51 on 2007-06-14
> **mrpeenut24 said:**
> So as I understand this you have [XP - Backup1 - Backup2 - extra partition for Ubuntu?]  What you can do is delete the last partition.  And create an extended partition.  Inside that extended partition create two logical paritions.  One for Ubuntu and one for swap.  I would make it at least as large as your memory.  That way if you hibernate, you will definitely have enough space.

That's what I'm doing.... 


               Thanks for the help!

---

### Post by ts51 on 2007-06-14
> **bigken said:**
> by the way the 2 dell partitions one is a restore the other the dell diagnostic tools


Oh! I see...

---

### Post by bigken on 2007-06-14
> **ts51 said:**
> I made an extended drive and then put 2 logical drives in there... I'll use those for Ubuntu.


...Should work

it will welcome to ubuntu ;)

I would personally recomend a separate partition for your /home also doing it this way if you need to reinstall the os (ubuntu) no need to backup your personal data :D

---

