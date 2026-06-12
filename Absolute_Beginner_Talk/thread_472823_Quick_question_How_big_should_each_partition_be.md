---
title: "Quick question: How big should each partition be?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-13
Update: Thanks for the advice, everyone! I think I've got it.
_________

Hey, everyone. I'm about to install a dual boot with XP and Fiesty on a brand new hard drive. My question: How big should the four partitions be? I read some good info here and at the following site: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) However, I need a bit of clarification.

I know that I'll need about 20 gigs for the NTFS XP partition with all the old programs and documents that are sitting there on my old hard drive. Those will eventually be converted to my Ubuntu /user folder, but there are also a few neat programs that I'm not willing to delete. Yet.

Now, here's where I'm confused. How much space do the other three need? Here are my partitions:

Partition #1: XP

Partition #2: Ubuntu and all the programs, of which there will be many. I plan on using Ubuntustudio and a lot of other audio editing stuff. By the way, is my understanding of the location of the programs correct? I am going by this explanation of the Linux directory structure: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)  

An additional question: Is this where the ext3 driver is installed, so I can read my Windows files on partition #1?
  

Partition #3: The /user directory, which may hold some pretty huge music files  

Partition #4: The swap file

So, how big should #'s 2, 3, and 4 be, according to what I want to do? Thanks!

---

### Post by phr0ze on 2007-06-13
Swap is generally = Ram size. However the installer gave me 3GB on my system with 1GB of ram.
Root - I'd go with 15GB, but if you have a very large disk, you can give more
Home - The rest of the drive.

---

### Post by shearn89 on 2007-06-13
Depends how big your HD is, but try this:

Partition 1: 20GB (as you said)
Partition 2: 20GB
Partition 3: 30GB
Partition 4: 2x your RAM (~2GB?)

Thats just a rough estimate... I have ubuntu installed on an old laptop with a 10GB HD, and mines set up:

/     (ubuntu system stuff): ~5GB
/home     (user stuff): 3.5GB
swap: 0.5GB (maybe 1, not sure)


Ubuntu really doesn't take up that much space, and it sounds like the music your putting on there will be the biggest thing.

---

### Post by samuraiCat on 2007-06-13
> **phr0ze said:**
> Swap is generally = Ram size. However the installer gave me 3GB on my system with 1GB of ram.
Root - I'd go with 15GB, but if you have a very large disk, you can give more
Home - The rest of the drive.

Okay, I'll go with the 3G for the swap since my RAM is 1G. I have a 250G hard drive, so I'll bump the root up to 20G. Great! 

By the way, do you know where is that ext3 driver is installed?

---

### Post by Happy_Man on 2007-06-13
Aaaaand the jury says........ you need to decide this for yourself, based on how much stuff goes where, the size of the HDD, etc. The swap file though, should be no bigger than 1 GB. Preferably less. Root directory for you should be about 15-20 GB. /user is what you need to decide.

---

### Post by samuraiCat on 2007-06-13
> **shearn89 said:**
> Depends how big your HD is, but try this:

Partition 1: 20GB (as you said)
Partition 2: 20GB
Partition 3: 30GB
Partition 4: 2x your RAM (~2GB?)

Thats just a rough estimate... I have ubuntu installed on an old laptop with a 10GB HD, and mines set up:

/     (ubuntu system stuff): ~5GB
/home     (user stuff): 3.5GB
swap: 0.5GB (maybe 1, not sure)


Ubuntu really doesn't take up that much space, and it sounds like the music your putting on there will be the biggest thing.

Okay, great. I'm putting in 1G of RAM, so I'll keep the swap at 3G. Thanks!

---

### Post by samuraiCat on 2007-06-13
> **Happy_Man said:**
> Aaaaand the jury says........ you need to decide this for yourself, based on how much stuff goes where, the size of the HDD, etc. The swap file though, should be no bigger than 1 GB. Preferably less. Root directory for you should be about 15-20 GB. /user is what you need to decide.

I think I've gotten some pretty consistent advice from everyone, so, thanks!

---

